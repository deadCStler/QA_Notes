Application Programming Interface, it allows applications to access data and interact with external software components.

### Web Services

Web Services are similar to API which is used for communication or exchanging data using XML (Extensible Markup Language) format using web protocols like HTTP or HTTPS.

## HTTP Extended

Hyper Text Transfer Protocol was designed for communication between web browsers and web servers, but it can be also used for other purposes.

Clients and servers communicate by exchanging individual messages. The messages sent by the client, usually a Web browser, are called **requests** and the messages sent by the server as an answer are called **responses**.

### Client: the user-agent

The user-agent is any tool that acts on behalf of the user. This role is primarily performed by the Web browser, but it may also be performed by programs used by engineers and Web developers to debug their applications.

### The Web server

On the opposite side of the communication channel is the server, which serves the document as requested by the client. A server appears as only a single machine virtually; but it may actually be a collection of servers sharing the load (load balancing), or other software (such as caches, a database server, or e-commerce servers), totally or partially generating the document on demand.

Between the Web browser and the server, numerous computers and machines relay the HTTP messages knows as **************proxies**************.

Request URL: URL of the resource fetched

Request Method: It contains the request method, the action to be performed, such as GET

Status Code: It represents whether a specific request has been completed or not

### HTTP Request Methods:

- GET: These requests are used to *get* resources from a server. By definition, they only fetch data from server.
    - We can only specify a single resource in the HTTP request-line at a time meaning that we need a separate request for fetching other files.
- POST: These requests are used to send some data to the server such as submitting data or uploading file.
- PUT: These requests are used to update data on the server side, can be used for situations like changing activity, updating marks on a server.

### HTTP Status Code

They are the part of the response they help to understand what happened to the request. They are 3 digit numbers and are divided into five categories:

- 1xx: Informational
- 2xx: Success
- 3xx: Redirection
- 4xx: Client Error
- 5xx: Server Error

In detail:
[HTTP Status Codes](https://www.restapitutorial.com/httpstatuscodes.html)

