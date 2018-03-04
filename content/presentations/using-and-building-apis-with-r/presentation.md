Using and Building APIs in R
========================================
author: Steven Mortimer
date: March 15, 2016
css: css-presentations.css
width: 960
height: 700



What is an API?
====================================================
type: subsection

<b><u>A</u></b>pplication <b><u>P</u></b>rogramming <b><u>I</u></b>nterface: 
<blockquote cite="https://en.wikipedia.org/wiki/Application_programming_interface">
expresses a software component in terms of its operations, inputs, outputs, and 
underlying types, defining functionalities that are independent of their 
respective implementations<sup>1</sup></blockquote>
* It's a contract between systems to facilitate a task 
<br><span style="font-size:65%;">(could be software, hardware, databases, web applications)</span>
* As Data Consumers we will focus on the specifications of webservice data API calls
<br>
<div class="footer">
<sup>1</sup>&nbsp;&nbsp;Wikipedia: <a href="https://en.wikipedia.org/wiki/Application_programming_interface">https://en.wikipedia.org/wiki/Application_programming_interface</a>
</div>

2 Common Webservice API Types
====================================

<div class="footer2">
<blockquote cite="">
<b>Resources:</b><br>
<a href="http://spf13.com/post/soap-vs-rest">The Difference Between SOAP and REST</a><br>
<a href="http://www.soapui.org/testing-dojo/world-of-api-testing/soap-vs--rest-challenges.html">SOAP vs REST Challenges</a>
</blockquote>
</div>

<div class="column column1 slideContent">
<span style="color:red">SOAP</span><br>
<span style="font-size:65%;"><b><u>S</u></b>imple <b><u>O</u></b>bject <b><u>A</u></b>ccess <b><u>P</u></b>rotocol</span> 
<ul>
<li>Protocol agnostic <br><span style="font-size:60%;">(HTTP, SMTP, TCP, or JMS)</span></li>
<li>Typically XML</li>
<li>Strongly Typed</li>
<li>Definitions provided by WSDL <span style="font-size:55%;">(<b><u>W</u></b>eb <b><u>S</u></b>ervice <b><u>D</u></b>escription <b><u>L</u></b>anguage)</span></li>
</ul>
</div><br>

<div class="column column2 slideContent">
<span style="color:red">REST</span><br>
<span style="font-size:65%;"><b><u>Re</u></b>presentational <b><u>S</u></b>tate <b><u>T</u></b>ransfer</span>
<ul>
<li>Noun-Verb Paradigm <br><span style="font-size:60%;">(HTTP GET/POST/PUT/DELETE)</span></li>
<li>Typically formatted as JSON <span style="font-size:55%;">(<b><u>J</u></b>ava<b><u>s</u></b>cript <b><u>O</u></b>bject <b><u>N</u></b>otation)</span></li>
</ul>
</div><br>


Diagramming SOAP vs. REST Services
====================================================
<div class="midcenter" style="margin-left:-410px; margin-top:-255px; width:103%;">
  <img style="width:100%;" src="http://downloads.eviware.s3.amazonaws.com/web_site_images/soapui/web_images/Dojo/REST_vs_Soap.png" alt="soap-v-rest-diagram">
</div><br>
<div class="footer">
&nbsp;&nbsp;Image from: <a href="http://spf13.com/post/soap-vs-rest">http://spf13.com/post/soap-vs-rest</a>
</div>


2 Common API Data Formats
====================================
<span style="color:red">XML</span>

```
<person>
  <firstname>Rick</firstname>
  <lastname>James</lastname>
  <occupation>legend</occupation>
</person> 
```
<ul>
<li>Favored by SOAP APIs</li>
<li>Traditional format</li>
</ul>
***
<span style="color:red">JSON</span>

```
{
	"person" : {
		"firstname" : "Rick",
		"lastname" : "James",
		"occupation" : "legend"
	}
}
```
<ul>
<li>Favored by REST APIs</li>
<li>A more modern, flexible approach</li>
</ul>


transition-to-using-api
====================================================
title: false
<h3>
  <div class="midcenter" style="margin-left:-400px; margin-top:-300px;">
  </br></br></br><span style="font-weight: 700; color:#25679E;">Next: </span><br>Using APIs from R
  </div>
</h3>

Using an XML API
====================================
<div class="footer">
&nbsp;&nbsp;The Open Movie Database API at: <a href="http://www.omdbapi.com/">http://www.omdbapi.com/</a>
</div> 


```r
# Find a movie by title ("The Godfather")
library(XML);library(RCurl)
data <- RCurl::getURL(paste0('http://www.omdbapi.com/', 
                             '?t=The+Godfather&plot=short&r=xml'))
substring(data,1,250)
```

```
[1] "<root response=\"False\"><error>No API key provided.</error></root>"
```

```r
formatted_xml <- xmlParse(data)
xml_to_list <- xmlToList(formatted_xml)
head(xml_to_list$movie)
```

```
NULL
```

Using an XML API with httr and xml2
====================================

```r
library(xml2);library(httr) # you could also use Hadley's packages
resp <- httr::GET(paste0('http://www.omdbapi.com/', 
                             '?t=The+Godfather&plot=short&r=xml'))
resp
```

```
Response [http://www.omdbapi.com/?t=The+Godfather&plot=short&r=xml]
  Date: 2018-03-04 15:14
  Status: 401
  Content-Type: text/xml; charset=utf-8
  Size: 65 B
```

```r
parsed_xml <- read_xml(content(resp, as="raw"))
parsed_xml
```

```
{xml_document}
<root response="False">
[1] <error>No API key provided.</error>
```

Using an XML API
====================================

```r
# Search all movies by a title ("The Godfather")
data <- getURL('http://www.omdbapi.com/?s=The+Godfather&r=xml')
formatted_xml <- xmlParse(data)
xmlAttrs(xmlChildren(formatted_xml)$root)
```

```
response 
 "False" 
```

```r
# find all "result" elements
parsed_movie_elements <- xpathSApply(formatted_xml, "//result")
head(parsed_movie_elements, 2)
```

```
list()
```

Parsing XML to data.frame
====================================











```
Error in `[.data.frame`(xml_to_df, c("title", "year", "imdbID", "type")) : 
  undefined columns selected
```
