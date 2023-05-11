(These are derived from [the study guide](https://launchschool.com/lessons/f48bf303/assignments/adbc20a4))

1. [What is the internet](https://launchschool.com/lessons/4af196b9/assignments/268243e5) is and how does it work?

 - The internet is a network of networks. Devices are connected to each other in various ways that enable them to transfer data. The first network your device connects to is the Local Area Network, which could be a home or office. At this point the data travels from your device to a network bridging device, such as a hub or switch. To connect your LAN to the wider internet your switch/hub sends the data on to a router. Routers are devices that exist to send data on to other machines on the internet. All of this data transferred is formatted according to protocols so that all devices know the agreed ways to read the messages. There are many protocols, but the first and most famous is Hyper Text Transfer Protocol (HTTP). Each message (or ‘packet’) between devices is a combination of different messages doing different jobs and these are organised in layers like Russian-nesting-dolls. Each layer will have a header (containing information about the packet) and a pay-load (which is the actual message). The packet is sent on a physical network as light signals or electrical signals or radio-waves. There’s much more to talk about such as DNS servers,  the client-server model, URLs and encryption, but I’ll stop there.


2. How does the internet differ from the world wide web?

- The internet is the physical infrastructure of devices linked with switches, hubs, routers, servers etc. The World Wide Web is a service provided on that infrastructure. So a web-page is part of the web, but a laptop is part of the internet. Allegories would be a book and the text or a road network and the shops/houses.

3. What are the characteristics of the physical network such as latency and bandwidth?	

-	As data travels between points on the internet the efficiency with which it can do so is measured in these two ways. Latency is the amount of time it takes. Bandwidth is how much data can be sent in a given time-frame. It’s comparable to a train having a maximum speed, but how big the train is also affects total passengers transported.

4. Explain how lower level protocols operate.

-	The layers of PDUs as they travel across the internet are conceptual aids for people and not strictly how the information is organised. Higher level protocols would be the Application and Transport layers and lower level protocols would be Network, Data-link and Physical layers.
-	Each layer of the PDU encapsulates the data for the layer below and the same in reverse.
-	Each layer operates independently of other layers. It completes its specific task and then passes the result to the next layer. During encapsulation this means taking the data from the layer above and passing it to the layer below. For instance, according to the TCP/IP model (Transmission Control Protocol / Internet Protocol) this would be the Internet layer taking the data from the Transport layer and passing the result of its encapsulation to the Link Layer.


5. What is a port address and an IP address	?

- [Relevant LS page here](https://launchschool.com/lessons/2a6c7439/assignments/41113e98)
- An IP address is a series of numbers between 0 and 255 representing a device’s address on the internet. It is what is used to direct traffic to the required destination. It only takes the information as far as the host. Once it has arrived the data needs to know which application it should go to. This is what ports are for. The PDU is directed to a specific port on a host so that multiple channels of communications can be maintained at once.  This allows multiple channels of communication between applications to be maintained on a single channel between hosts, which is called multiplexing.

6. How does DNS work?

- [DNS](https://github.com/SandyRodger/launch_school_books/blob/main/http_book.md#dns)
- DNS (Domain Name System) is a distributed database that takes a website name and finds its corresponding IP address. DNS databases are stored on DNS servers.
-	If a DNS server doesn’t contain the address it passes it up the hierarchy chain to the next DNS server and searches that.
-	It then sends back the IP address to be used in your PDUs. IP addresses are often saved in a browser cache, so if your browser already has the IP address it won’t search the DNS database.

7. What is the client-server model of web interactions and the role of HTTP protocol as a protocol within that model?

- Most data transfer on the internet happens between two hosts where one host is requesting something and the other is responding to that request. This is called the client-server model. HTTP is a set of rules for how messages between points on the internet should be formatted so that each side knows how to parse the Protocol Data Unit.

9. Explain the TCP and UDP protocols, their similarities and differences	

- TCP and UDP are protocols for data transfer at the transport layer. Their purpose is to make data transfer reliable even with HTTP, which is inherently unreliable.
- It abstracts reliable network communication away from the Application layer. So it takes care of de-duplication, data-integrity, in-order delivery and re-transmission of lost data.
- As well as taking care of reliability, TCP also deals with encapsulation and multiplexing, through th use of TCP segments.
- TCP is a connection oriented protocol. It uses a 'three-way handshake' system to establish a connection before it starts sending data.
- TCP does its job well, but this comes at a cost to performance. 
- UDP on the other hand does not guarantee message delivery, guarantee message delivery-order, have a built in congestion avoidance/ flow-control mechanism or provide connection state tracking.
- UDP's advantages are speed and flexibility. It allows, but to some degree also requires, a developer to implement their own forms of the features it lacks.

11. Explain the three-way handshake and its purpose.

-  This is a process of establishing a connection between application processes. It is implemented with TCP To do this the sender sends a SYN segment (to synchronise), the receiver sends back a SYN ACK segment (acknowledging receipt of the SYN segment) and the sender sends back an ACK segment and starts transmitting data.

12. What are flow control and congestion avoidance?

-  Flow control is a mechanism to prevent the sender from overwhelming the receiver with too much information sent too quickly.
 -  Congestion avoidance is everything done to avoid network congestion, such as monitoring retransmission, which indicates data-loss from routers, to detect congestion. In response it decreases the transmission window which is the amount of data it is transmitting in a given time. 

13. What are the components of a [URL](https://launchschool.com/lessons/cc97deb5/assignments/a28ccb6f), including query strings([also here](https://launchschool.com/books/http/read/what_is_a_url))

- URL stand for Uniform Resource Locator and is a type of URI (Uniform Resource identifier) which acts as an address for a resource on the internet. They are composed of:
 - the scheme
 - the host
 - the port
 - the path
 - the query string (made of query parameters)

14. Construct a valid URL.
15. What is URL encoding and when it might be used?
16. What are HTTP requests and responses? Identify the components of each.
17. Describe the HTTP request/response cycle
18. Explain what status codes are, and provide examples of different status code types.
19. What is meant by 'state' in the context of the web, and explain some techniques that are used to simulate state.
20. Explain the difference between GET and POST. When is each appropriate?
21. What are the various security risks that can affect HTTP?
22. What measures can be used to mitigate against these risks?
23. What are the different services that TLS can provide, give a broad description of each of those services
