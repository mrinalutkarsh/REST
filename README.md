REST

URI = "http:" "//" host [ ":" port ] [ abs_path [ "?" query ]]


there are specific URLs for different operations
When you call web services, you need to know what the method does, what the input arguments are and what the return type is. 
Just like web pages, REST APIs have URLs and addresses too.
Since APIs have addresses, an API designer or web service developer needs to decide what the addresses should be.

ACTION BASED/RESOURCE BASED ADDRESSES
-------------------------------------
The address is action based:
/weatherapp.com/weatherLookup.do?zipcode=12345
This tells you that there is something called weatherLookup.do that takes the zip code as parameter.


RESTful APIs have resource based addresses.

/weatherapp/zipcode/12345
/weatherapp/zipcode/56789

It’s almost as if you are not making the server do any action, but rather just look up and get something that already exists.
And weather forecast for a country could be designed to be at a location like 

/weatherapp/countries/countryname

1.we tell the client what the address is
2.what HTTP method to use to call it
3.what is the response that we’ll send back
4.One useful piece of information that every response has is the status code
5. 200 a HTTP response is successful,
   500 If there is an error on the server while processing 
   404 If you are trying to access something that does not exist
6.In the case of RESTful web services, you cannot send readable messages because the client is a piece of code! This is why sending the right status code is very important.
7.All requests and responses need to have the right Content-Type header set so that the format of the messages are well understood by everyone.
8.CONTENT-NEGOTIATION:The same API can send back data in multiple different formats, and the actual format it chooses depends on what the client wants.

collection URIs:- Accessing a directory gives you all the contents in that directory. So, think of /messages as the top level directory for all messages and accessing that URI gives a list of all messages. These URIs pull up a collection of INSTANCE RESOURCES.

/messages?offset=30&limit=10
client who's making the request probably doesn't want all that data. We should design our API to provide a way for the client to paginate or filter the results.
One way to do that is using query params. Standard practice to provide pagination is to have two query params: starting point and page size.
/messages?year=2014
retrieve messages posted in a given year
/messages?year=2014&offset=50&limit=25

C	POST
R	GET
U	PUT
D	DELETE

ERROR CODES
------------
HTTP specification requires the very first line of any response to be a status line.
1XX Codes - Informational
2XX Codes - Success
	200 OK
	201 Created
	204 No Content
3XX Codes - Redirection
	The server sends these codes to ask the client to do further action to complete the request. 
	302 Found and 307 Temporary Redirect
	304 Not Modified
		When a client tries to get a resource that it has already got before, the server can send this status code
4XX Codes - Client error
	400 Bad Request
	401 Unauthorized
	403 Forbidden The client may have authorized, but they are still not allowed to make the request. 



