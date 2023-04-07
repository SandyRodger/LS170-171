# [The Internet](https://launchschool.com/lessons/4af196b9)

## [Introduction](https://launchschool.com/lessons/4af196b9/assignments/89b5fc88)
-  Outlines what the course is
## [What to focus on](https://launchschool.com/lessons/4af196b9/assignments/a6f8ef54)
- Build a general picture of the network infrastructure.
- Be aware of the limitations of the physical network.
- Understand that protocols are systems of rules.
- Learn that IP enables communication between devices.
## [AWS Cloud9](https://launchschool.com/lessons/4af196b9/assignments/fe5b1fbe)
- The argument for AWS at this part of the course & how to install it. (nothing to learn)
## [What is the internet?](https://launchschool.com/lessons/4af196b9/assignments/268243e5)
- A network of networks.
- A network: 2 or more devices connected in such a way that they can communicate or exchange data.
  - At its most basic this is 2 computers connected by a LAN cable.
  - At its most complex it is the whole internet 
- Local Area Network (LAN): A bunch of computers physically near to each other connected by network cables. An office for instance.

<p align="center">
<img width="627" alt="Screenshot 2023-04-07 at 14 11 06" src="https://user-images.githubusercontent.com/78854926/230614563-05bb1e8a-a747-4313-b757-92dce966ad13.png">
</p>
- Your home network is the same, probably with a wireless hub or switch. This is a WLAN.
- The hub or switch is the "local" in LAN.

### Inter-network communication:

- Routers are network devices that can route network traffic to other networks. For a LAN they are the gatekeepers in and out.

<p align="center">
<img width="902" alt="Screenshot 2023-04-07 at 14 25 54" src="https://user-images.githubusercontent.com/78854926/230616710-83b4a14a-7008-484f-b6f8-87db32950e4c.png">
</p>

### A network of networks:

- The intenet is many sub-networks (like your home) connected by routers:

<p align="center">
<img width="898" alt="Screenshot 2023-04-07 at 14 28 33" src="https://user-images.githubusercontent.com/78854926/230617057-6585308d-8a00-473d-9bfb-ce659f456f5d.png">
</p>

## [Protocols](https://launchschool.com/lessons/4af196b9/assignments/a53e65ce)

- The internet is made by many different devices and different softwares. So in order for them to communicate there are rules that govern the way they send and receive messages. These are protocols.
- "A set of rules that govern the exchange or transmission of information."
- There are many protocols. 
- Why?
  - To address different aspects of network communication. (Structure)
  - To address the same aspect of network communication, but for a different use case. (message transfer rules).
- Different aspects of communication could be:
  -  The structure of the message
  -  The order in which messages are sent and received
- Different protocols for the same aspect:
  - speaking to the teacher in a class
  - speaking to a friend in a social setting.
  - To address the same aspect of network communication, but for a different use case.
- TCP and UDP are examples of 2 protocols that control the same aspect of communication differently.

## [A layered system](https://launchschool.com/lessons/4af196b9/assignments/21ef33af)

- Protocols are best grouped together by the aspect of communication they deal with.
- Rather than trying to understand all aspects of communication simultaneously (language, physics, biology, etiquette) there are models for message thransfer that aim to deal with everything in a manageable way. The two main ways are :
  - The Internet Protocol Suite
  - The OSI model.
<p align="center">
<img width="738" alt="Screenshot 2023-04-07 at 15 18 37" src="https://user-images.githubusercontent.com/78854926/230624307-5728f0a0-946b-43dd-bac2-2ae6c425f17f.png">
</p>

- The Internet protocol suite divides layers by **scope of communication**
  - Within a Local network
  - between networks
  - etc. 
- The OSI model divides layers by **the function that each layer supplies**
  - Physical addressing
  - logical addressing and routing
  - encryption
  - compression 
 - Both models have their advantages, but no model will perfectly fit real-world implementation.
### Data encapsulation
- A concept used by most network communication models.
- Hiding data from one layer by hiding it within a data-unit of the level below.

### Protocol Data Units
- A block of data transferred over a network.
- Different protocols and different layers within a protocol refer to PDUs by different names. 

| Layer | Name for PDU
| :---: | :---: |
|link/data layer|'frame'
|Internet/Network 'layer|packet'
|Transport layer|'datagram' or 'segment'

- Despite the different names PDUs always consist of a header, a data payload and in some cases a trailer/footer.
- **The header** provides protocal specific meta-data about the PDU.
  - For example an IP packet header would include fields for the Source IP address and the Destination IP address, which would be used to correctly route the packet.
- **The Data Payload** Is the data we want to transfer.
- The entire PDU from a protocol at one layer is set as the data payload for a protocol at the layer below
  - For example a HTTP request at the Application Layer could be set as the payload for a TCP segment at the Transport layer.
<p align="center">
  <img width="874" alt="Screenshot 2023-04-07 at 15 56 18" src="https://user-images.githubusercontent.com/78854926/230629907-fe2f5ee4-4692-49bc-9274-a049b7999f8b.png">
</p>
- The major benefit of this approach is the seperation it creates between the different layers of the protocol. So each layer needn't know anything about how a protocol at another layer is implemented in order to interact. It does its little job, without worrying about what is happening at the other levels.
- Lower levels do a task for the level above them.
- Sandy's image: a slice of ham on floor 5 gets thrown down to floor 4, they put it between slices of bread, throw it down to level 3, they wrap it in cling-film, throw it down to floor 2, they put it in a box, throw it down to floor 1, they put it in a car and drive away.
- The seperation of layers provides a level of abstraction which allows us to use different protocols at one layer without worryinbg about the other layers.
  - A good example of this is at the Application layer where many different protocols are used depending on the application and use case.
## [The physical network](https://launchschool.com/lessons/4af196b9/assignments/097d7577)
## [ The data/link layer](https://launchschool.com/lessons/4af196b9/assignments/81df3782)
## [The internet/network layer](https://launchschool.com/lessons/4af196b9/assignments/b222ecfb)
## [Summary](https://launchschool.com/lessons/4af196b9/assignments/6b7df8fb)
## [Quiz](https://launchschool.com/lessons/4af196b9/assignments/d810a100)
## [Ginni's notes](https://github.com/gcpinckert/ls170_171/blob/main/study_guide/the_internet.md)

 
Lesson 1: The Internet

|  | Once | Twice | Thrice | How well do you know this?
| :--- | :---: | :---: | :---: | :--- 
|1. Introduction|4th April| 7th April||N/A
|2. What to Focus on|4th April|7th April||N/A
|3.  AWS Cloud 9|4th April|7th April||N/A
|4.  What is the internet?|4th April|7th April || 90%
|5. Protocols|4th April|7th April||
|6.  A layered system|4th April| |
|7. The Physical network|4th April| |
|8.  The data/link layer|4th April| |
|9.  The internet/network layer |4th April| |
|10.  Summary|4th April| |
|11. Quiz |4th April (44%)| |
| + Read through Discussions |
