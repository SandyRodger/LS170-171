# [The Transport Layer](https://launchschool.com/lessons/2a6c7439/home)

- This layer deals with how networked applications communicate with each other:
  - how transport layer protocols enable communication between processes (?!)
  - Network reliability is engineered. Peel back the abstraction of the internet to reveal tangible processes that result in the internet we take for granted.
  - Understand the trade-offs (particularly between TCP and UDP).

## [Communication between processes](https://launchschool.com/lessons/2a6c7439/assignments/41113e98)

- The Internet PRotocol provides the inter-network communicationservaces necessary for "minimum viable internet".
- But to create networked applications we need more than IP.
  - A direct connection between applications
  - Reliable network communication.
- The IPs system of addressing is designed to provide communication between *hosts*. These hosts can be on the same network or on the other side of the world. IP is great for getting a message from A to B, but not more than that. 


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

- Problem 1: The receiver receives the message but the acknowledgement becomes corrupt/lost/ delayed to the extent that the sender resends the same message. The receiver is now getting duplicate messages.

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
  - How does that impact reliability? It doesn't, the aclknowledgment system is unchanged.
 
 <p align="center">
<img width="865" alt="Screenshot 2023-04-10 at 16 45 31" src="https://user-images.githubusercontent.com/78854926/230938239-75b7ff33-f9e1-40b7-9cb2-742112dfff7d.png">
</p>

## [Transmission Control Protocol(TCP](https://launchschool.com/lessons/2a6c7439/assignments/d09ddd52)
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
