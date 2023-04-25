# [Intro to HTTP](https://launchschool.com/lessons/cc97deb5/assignments)

## [What to focus on](https://launchschool.com/lessons/cc97deb5/assignments/cd70ff6d)

- Develop a clear understanding of the role of HTTP (not in isolation, but in context). The web as a combination of inter-woven technologies of which HTTP is one.
- Break things down into individual components. Break concepts like HTTP and URLs into parts in order to ensure clarity of each part's purpose.

## [The Application Layer](https://launchschool.com/lessons/cc97deb5/assignments/c604eb60)

- Bear in mind that the application layer is not the application itself.
- The application can talk to other layers apart from the application layer, but it will mainly talk to the protocols at the application layer.
- The OSI model defines 2 more layers between the application and transport layers. This is because of OSI's emphasis on different functions. We won't look at what those two do right now. 
- A common example of applications communicating with other layers would be an application creating a socket at the Transport layer. But it hardly ever happens that an application would communicate directly with any layer below that.
- The protocols we've looked at so far have been focused on the flow of communications (how messages get from one point to another). Application layer protocols rely on the layers below them to do this and instead deal with the structure of the message and the data it should contain.

### Application layer protocols

- Application layer protocols are rules for how applications talk to each other at a syntactical level.
- As a result there are many different protocols that exist at this level. For example the rules of how an email client communicates with a web-server because emails and web pages are fundamentally different things.
- If you were building an application for transferring files it would likely work with FTP. If you were building an email client it would almost certainly have to use some SMTP along with either POP or IMAP. In this lesson we'll just look at HTTP. That is the primary protocol used in communication on the web.

## [HTTP and the web](https://launchschool.com/lessons/cc97deb5/assignments/e3d85587)

- HTTP is the primary protocol used for  communication on the web (not the internet).
- The internet: A network of networks. The physical infrastructure that enables inter-network communication. Both in terms of the physical network and lower level protocols that control its use.
- The World Wide Web: A service that can be accessed via the internet. A vast information system comprised of resources which are navigable by means of a  URL (uniform resource locator).
- HTTP is tied historically and functionally to the web as we know it. It is the primary way in which applications interact with resources which make up the web.

### A brief history of the web

- The idea for the web was conceived at CERN in 1989 by Tim Berners-Lee.
- His idea was to leverage the internet connectivity along with an emerging technology called Hypertext to create an easily accessible information system.
- This system required uniformity:
  - How the resources were structured
  - How they were addressed.
  - How a request for a resource was made.
  - How such a request would be responded to.
- The way this was achieved combined three technologies: HTML, URIs and HTTP. This was the earliest incarnation of the internet.

- HyperText Markup Language:  The means by which resources in this system would be uniformly structured. This early version of HTML was intended for structuring text documents using headings, paragraphs and lists. It was very basic containing only 18 elements. Of these the most revolutionary was the anchor, `<A>` this used a `href` attribute to provide a link from one resource to another.
  - A Uniform Resource Identifier (URI) is a string of characters which identifies a particular resource. It is part of a system by which resources should be uniformly addressed on the web:
    - The web is an information space. Human beings have a lot of mental machinery for manipulating, imagining and finding their way in spaces. URIs are the points in that space.
  - "URI" and "URL" are often used interchangeably, but they are distinct. (more later).
  - HTTP: is the set of rules which provide uniformity to the way resources on the web are transferred between applications
  - In the beginning it was just text files on the internet, since then it has adapted to include lots more.  

## Assignment: read HTTP book
[my notes](https://github.com/SandyRodger/launch_school_books/blob/main/http_book.md)
## [Some background diagrams](https://launchschool.com/lessons/cc97deb5/assignments/586769d9)

- When you're coding or debugging a web application it's important to be able to see where you are.
- The ability to zoom in to a section of code, while understanding where you are on a larger scale is key to web development.

### Client - server

HTTP: A stateless protocol for how clients communicate with servers.

<p align="center">
<img width="730" alt="Screenshot 2023-04-25 at 14 31 32" src="https://user-images.githubusercontent.com/78854926/234292904-f57fa633-ff6d-46c5-9e4f-22e8c2310af5.png">
</p>

This is every interaction you have with a website.

Here is what is happening at the server:

<p align="center">
<img width="889" alt="Screenshot 2023-04-25 at 14 34 53" src="https://user-images.githubusercontent.com/78854926/234293794-344a2813-8ca3-4b07-8b56-e3783cd25b21.png">
</p>

This is very simplified. Each of these components could be shared across multiple machines, with intermediary machines (like load balancers). So the word 'server' is an umbrella term. Let's look at the three parts in the diagram above:
  - The web server
  - The application server
  - The data store

- A webserver: A server that responds to requests for static assets (files, images, javascript, css). These requests don'trequire any processing, so can be handled by a simple web-server.
- An application server: Where application or business logic resides. Here, more complicated requests are handled. This is where your server side-code lives when deployed.
- The application server will consult a persistent data-store, like a relational database, to retrieve or create data. Data stores can also be simple files or key-data stores, document stores or something else -  as long as it can save data in some format.
- Regardless of how it is stored, it can be used to *persist* data between stateless request/response cycles.

### HTTP over TCP/IP

<p align="center">
<img width="902" alt="Screenshot 2023-04-25 at 14 48 52" src="https://user-images.githubusercontent.com/78854926/234297513-d971ea76-5f25-4ba9-9b1b-8e540f6bb1dd.png">
</p>

- This diagram shows that HTTP is actually relying on a TCP/IP connection most of the time, even though they are different protocols operating at different levels.

In summary HTTP operates at the application layer and is concerned with structuring the messages that are exchanged between applications, but it's actually TCP/IP that is doing all the heavy lifting and ensuring that the response/request cycle gets completed between your browser and the server.

## [URLs](https://launchschool.com/lessons/cc97deb5/assignments/a28ccb6f)

- Distinction between URL and URI

### Schemes and protocols

- Scheme names lower-case, Protocol names upper-case.

### URLs and Filepaths

- Much of the content on the web now is generated dynamically.

## [Practice problems: URL components](https://launchschool.com/lessons/cc97deb5/assignments/d69da941)

|  | First go | result | second go | Comprehension | Retention
| :--- | :---: | :---: | :---: | :--- | :---
|1.|amazon.com|
|2.|
|3.|
|4.|
|5.|
|6.|
|7.|

| + Read through Discussions |


## The Request Response Cycle
## Summary

Overview:

|  | Once | Twice | Thrice | Comprehension | Retention
| :--- | :---: | :---: | :---: | :--- | :---
|1. What to Focus on|11th April|
|2. The Application Layer|11th April|
|3.  HTTP and the web|12th April|
|4. Assignment: read HTTP book|12th - 23rd April|
|5. Some background diagrams|24th April|
|6.  URLs|24th April|
|7. Practice problems: URL components|
|8. The Request Response Cycle|
|9. Summary|
|10. Quiz |
| + Read through Discussions |
