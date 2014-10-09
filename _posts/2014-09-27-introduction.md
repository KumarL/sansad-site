---
layout: post
title:  Introduction
date:   2014-09-27 22:47:50
categories: jekyll update
---
A live JSON API for the people and the work of the [Parliament of India](http://parliamentofindia.nic.in/).

We gather the latest data from the Parliament, and make it available to you through an `HTTP GET` call.

* Look up a legislator by their constituency, and check their attendance record in the Parliament
* Find out the number of questions a legislator has asked in the Parliament
* Look up the latest status of a bill and its summary
* Search for the bills based on the topic of your interest, like education

Using the API
-------------

All calls are made with the format below.

{% highlight text %}
http://sansad.co/api/[method]
{% endhighlight %}

We provide two methods, `Legislators`, and `Bills`, that are described in detail in the following sections.

Legislators
-----------

This method provides information and activity stats on the current members of the Parliament, belonging to both the houses, Lok Sabha, and Rajya Sabha. This method lives at the below root domain.

{% highlight text %}
http://sansad.co/api/legislators
{% endhighlight %}

The result is an array of JSON records

### /legislators

An example JSON record for a legislator looks like this:

{% highlight JSON %}
{
  "mp_id": "4764",
  "first_name": "Udit",
  "last_name": "Raj",
  "gender": "Male",
  "age": "56",
  "state": "Delhi",
  "constituency": "North West Delhi",
  "party": "Bhartiya Janata Party",
  "elected": true,
  "in office": true,
  "educational_qualification": "Doctorate",
  "educational_details": "M.A., L.L.B., Hon. Doctorate",
  "debates":"3",
  "private_bills":"0",
  "questions":"9",
  "attendance_percentage":"100",
  "notes":"(Data corresponds to the period 4 June 2014 to 14 Aug 2014.)",
  "house":"Lok Sabha",
  "term_start":"2014-05-18",
  "term_end":"In office"
}
{% endhighlight %}

###Fields

***mp_id**:  
This is an official, and unique id assigned by the parliament to each of their member, and lasts the entire life time of the member. It's the most suitable for use as the id for a legislator.

***first_name**:  
The first name of the legislator

***last_name**:  
The last name of the legislator

***gender**:  
The gender of the legislator

***age**:  
The age, as reported in the offical documents, of the parliamentarian

***state**:  
The state, to which the legislator represents in the Parliament.

***constituency**:  
The constituency of the legislator that they represent in the Parliament. In the case of Rajya Sabha members, this field is left blank as they are elected by the state and do not represent any constituency.

***party**:  
The political party to which the legislator belongs

***elected**:
A boolean value that is set to true for the members that gained membership to the Parliament by contesting and winning an election. If a legislator was made a member through nomination by the speaker of the parliament, this value is set to false.

***in_office**:  
A boolean value that is set to true if the legislator is currently a member of the parliament.

***educational_qualification**:  
This field shows the level of education of a legislator. It can have a value of Graduate, professional graduate, doctorate, etc.

***educational_details**:  
This field has the education degrees, and the name of the educational institutes if provided by the legislator.

***debates**:  
The number of times the legislator has taken part during the debate session in Parliament

***private_bills**:  
The number of private bills that the legislator has introduced in the parliament

***questions**:  
The number of questions that the legislator has asked in the parliament

***attendance_percentage**:  
The attendance percentage of the legislator in the parliament.

***house**:  
The house to which the legislator is a member of - Lok Sabha, or Rajya Sabhya.

***term_start**:  
The date as which the legislator's membership started.

***term_end**:
If the legislator is a not a current member, this field would have the date when the term ended for the legislator. If not, this field would be `In Office`.

Bills
-----------

The Bills method provide information on the current status of a bill introduced in the Parliament, either Lok Sabha, or Rajya Sabha. The method lives at the below root domain.

{% highlight text %}
http://sansad.co/api/bills
{% endhighlight %}

The method returns an array of JSON records of bills. An example JSON record of a bill looks like:

{% highlight JSON %}
{
  "bill_id": "Bill 98, 2014",
  "com_ref": "",
  "com_rep": "",
  "introduced_by": "Smriti Zubin Irani",
  "introduced_on": "2014-08-12",
  "last_action": "Introduction",
  "last_action_at": "2014-08-12",
  "ls_status": "",
  "ministry": "Human Resource Development",
  "rs_status": "",
  "status": "Pending",
  "summary": "The Indian Institutes of Information Technology (IIIT) Bill, 2014 was introduced by the Minister of Human Resource Development, Ms. Smriti Zubin Irani, in the Lok Sabha on August 12, 2014.  The Bill aims to set up IIITs to improve quality of human resources, at par with global standards, within the information technology sector.  \r\nObjectives:  According to the Statement of Objects and Reasons, the Bill seeks to provide four existing IIITs, independent statutory status.  It proposes to declare them as institutes of national importance, to enable them to grant degrees to their students.      \r\nPowers of the institutes:  The four IIITs are situated in, Uttar Pradesh, Tamil Nadu and two in Madhya Pradesh.  They will aim to: (i) provide instruction in areas concerning information technology and allied fields of knowledge, (ii) conduct research and innovation in information technology, (iii) hold examinations and grant degrees, diplomas and other titles, (iv) create and make appointments to various posts, (v) establish and maintain such infrastructure as may be necessary, etc.   \r\nBoard of Governors:  The Board shall be the principal executive body of each institute.  It will be headed by a Chairperson, and consist of faculty members and persons from the fields of information technology.   The Board will be responsible for the general superintendence, direction and control of the affairs of the institute.  It shall have the power to frame, amend, modify and rescind the Statutes and Ordinances governing the institutes. Statues provide for matters such as the constitution, powers and duties of the authorities of the institute, conferment of honorary degrees, and fees to be charged for courses.\r\nSenate:  The Senate will be the principle academic body of each institute.  It will be chaired by the Director of the institute and consist of senior faculty members and persons of eminence from the field of information technology.  It shall have the power to enact, amend or modify Ordinances governing academic matters such as process of admission, courses of study and conduct of examinations.\r\nCouncil:  A Council shall be established to coordinate the activity of all the institutes.  It will consist of Ministers having administrative control over technical education, industry partners, Chairpersons and Directors of all institutes and persons of eminence in the field of information technology.  Key functions include: (i) advising on matters related to the duration of the courses and degrees; (ii) laying down policies regarding recruitment, levying of fees, etc; (iii) examining the development plans and annual budget estimates of each institute.      \r\nResearch Council:  Research Councils shall be instituted to organise and promote research in the institutes.  They will provide an interface with research funding organisations and industry, and provide for the incubation of technology applications emerging from research.  \r\nDirector:  The Director will be the principle executive officer of every institute and exercise powers and discharge duties as assigned by the Act, or Statutes or Ordinances or by the Board or Senate.\r\nPerformance Review:  All institutes shall establish a Committee to review the performance of the institute within the first seven years of establishment and every fifth year thereafter.\r\nFinancing of the institutes:  The institutes shall receive grants every financial year, from the central government, for meeting their expenditure.  Every institute shall maintain proper accounts and records which are to be audited by the Comptroller and Auditor-General of India.",
  "title": "The Indian Institutes of Information Technology Bill, 2014",
  "url": "http://www.prsindia.org/billtrack/the-indian-institutes-of-information-technology-bill-2014-3363/"
}
{% endhighlight %}

###Fields

***bill_id**:  
The bills number, as indicated in the official text of the bill. The Parliament accords this unique id to each bill, and is most suitable for use as an Id.

***com_ref**:  
The date on which this bill was referred to a committee for further discussion.

***com_rep**:
The date on which a report was presented by the committee to which this bill was earlier referred to.

***introduced_by**:  
The member of the Parliament that introduced this bill.

***introduced_on**:  
The date on which this bill was introduced in the Parliament.

***last_action**:
The last action taken on this bill. It could be `Introduction`, as shown in our example bill, or `Referred to the standing committee`, or `Report presented by the standing committee`, etc.

***last_action_at**:  
The date on which the last action on this bill was taken.

***ls_status**:
The status of the bill in Lok Sabha, if it's different from the current status of the bill. For example, if the bill has passed in the Lok Sabha, but is still pending approval in the Rajya Sabha, the status of the bill in the Parliament is still `Pending`, but this field would be set to `Passed`.

***rs_status**:
The status of the bill in Rajya Sabha, if it's different from the current status of the bill. For example, if the bill has passed in the Rajya Sabha, but is still pending approval in the Lok Sabha, the status of the bill in the Parliament is still `Pending`, but this field would be set to `Passed`.

***status**:  
The status of the bill in the Parliament.

***summary**:  
The official summary of the bill as described in the latest draft of the bill.

***title**:  
The official title of the bill

***url**:  
A very good source of additional details on the bill.

Common Parameters to API
------------------------

###Status endpoint

You can check the status of the API at the root address of the API: `http://sansad.co/api`. If all is good, you'll get a HTTP status of 200, and the following JSON:

{% highlight JSON %}
{
  "status": 200,
  "message": "Namaste!",
  "documentation": "http://sansad.co",
  "code": "https://github.com/kumarl/sansad",
  "report_bugs": "https://github.com/kumarl/sansad/issues",
  "more_apis":"http://sansad.co/api"
}
{% endhighlight %}

### Pagination  

All results in the Sansad API are paginated. You can set `per_page`, and `page` to control the page size and the offset. The maximum `per_page` is 50.

{% highlight text %}
/legislators?fields=party&per_page=30&page=5
{% endhighlight %}

At the top-level of every response are **count** and **page** fields, with pagination information.

{% highlight JSON %}
"count": 781,
"page": {
  "count": 20,
  "per_page": 30,
  "page": 5
}
{% endhighlight %}

### Partial Responses

IF you're interested in a subset of the fields, you can request them by supplying a comma-separated list of files as the `fields` parameter.

**Political parties of the legislators in the state of Delhi**

{% highlight text %}
/legislators?fields=party
{% endhighlight %}

{% highlight text %}
"results":[
    {
      "party": "Bharatiya Janata Party"
    },
    {
      "party": "Bharatiya Janata Party"
    },
    {
      "party": "Indian National Congress"
    }
    ...
]
{% endhighlight %}

### Filtering
You can filter on many fields to get a subset of the results.

{% highlight text %}
/legislators?first_name=Udit&last_name=Raj
{% endhighlight %}

{% highlight text %}
/bills?introduced_by=Smriti Zubin Irani
{% endhighlight %}

{% highlight text %}
/bills?ministry=Law and Justice
{% endhighlight %}

### Basic Search
You can search the data by providing a `query` parameter to return results that the API thinks match your query. Queries are interpreted as *phrases*.

*Bills on topic related to "education"*
{% highlight text %}
/bills?query=education
{% endhighlight %}
