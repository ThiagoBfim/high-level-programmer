# What should I know about REST API?

### What is a REST API?

API (Application Programming interface) is a set of routines, protocols, and tools for building software applications.

REST (Representational state transfer) is an architectural style for distributed hypermedia system. It was introduced in 2000 by [Roy Fielding in his dissertation](https://www.ics.uci.edu/\~fielding/pubs/dissertation/rest\_arch\_style.htm).

So, a REST API or a RESTFul API is an API that implements the REST principles.

### RFC what is it?

RFC is request for comments, is a formal document from Internet engineering Task Force (IETF).

RFC documents contain technical specifications and organizational notes for the Internet.

To know more about RFC access: https://www.ietf.org/standards/rfcs/

There are some RFCs that were created to deal with REST, the first one was RFC 2616 created in June 1999 and became obsolete by RFC7230 - RFC7235 created in June 2014, and now these RFCs are also obsolete because of the new RFC9110, RFC9111 and RFC9112 that were created in June 2022.

### What is the most common HTTP Methods?

| Method  | Description                                                                                                                | Is Idempotent |
| ------- | -------------------------------------------------------------------------------------------------------------------------- | ------------- |
| GET     | Return the current value of an object                                                                                      | True          |
| PUT     | Replace an object, or create a named object, when applicable                                                               | True          |
| DELETE  | Delete an object                                                                                                           | True          |
| POST    | Create a new object based on the data provided, or submit a command                                                        | False         |
| HEAD    | Return metadata of an object for a GET response. Resources that support the GET method MAY support the HEAD method as well | True          |
| PATCH   | Apply a partial update to an object                                                                                        | False         |
| OPTIONS | Get information about a request; see below for details.                                                                    | True          |

For more information, access [RFC9110 - HTTP Methods](https://datatracker.ietf.org/doc/html/rfc9110#section-9)

### What is the most common HTTP Response?

* 1xx (Informational): The request was received, continuing process
* 2xx (Successful): The request was successfully received, understood, and accepted
* 3xx (Redirection): Further action needs to be taken in order to complete the request
* 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
* 5xx (Server Error): The server failed to fulfill an apparently valid request

These are the most common HTTP Status:

| HTTP Status | Name                  | Description                                                                                                                                   |
| ----------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 200         | OK                    | Indicates that the request has succeeded                                                                                                      |
| 201         | Created               | Indicates that the request has resulted in one or more new resources being created                                                            |
| 202         | Accepted              | Indicates that the request has been accepted for processing, but the processing has not been completed.                                       |
| 204         | No Content            | Indicates that the server has successfully fulfilled the request and there is no content to send in the response payload body                 |
| 301         | Moved Permanently     | Indicates that the target resource has been assigned a new permanent URI                                                                      |
| 400         | Bad Request           | Indicates that the server cannot or will not process the request due to something that is perceived to be a client error                      |
| 401         | Unauthorized          | Indicates that the request has not been applied because it lacks valid authentication credentials for the target resource                     |
| 403         | Forbidden             | Indicates that the server understood the request but refuses to authorize it                                                                  |
| 404         | Not Found             | Indicates that the origin server did not find a current representation for the target resource or is not willing to disclose that one exists. |
| 500         | Internal Server Error | Indicates that the server encountered an unexpected condition that prevented it from fulfilling the request.                                  |

As I said, these are the most common, but there are others HTTP status.

To know more about the HTTP status, access the [RFC9110 - Status Codes](https://datatracker.ietf.org/doc/html/rfc9110#section-15)

### What is the Glory of rest?

Leonard Richardson breaks down the principal elements of a REST approach into three steps:

* Level 0 (The Swap of POX): At this level there is only one endpoint, and normally it doesn't use HTTP Status, so the API will return 200 OK on all types of responses and the output will contain the error. At this level there is a single HTTP Method, usually POST.
* Level 1 (Resources): At this level it will be more than one endpoint, actually one endpoint per resource, but still not using the HTTP Verbs or HTTP Status.
* Level 2 (HTTP Verbs): At this level will use the HTTP Verbs and the HTTP Status
* Level 3 (Hypermedia Controls): This is the most mature level of Richardson’s model, in this level the API will use HATEOAS(Hypermedia as the Engine of Application State), which encourages easy discoverability.

If you want to know more about it, read these articles:

[Richardson Maturity Model - Martin Fowler's blog](https://martinfowler.com/articles/richardsonMaturityModel.html)

[What is Richardson Maturity Model](https://restfulapi.net/resource-naming/)

### Conclusion

Now you know what is an API and what is a REST API, but what I showed here is just the basics concepts, so keep studying :)

To write a wonderful API, you must know RFC and best practices. This will help you create an API that follows the common standard, so it's easy to be a customer of your API.

Another important thing is to define a REST API design. It will be easier to use your API if you have some well-known design. Try searching for famous APIs and see how they design to understand how to do this and what are the best practices.

### References:

If you want to create a better API, I recommend these reading:

**REST API - Design Rulebook**\
**-** Mark Masse\
\
[AZURE API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/azure/Guidelines.md)

[Best practices for REST API design - Stackoverflow Blog](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)

[Swagger specification](https://swagger.io/specification/)

[RESTFUL API](https://restfulapi.net/)

[Stripe API Design](https://stripe.com/blog/payment-api-design)

