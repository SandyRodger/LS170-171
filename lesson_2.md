# [The Transport Layer](https://launchschool.com/lessons/2a6c7439/home)

- This layer deals with how networked applications communicate with each other:
  - how transport layer protocols enable communication between processes (?!)
  - Network reliability is engineered. Peel back the abstraction of the internet to reveal tangible processes that result in the internet we take for granted.
  - Understand the trade-offs (particularly between TCP and UDP).

## [Communication between processes](https://launchschool.com/lessons/2a6c7439/assignments/41113e98)

- The Internet Protocol provides the inter-network communication services necessary for "minimum viable internet".
- But to create networked applications we need more than IP.
  - A direct connection between applications
  - Reliable network communication.
- The IPs system of addressing is designed to provide communication between *hosts*. These hosts can be on the same network or on the other side of the world. IP is great for getting a message from Host A to Host B, but not more than that. 

I MADE GREAT NOTES FOR THIS ON SUNDAY, 9TH APRIL, BUT FAILED TO SAVE THEM. 

## [Network reliability](https://launchschool.com/lessons/2a6c7439/assignments/89636ed4)

- This chapter is all about how the sender and receiver of data in a network can reliably know whether the other end has successfully received the data.
- The two genreals problem video (Tom Scott):

https://www.youtube.com/watch?v=IP-rGJKSZ3s&vl=en

- Protocols such as the ethernet and internet protocols contain checksum data to prove to the receiver that the data after transmission is the same as when it was sent. But is the data is corrupt they just drop the packet. We need a system that guarantees that a packet of information will be replaced if it becomes lost or corrupt. 
- The possibility of losing data means that the network uo to and including the Internet Protocol is effectively an unreliable communication channel.
- As developers we need a reliable communication channel.
- At lower levels out communication channel is unreliable, so how to we ensure reliability.

### Building a reliable protocol

Solution 1:
- Use acknowledgement messages to ensure that the sender knows the transfer was successful.
  - Sender sends one message at a time
  - If message received, receiver sends acknowledgement back.
  - When acknowledgement received, sender sends next message.
 
 <p align="center">
  <img width="855" alt="Screenshot 2023-04-10 at 16 24 26" src="https://user-images.githubusercontent.com/78854926/230932176-575db796-872d-4546-ba3e-bfbb3b05821b.png">
</p>
  - Problem 1: If the receiver never gets the message the system fails.
  - Problem 2: If the acknowledgement message is corrupted/lost the system fails.

Solution 2:

- Resend the message if the acknowledgement is not received within a certain time-frame.
  - Sender sends one message at a time and sets a time-out
  - If message is received receiver sends acknowledgement.
  - When acknowledgement is received, sender sends next message.
  - If time-out expires before acknowledgement recieved sender assumes message has been lost and re-sends it. 

<p align="center">
<img width="805" alt="Screenshot 2023-04-10 at 16 30 10" src="https://user-images.githubusercontent.com/78854926/230933136-ec313447-f587-4524-8b7b-23ac93a941db.png">
</p>

- Problem: The receiver receives the message but the acknowledgement becomes corrupt/lost/ delayed to the extent that the sender resends the same message. The receiver is now getting duplicate messages.

Solution 3:

- Add a sequence of numbers (idempotency token) to the message.
  - Sender sends one message at a time with a timer and an idempotency token.
  - If received the receiver sends back an acknowledgement conaining the idempotency token, to indicate which message was received.
  - When acknowledgement is received the sender sends the next part of the sequence.
  - If acknowledgement is not received in time the sender re-sends the message with the same idempotency token.
  - If the receiver receives a duplicated token, it resends an acknowledgement with that token and discards the duplicated message.

<p align="center">
<img width="757" alt="Screenshot 2023-04-10 at 16 38 26" src="https://user-images.githubusercontent.com/78854926/230935633-606a6126-29f4-4e0e-901b-5f43c6b4add4.png">
</p>

- This solution covers the fundamental principles of reliable data-transfer
  - In-order delivery: Data is received in the order it was sent.
  - Error detection: Corrupt data is detected with a checksum.
  - Handling data-loss: Lost data is resent using a system of acknowledgements and time-outs.
  - Handling duplication: duplicate data is eliminated with an idempotency token system.
- The solution is effective, but inefficient. The solution is:

### Pipelining:
  - Sending multiple messages before receiving acknowledgements.
  - How does that impact reliability? It doesn't, the acknowledgment system is unchanged.
 
 <p align="center">
<img width="865" alt="Screenshot 2023-04-10 at 16 45 31" src="https://user-images.githubusercontent.com/78854926/230938239-75b7ff33-f9e1-40b7-9cb2-742112dfff7d.png">
</p>

- Different ways to pipeline:
  - Go back N
  - Selective repeat
- but the difference isn't important right now.
- With both systems the send implements a 'window' representing the maximum number of messages that can be 'in the pipeline' at any one time.
- Once it has received an acknowledgement it sends the next message:
 
 <p align="center">
  <img width="802" alt="Screenshot 2023-04-10 at 16 57 28" src="https://user-images.githubusercontent.com/78854926/230940667-5b668c63-aedf-41a3-9115-9a27d1e6cae5.png">
 </p>
 
 [interactive pipelining simulation](http://www.ccs-labs.org/teaching/rn/animations/gbn_sr/)
 
 - Pipelining is a more efficient use of bandwidth. Less time is spent waiting. More time is spent transmitting.
 - Finding a balance between reliability and performance is a key part of the Transmission Control Protocol(TCP)

## [Transmission Control Protocol(TCP](https://launchschool.com/lessons/2a6c7439/assignments/d09ddd52)

- The transmission control protocol is one of the corner-stones of the internet and one of its keyfeatures is providing reliable data transfer.
- TCP provides the abstraction of reliable data-transfer on top of an unreliable channel.
- What this abstraction does is to hide the complexity of reliable network communication from the application layer:
  - Data integrity.
  - de-duplication.
  - in-order delivery.
  - re-transmission of lost data.
- TCP is the protocol of choice for many networked applications because it provides great services.
- The disadvantage is that these services are the performance challenges that come with this complexity. (Just because the complexity is hidden from the dev working at the application layer doesn't mean its not there- it's real and does affect performance).
- TCP also provides:
  - Multiplexing
  - Data-encapsulation

### TCP segments
 
 - OK, so TCP segments are just like the PDUs discussed so far. They have a header and a data-payload. They encapsulate the entire PDU of the Application layer above it and are encapsulated by the layer benath, which is the Internet layer.
 
 <p align="center">
<img width="869" alt="Screenshot 2023-04-10 at 17 15 36" src="https://user-images.githubusercontent.com/78854926/230943883-f9503ff1-9f42-417a-aa54-cc1e1e2830db.png">
 </p>

-  A TCP segment header contains a number of fields:
  -  A Source port and destination port to allow multiplexing capabilities.
  -  Most of the other fields relate to the way TCP provides reliable data transfer.
- A typical TCP segment header might look like this (although bear in mind there are variants, but most will at a minimum contain these fields):
 
 <p align="center">
  <img width="874" alt="Screenshot 2023-04-10 at 21 36 24" src="https://user-images.githubusercontent.com/78854926/230993460-53ce99b1-eb2f-4fdc-a6b6-511ddd018fcb.png">
 </p>
 - Some of the more important fields in terms of implementing reliability are:
   - CHECKSUM: this provides the error detection aspect of TCP reliability. It is a value generated by the sender using an algorithm. The receiver generates a value using the same algorithm and if it doesn't match it drops the segment.
   - Other PDUs also use checksum values.
   - Having a checksum at the transport layer pretty much renders checksums at lower layers redundant. This is why ipv6 headers don't include one, assuming that checksums are implemented at either/both the Transport or Link/Data layer.
   - SEQUENCE NUMBER and ACKNOWLEDGEMENT NUMBER: These two fields are used together to provide for the other elements of TCP reliability, such as:
    - In-order delivery
    - Handling Data loss
    - Handling Duplication
  -  Precisely how this happens is beyond the scope of this course (but it looks a lot like the reliable-protocol covered in lesson 1).
  -  WINDOW SIZE: relates to flow control.
  -  FLAGS: sre one bit boolean fields.
    -  URG and PSH relate to how the data contained in this segment should be treated in terms of its importance/urgency.
    -  The SYN, ACK, FIN and RST flags are used to establish and end a TCP connection plus manage that connection.
### TCP Connections

- We covered connectionless v connection-based communication. TCP is connection-oriented.
- This means it doesn't start sending application data until a connection has been established between application processes.
- In order to establish a connection TCP uses a "three-way-handshake". THis involves the SYN and ACK flags.
- FIN is used in a "four-way-handshake" that terminates connections.
- The three way handshake looks like this:
<p align="center">
<img width="893" alt="Screenshot 2023-04-10 at 22 00 23" src="https://user-images.githubusercontent.com/78854926/230997932-0ae70d6a-5d6b-435e-a946-b026ccc957c9.png">
</p>

## [User datagram protocol (UDP)](https://launchschool.com/lessons/2a6c7439/assignments/9bb82c9b)
## [Summary](https://launchschool.com/lessons/2a6c7439/assignments/4ab0993c)

Overview:

|  | Once | Twice | Thrice | Comprehension | Retention
| :--- | :---: | :---: | :---: | :--- | :---
|2. What to Focus on| 6th April | 8th April | 
|3.  Communication between processes| 6th April | 9th April 
|4.  Network Reliability| 6th April |10th April
|5. Transmission Control Protocol| 6th April |
|6.  User Datagram Protocol| 6th April |
|7.  Summary|6th April |
|8. Quiz |
| + Read through Discussions |
