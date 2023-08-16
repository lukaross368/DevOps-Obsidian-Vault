#devops 
#networking 
#networkingProtocols 

Hyper Text Transfer Protocol

Most widely used protocol, used for viewing web pages on the internet.

All Information exchanged with HTTP is sent in clear text (Not very secure, since this is traveling across the public internet). The most popular way of establishing an encrypted HTTP connection is [[HTTPS]].

HTTP is an Application Layer protocol in the [[Internet Protocol Suite]]

The Client submits an HTTP request to the Server. The Server, which provides resources such as HTML files, returns a response message to the client. 

### Request Methods

HTTP defines methods (sometimes called 'verbs') to indicate the desired action to be performed on the identified resource. 

- GET: The GET method requests that the target resource transfer a representation of its state.
- HEAD: The HEAD method requests that the target resource transfer a representation of its state but without the data enclosed in the response body. This is useful for retrieving metadata in the response header.
- POST: The POST method requests that the target resource process the representation enclosed in the request according to the semantics of the target resource.
- PUT: The PUT method requests that the target resource create or update its state with the state defined by the representation enclosed in the request. A distinction from POST is that the client specifies the target location on the server.
- DELETE: The DELETE method requests that the target resource delete its state.
- CONNECT: The CONNECT method requests that the intermediary establish a TCP/IP tunnel to the origin server identified by the request target.
- OPTIONS: The OPTIONS method requests that the target resource transfer the HTTP methods that it supports
- TRACE: The TRACE method requests that the target resource transfer the received request in the response body.
- PATCH: The PATCH method requests that the target resource modify its state according to the partial update defined in the representation enclosed in the request.

A request method is _safe_ if a request with that method has no intended effect on the server. The methods GET, HEAD, OPTIONS, and TRACE are defined as safe. In other word, safe methods are intended to be read-only.

A request method is _idempotent_ if multiple identical requests with that method have the same effect as a single such request.

The methods PUT and DELETE, and safe methods are defined as idempotent.