# HTTP Introduction
- Protocol used to read and write resources (data) in a simple text-based manner.
- Used for `JS` files, `CSS`, `PDFs` and of course `HTML`

## HTTP Flow
- Request-response based protocol
  - A slient makes a request to an HTTP server, immediately also sending a message asking for a specific resource, which the server sends down as a response.
  - A server cannot send a response to a client if the client has not first sent a request.

### HTTP flow Reading [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#http_flow)
When a client wants to communicate with a server, either the final server or an intermediate proxy, it performs the following steps:
  1. Open a `TCP` connection: The TCP connection is uses to send a request, or several, and receive an answer. The client may open a new connection, or open several TCP connections to the servers
  2. Send an `HTTP` message: HTTP messages (before HTTP/2) are human-readable. With HTTP/2 these simple messages are encapsulated in frames, making them impossible to read directly, but the principle remains the same. For ex:
  ```HTTP
  GET / HTTP/1.1
  Host: developer.mozilla.org
  Accept-Language: fr
  ```
  3. Read the response send by the server, such as:
  ```HTTP
  HTTP/1.1 200 OK
  Date: Sat, 09 Oct 2010 14:28:02 GMT
  Server: Apache
  Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
  ETag: "51142bc1-7449-479b075b2891b"
  Accept-Ranges: bytes
  Content-Length: 29769
  Content-Type: text/html

  <!DOCTYPE html>… (here come the 29769 bytes of the requested web page)
  ```
  4. Close or reuse the connection for further requests.

If HTTP pipelining is activated, several requests can be send without waiting for the first response to be fully received. HTTP pipelining has proven difficult to implement in existing networks, where old pieces of software coexist with modern versions. HTTP pipelining has been superseded in HTTP/2 with more robust multiplexing requests within a frame.

### HTTP Messages Reading [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#http_messages)
HTTP messages, as defined in HTTP/1.1 and earlier, are human-readable. In HTTP/2, these messages are embedded into a binary structure, a frame, allowing optimizations like compression of headers and multiplexing. Even if only part of the original HTTP message is sent in this version of HTTP, the semantics of each message is unchanged and the client reconstitutes (virtually) the original HTTP/1.1 request. It is therefore useful to comprehend HTTP/2 messages in the HTTP/1.1 format.

There are two types of HTTP messages, requests and responses, each with its own format.

### An example HTTP request:
![example http request](./http_request.png)

- Consists of the following elements:
  - An HTTP method, usually a verb like `GET`, `POST`, or a noun like `OPTIONS` or `HEAD` that defines the operation the client wants to perform. Typically, a client wants to fetch a resource (using `GET`) or post the value of an HTML form (using `POST`), though more operations may be needed in other cases.
  - The path of the resource to fetch; the URL of the resource stripped from elements that are obvious from the context, for example without the protocol (http://), the domain (here, developer.mozilla.org), or the TCP port (here, 80).
  - The version of the HTTP protocol.
  - Optional headers that convey additional information for the servers.
  - A body, for some methods like `POST`, similar to those in responses, which contain the resource sent.

### HTTP Responses
![example http response](./http_response.png)
- The version of the HTTP protocol they follow.
- A _status code_, indicating if the request was successful or not, and why.
- A status message, a non-authoritative short description of the status code.
- HTTP headers, like those for the requests
- Optionall, a body containing the fetched resources.

## Compass note on HTTP Requests
- When a client wants to communicate with a server it issues a *request*.
- An HTTP request is made up of many components, but there are only two parts that we need to pay attention to right now:
  - The *`PATH`*, says what the resource the client wants to act on.
  - The *`METHOD`*, says what action it would like to perform.

### HTTP Methods
There are 9 HTTP request methods, but we only need to consider 4 (CRUD)

- `GET`: used to 'get' some data from the server
- `POST`: usually used to create some new data
- `PUT`: generally used for editing existing data on the server
- `DELETE`: used to delete some existing data

### Paths and URL Structures
In order to request a resource (webpage, etc.) from an HTTP server, we need to know its `URL`. The _path_ is part of the URL.

***
### Reading on Understanding URLs and their structure [here](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL)

`Uniform Resource Locators`  
- Mechanism used by browsers to retrieve any published resource on the web.
- An address of a given unique resource on the web.
#### Basics: anatomy of a URL
```
Examples:
https://developer.mozilla.org
https://developer.mozilla.org/en-US/docs/Learn/
https://developer.mozilla.org/en-US/search?q=URL
```
Any of these can be types into your browser to tell it to load the associated page (resource)  
A URL is composed of different parts, some mandatory and others optional.
![url decomposed](./mdn-url-all.png)

#### Scheme
First part of the URL, indicates the protocol that the browser must use to request the resource. Usually for websites the protocol is `HTTPS` or `HTTP` (unsecured version). Addressing web pages requires one of these two, but browsers also know how to handle other schemes such as `mailto:`.

#### Authority
Separated from the scheme by the character pattern `://`. Includes both the *domain* (e.g. `www.example.com`) and the *port* (`80`).
- domain indicates which web server is being requested. Usually a domain name, but an IP address may also be used
- Port indicates the technical 'gate' used to access the resources on the web server. Usually omitted if the web server uses the standard ports of the HTTP protocol (80 for HTTP and 443 for HTTPS) to grant access to its resources.

#### Path to resource
`/path/to/myFile.html` is the path to the resource on the web server. In the early days of the web, a path like this represented a physical file location on the web server. Nowadays, it is mostly an abstraction handled by web servers without physical reality.

#### Parameters
`?key1=value1&key2=value2` are extra parameters provided to the Web server. Those parameters are a list of key/value pairs separated with the `&` symbol. The Web server can use those parameters to do extra stuff before returning the resource. Each Web server has its own rules regarding parameters, and the only reliable way to know if a specific Web server is handling parameters is by asking the Web server owner.

#### Anchor
`#SomewhereInTheDocument` is an anchor to another part of the resource itself. An anchor represents a sort of "bookmark" inside the resource, giving the browser the directions to show the content located at that "bookmarked" spot. On an HTML document, for example, the browser will scroll to the point where the anchor is defined; on a video or audio document, the browser will try to go to the time the anchor represents. It is worth noting that the part after the `#`, also known as the fragment identifier, is never sent to the server with the request.
***

## HTTP Responses
When a server receives a request from a client, it reads the path and method to figure out what it should do. For example, if the request it receives is something like `GET /dogs` the server may try to fetch and return all of the data about dogs it has.  
  
After the server has tried to perform the requested action, it sends a response back to the client. The response contains all kinds of useful information, we'll look at two important bits:
- Status code
- Body

### HTTP Status codes
Three digit number that server puts in the response to let the client know whether or not the operation was successful. [List of status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).  
Main ones are:
- `200`: "Everything went great!"
- `201`: "The request has succeeded and a new resource has been created as a result."
- `404`: "Resource was not found."
- `500`: "The server had an error."