# Homework of Computer Networking

### Problem6

##### Question: 

Obtain the HTTP/1.1 specification (RFC 2616). Answer the following questions:

​	a. Explain the mechanism used for signaling between the client and server to indicate that a persistent connection is being closed. Can the client, the server, or both signal the close of a connection?

​	b. What encryption services are provided by HTTP?

​	c. Can a client open three or more simultaneous connections with a given server?

​	d. Either a server or a client may close a transport connection between them if either one detects the connection has been idle for some time. Is it possible that one side starts closing a connection while the other side is transmitting data via this connection? Explain.

##### Answer:

a. The mechanism used for signaling between the client and server to indicate that a persistent connection is being closed is as follows:

1. Unless the "close" tag is included in the request's Connect header, HTTP/1.1 servers can always assume that the HTTP/1.1 client wants to maintain a persistent connection. If the server wants to close the connection immediately after sending the response, it SHOULD send a Connect header field containing "close".

2. An HTTP/1.1 client may expect to keep the connection open, but this must be based on whether the server response contains a Connect header field and whether the header field contains "close". If the client does not want to maintain the connection for more requests, it SHOULD send

   ```

   ```

    a Connect header field with a value of "close".

3. If either the client or the server sends a Connect header with "close" in it, then the client's request will become the last request for this connection.

4. Therefore, either the client or the server can signal that the connection is closed.

b. Actually, the HTTP protocol itself has no encryption service.

c. No, there is a maximum of two simultaneous connections.

d. If One side has been closed, then it is impossible for the other side to transmit data via the connection. Because it required that client software should be able to reopen transport layer connections and retransmit abandoned request sequences without user interaction.



### Problem12

##### Question: 

Write a simple TCP program for a server that accepts lines of input from a client and prints the lines onto the server’s standard output. (You can do this by modifying the TCPServer.py program in the text.) Compile and execute your program. On any other machine that contains a Web browser, set the proxy server in the browser to the host that is running your server program; also configure the port number appropriately. Your browser should now send its GET request messages to your server, and your server should display the messages on its standard output. Use this platform to determine whether your browser generates conditional GET messages for objects that are locally cached.

##### Answer:

```python
from socket import *
# set port number
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)
# Bind the listening address and port
serverSocket.bind(("0.0.0.0", serverPort))
serverSocket.listen(5)
print("The server is ready to receive")
while 1:
    connectSocket, addr = serverSocket.accept()
    sentence = connectSocket.recv(1024)
    print(sentence.decode())
    connectSocket.close()
```

Compile and execute the program, we can get:

```
GET /cs453/index.html HTTP/1.1<cr><lf>Host: gai
a.cs.umass.edu<cr><lf>User-Agent: Mozilla/5.0 (
Windows;U; Windows NT 5.1; en-US; rv:1.7.2) Gec
ko/20040804 Netscape/7.2 (ax) <cr><lf>Accept:ex
t/xml, application/xml, application/xhtml+xml, text
/html;q=0.9, text/plain;q=0.8,image/png,*/*;q=0.5
<cr><lf>Accept-Language: en-us,en;q=0.5<cr><lf>AcceptEncoding: zip,deflate<cr><lf>Accept-Charset: ISO
-8859-1,utf-8;q=0.7,*;q=0.7<cr><lf>Keep-Alive: 300<cr>
<lf>Connection:keep-alive<cr><lf><cr><lf>
```

