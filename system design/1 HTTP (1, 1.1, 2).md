
hyper transfer protocol

versions of http

### HTTP/1.x
If we have a html, css, js files, the html get render first using a rest api request like get/post/put/delete. and the browser read the images, css and js assets in a queue

few problems:
a. head-of-line blocking: each connection could handle only one request at a time. this limitation often led to inefficient use of network resources, as subsequent requests had to wait for the previous request to complete. 

b. lack of priortization: http/1.x did not offer a way to priortize requests, which could lead to less crticial resources blocking more important ones.

c. other problems, such as plain text headers being sent that are large, especially when cookies in use.

### HTTP/2
- released in 2015
- The issue raised by HTTP/1.1 is resolved by this. 
- In HTTP/1.1 we had less than 4g network so, it was suitable. As in 2015, things changed, according to Web Archive, the avg. size of an image on a web page grew over 8000%  and, so, did the number of images, and that's before other assets like JS. 
- For this, HTTP/2 multiplexing feature was introduced. 

![[http-image.png]]

In HTTP/1.x, the asset requests are queued and requested one at a time.

Using multiplexing, the browser effectively requests the assets together, and then receives them in the same way, all on the same connection. 

##### other benefits
1. header compression: uses HPACK algorith to compress request and response headers
2. server push: server proactively push resources to the client's cache before they are requested, reducing latency and improving overall user experience.
3. stream prioritization: enables client to prioritize requests, allowing more critical requests to be fetched and rendered first
4. binary farming: uses a binary farming layer to encapsulates messages, which makes the protocol more efficient and less error-prone compared to plain-text approach of HTTP/1.xThe downside is that there are issues with TCP, especially in high-latency and lossy networks.

The base layer protocol is TCP. 

### HTTP/3
The base layer protocol utilizes a flavour of UDP called Quick UDP Internet Connection. 

QUIC has a few benefits:
 1. built-in encryption
 2. reduced head-of-line blocking
 3. connection migration
 4. 0-RTT connection establishment
 5. improved congestion control

HTTP/3 and QUIC is good. 

Ref:
https://dev.to/accreditly/http1-vs-http2-vs-http3-2k1c

