(These are derived from [the study guide](https://launchschool.com/lessons/f48bf303/assignments/adbc20a4))

1. [What is the internet](https://launchschool.com/lessons/4af196b9/assignments/268243e5) is and how does it work?

 - The internet is a network of networks. Devices are connected to each other in various ways that enable them to transfer data. The first network your device connects to is the Local Area Network, which could be a home or office. At this point the data travels from your device to a network bridging device, such as a hub or switch. To connect your LAN to the wider internet your switch/hub sends the data on to a router. Routers are devices that exist to send data on to other machines on the internet. All of this data transferred is formatted according to protocols so that all devices know the agreed ways to read the messages. There are many protocols, but the first and most famous is Hyper Text Transfer Protocol (HTTP). Each message (or ‘packet’) between devices is a combination of different messages doing different jobs and these are organised in layers like Russian-nesting-dolls. Each layer will have a header (containing information about the packet) and a pay-load (which is the actual message). The packet is sent on a physical network as light signals or electrical signals or radio-waves. There’s much more to talk about such as DNS servers,  the client-server model, URLs and encryption, but I’l stop there.


2. How does the internet differ from the world wide web?

- The internet is the physical infrastructure of devices linked with switches, hubs, routers, servers etc. The World Wide Web is a service provided on that infrastructure. So a web-page is part of the web, but a laptop is part of the internet. Allegories would be a book and the text or a road network and the shops/houses.

3. What are the characteristics of the physical network such as latency and bandwidth?	

- -	As data travels between points on the internet the efficiency with which it can do so is measured in these two ways. Latency is the amount of time it takes. Bandwidth is how much data can be sent in a given time-frame. It’s comparable to a train having a maximum speed, but how many parallel train tracks there are also affects total passengers transported.

4. Explain how lower level protocols operate.

- -	The layers of PDUs as they travel across the internet are conceptual aids for people and not strictly how the information is organised. Higher level protocols would be the Application and Transport layers and lower level protocols would be Network, Data-link and Physical layers.
-	Each layer of the PDU encapsulates the data for the layer below and the same in reverse.
-	Each layer operates independently of other layers. It completes its specific task and then passes the result to the next layer. During encapsulation this means taking the data from the layer above and passing it to the layer below. For instance, according to the TCP/IP model (Transmission Control Protocol / Internet Protocol) this would be the Internet layer taking the data from the Transport layer and passing the result of its encapsulation to the Link Layer.


5. What is a port address and an IP address	?

- [Answer here](https://launchschool.com/lessons/2a6c7439/assignments/41113e98)
- 

6. How does DNS work?
7. What is the client-server model of web interactions and the role of HTTP protocol as a protocol within that model?
8. Explain the TCP and UDP protocols, their similarities and differences	
9. Explain the three-way handshake and its purpose.
10. What are flow control and congestion avoidance?
11. What are the components of a URL, including query strings	
12. Construct a valid URL.
13. What is URL encoding and when it might be used?
14. What are HTTP requests and responses? Identify the components of each.
15. Describe the HTTP request/response cycle
16. Explain what status codes are, and provide examples of different status code types.
17. What is meant by 'state' in the context of the web, and explain some techniques that are used to simulate state.
18. Explain the difference between GET and POST. When is each appropriate?
19. What are the various security risks that can affect HTTP?
20. What measures can be used to mitigate against these risks?
21. What are the different services that TLS can provide, give a broad description of each of those services
