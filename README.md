WebCrawler
==========

Web Crawler to craw test website fakebook.com at http://cs5700.ccs.neu.edu/accounts/login/?next=/fakebook/

I. File list
-------------
Crawler.java         Source code for main program 
HTTPClient.java      Source code for HTTP protocol and handle request & response
HTTPRequest.java     Source code for HTTP request 
HTTPResponse.java    Source code for HTTP response
Makefile		     Makefile to build word-count
README			     This file

Program can be built using default make arguments.


II. Design
-------------
A. Program design

The crawler works in this way :
Parse the root web page("http://cs5700f14.ccs.neu.edu/accounts/login/?next=/fakebook/."), 
and get all links from this page. Using the URLs that retrieved from step 1, and parse those URLs.
When doing the above steps, we need to track which has been processed before, 
so that each web page only get processed once. We store the frontier URLs in Queue. 
We're using the following step:

1. We login to fakebook using HTTP methods. Get the session and csrf token.

2. We get the homepage and begin crawl this website. We maintained two url sets, 
one is the url sets we have visited, the other one is the url sets that we haven't visited.
we are using hashmap to avoid visiting duplicate url and using BFS when crawling.

3. We continue crawl this website until we could't find new unvisited url or we have
collected all the five secret_flags.


B. HTTP protocol 
The Hypertext Transfer Protocol (HTTP) is an application protocol for distributed, 
collaborative, hypermedia information systems.HTTP is the foundation of data communication 
for the World Wide Web.

1. Http Request Methods 
Those methods are commonly used:
GET      Requests a representation of the specified resource
HEAD     Asks for the response identical to the one that would correspond to a GET request, 
         but without the response body. 
POST     Requests that the server accept the entity enclosed in the request 
         as a new subordinate of the web resource identified by the URI. 
DELETE   Deletes the specified resource.

In this crawler program, we mainly use GET and POST method.


2. HTTP header
Request Line   First line of header, and contains basic info on the request. 
               We can get the status code for request line
Header         The rule format we need follow 
 

3. HTTP status codes
200  OK
301  Moved Permanently  
302  Moved Temporarily
400  Bad Request
403  Forbidden
500  Internal Server Error

We will response depending on the given http status code.







