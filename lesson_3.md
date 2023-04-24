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

- When you're coding or debugging a web application it's important to be able to see where you are

## URLs
## Practice problems: URL components
## The Request Response Cycle
## Summary

Overview:

|  | Once | Twice | Thrice | Comprehension | Retention
| :--- | :---: | :---: | :---: | :--- | :---
|1. What to Focus on|11th April|
|2. The Application Layer|11th April|
|3.  HTTP and the web|12th April|
|4. Assignment: read HTTP book|12th - 23rd April|
|5. Some background diagrams|
|6.  URLs|
|7. Practice problems: URL components|
|8. The Request Response Cycle|
|9. Summary|
|10. Quiz |
| + Read through Discussions |
