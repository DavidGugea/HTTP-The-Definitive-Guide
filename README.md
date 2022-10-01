# HTTP - The Definitive Guide

## Part I. HTTP: The Web's Foundation

### 1. Overview of HTTP
### 2. URLs and Resources
### 3. HTTP Messages
### 4. Connection Management

## Part II: HTTP Architecture

### 5. Web Servers
### 6. Proxies
### 7. Caching
### 8. Integration Points: Gateways, Tunnels, and Relays
### 9. Web Robots
### 10. HTTP-NG

## Part III: Identification, Authorization, and Security

### 11. Client Identification and Cookies
### 12. Basic Authentication
### 13. Digest Authentication
### 14. Secure HTTP

## Part IV: Entities, Encodings, and Internationalization

### 15. Entities and Encodings
### 16. Internationalization
### 17. Content Negotiation and Transcoding

## Part V: Content Publishing and Distribution

### 18. Web Hosting
### 19. Publishin Systems
### 20. Redirection and Load Balancing
### 21. Logging and Usage Tracking

---
---

# Part I. HTTP: The Web's Foundation

---

# 1. Overview of HTTP

## Web Clients and Servers

Web content lives on web servers. Web servers speak the HTTP protocol, so they are often called HTTP servers. These HTTP servers store the Internet’s data and provide the data when it is requested by HTTP clients. The clients send HTTP requests to servers, and servers return the requested data in HTTP responses, as sketched in the following figure. Together, HTTP clients and HTTP servers make up the basic components of the World Wide Web.

![Web Clients And Servers](ScreenshotsForNotes/Chapter1/WebClientsAndServers.PNG)

You probably use HTTP clients every day. The most common client is a web browser, such as Microsoft Internet Explorer or Netscape Navigator. Web browsers request HTTP objects from servers and display the objects on your screen.

When you browse to a page, such as “http://www.oreilly.com/index.html,” your browser sends an HTTP request to the server www.oreilly.com (see Figure 1-1). The server tries to find the desired object (in this case, “/index.html”) and, if successful, sends the object to the client in an HTTP response, along with the type of the object, the length of the object, and other information.

## Resources

Web servers host web resources. A web resource is the source of web content. The simplest kind of web resource is a static file on the web server’s filesystem. These files can contain anything: they might be text files, HTML files, Microsoft Word files, Adobe Acrobat files, JPEG image files, AVI movie files, or any other format you can think of.

However, resources don’t have to be static files. Resources can also be software programs that generate content on demand. These dynamic content resources can generate content based on your identity, on what information you’ve requested, or on the time of day. They can show you a live image from a camera, or let you trade stocks, search real estate databases, or buy gifts from online stores (see Figure 1-2).

![Figure1_2](ScreenshotsForNotes/Chapter1/Figure1_2.PNG)

In summary, a resource is any kind of content source. A file containing your company’s sales forecast spreadsheet is a resource. A web gateway to scan your local public library’s shelves is a resource. An Internet search engine is a resource.

## Media Types

Because the Internet hosts many thousands of different data types, HTTP carefully tags each object being transported through the Web with a data format label called a MIME type. MIME (Multipurpose Internet Mail Extensions) was originally designed to solve problems encountered in moving messages between different electronic mail systems. MIME worked so well for email that HTTP adopted it to describe and label its own multimedia content.

Web servers attach a MIME type to all HTTP object data (see Figure 1-3). When a web browser gets an object back from a server, it looks at the associated MIME type to see if it knows how to handle the object. Most browsers can handle hundreds of popular object types: displaying image files, parsing and formatting HTML files, playing audio files through the computer’s speakers, or launching external plug-in software to handle special formats.

![Figure1_3](ScreenshotsForNotes/Chapter1/Figure1_3.PNG)

A MIME type is a textual label, represented as a primary object type and a specific subtype, separated by a slash. For example:

* An HTML-formatted text document would be labeled with type text/html.
* A plain ASCII text document would be labeled with type text/plain.
* A JPEG version of an image would be image/jpeg.
* A GIF-format image would be image/gif.
* An Apple QuickTime movie would be video/quicktime.
* A Microsoft PowerPoint presentation would be application/vnd.ms-powerpoint.

There are hundreds of popular MIME types, and many more experimental or limiteduse

## URIs

Each web server resource has a name, so clients can point out what resources they are interested in. The server resource name is called a uniform resource identifier, or URI. URIs are like the postal addresses of the Internet, uniquely identifying and locating information resources around the world.

Here’s a URI for an image resource on Joe’s Hardware store’s web server:

```
http://www.joes-hardware.com/specials/saw-blade.gif
```

Figure 1-4 shows how the URI specifies the HTTP protocol to access the saw-blade GIF resource on Joe’s store’s server. Given the URI, HTTP can retrieve the object. URIs come in two flavors, called URLs and URNs. Let’s take a peek at each of these types of resource identifiers now.

## URLs

The uniform resource locator (URL) is the most common form of resource identifier. URLs describe the specific location of a resource on a particular server. They tell you exactly how to fetch a resource from a precise, fixed location. Figure 1-4 shows how a URL tells precisely where a resource is located and how to access it. Table 1-1 shows a few examples of URLs.

![Figure1_4Table1_1](ScreenshotsForNotes/Chapter1/Figure1_4Table1_1.PNG)

Most URLs follow a standardized format of three main parts:

* The first part of the URL is called the scheme, and it describes the protocol used to access the resource. This is usually the HTTP protocol (http://).

* The second part gives the server Internet address (e.g., www.joes-hardware.com).

* The rest names a resource on the web server (e.g., /specials/saw-blade.gif ).

Today, almost every URI is a URL.

## URNs

The second flavor of URI is the uniform resource name, or URN. A URN serves as a unique name for a particular piece of content, independent of where the resource currently resides. These location-independent URNs allow resources to move from place to place. URNs also allow resources to be accessed by multiple network access protocols while maintaining the same name.

For example, the following URN might be used to name the Internet standards document “RFC 2141” regardless of where it resides (it may even be copied in several places):

```
urn:ietf:rfc:2141
```

## Transactions

Let’s look in more detail how clients use HTTP to transact with web servers and their resources. An HTTP transaction consists of a request command (sent from client to server), and a response result (sent from the server back to the client). This communication happens with formatted blocks of data called HTTP messages, as illustrated in Figure 1-5.

![Figure1_5](ScreenshotsForNotes/Chapter1/Figure1_5.PNG)

## Methods

HTTP supports several different request commands, called HTTP methods. Every HTTP request message has a method. The method tells the server what action to perform (fetch a web page, run a gateway program, delete a file, etc.). Table 1-2lists five common HTTP methods.

![Table](ScreenshotsForNotes/Chapter1/Table1_2_1.PNG) ![Table](ScreenshotsForNotes/Chapter1/Table1_2_2.PNG)

## Status Codes

Every HTTP response message comes back with a status code. The status code is a three-digit numeric code that tells the client if the request succeeded, or if other actions are required. A few common status codes are shown in Table 1-3.

![Table1_3](ScreenshotsForNotes/Chapter1/Table1_3.PNG)

HTTP also sends an explanatory textual “reason phrase” with each numeric status code (see the response message in Figure 1-5). The textual phrase is included only for descriptive purposes; the numeric code is used for all processing.

The following status codes and reason phrases are treated identically by HTTP software:

```
200 OK
200 Document attached
200 Success
200 All’s cool, dude
```

## Web Pages Can Consist of Multiple Objects

An application often issues multiple HTTP transactions to accomplish a task. For example, a web browser issues a cascade of HTTP transactions to fetch and display a graphics-rich web page. The browser performs one transaction to fetch the HTML “skeleton” that describes the page layout, then issues additional HTTP transactions for each embedded image, graphics pane, Java applet, etc. These embedded resources might even reside on different servers, as shown in Figure 1-6. Thus, a “web page” often is a collection of resources, not a single resource.

![Figure1_6](ScreenshotsForNotes/Chapter1/Figure1_6.PNG)

## Messages

Now let’s take a quick look at the structure of HTTP request and response messages. We’ll study HTTP messages in exquisite detail in Chapter 3.

HTTP messages are simple, line-oriented sequences of characters. Because they are plain text, not binary, they are easy for humans to read and write.* Figure 1-7 shows the HTTP messages for a simple transaction.

![Figure1_7](ScreenshotsForNotes/Chapter1/Figure1_7.PNG)

HTTP messages sent from web clients to web servers are called request messages. Messages from servers to clients are called response messages. There are no other kinds of HTTP messages. The formats of HTTP request and response messages are very similar.

HTTP messages consist of three parts:

* Start line
    * The first line of the message is the start line, indicating what to do for a request or what happened for a response.
* Header fields
    * Zero or more header fields follow the start line. Each header field consists of a name and a value, separated by a colon (:) for easy parsing. The headers end with a blank line. Adding a header field is as easy as adding another line.
* Body
    * After the blank line is an optional message body containing any kind of data. Request bodies carry data to the web server; response bodies carry data back to the client. Unlike the start lines and headers, which are textual and structured, the body can contain arbitrary binary data (e.g., images, videos, audio tracks, software applications). Of course, the body can also contain text.     ## Simple Message Example

Figure 1-8 shows the HTTP messages that might be sent as part of a simple transaction. The browser requests the resource http://www.joes-hardware.com/tools.html.

In Figure 1-8, the browser sends an HTTP request message. The request has a GET method in the start line, and the local resource is /tools.html. The request indicates it is speaking Version 1.0 of the HTTP protocol. The request message has no body, because no request data is needed to GET a simple document from a server.

The server sends back an HTTP response message. The response contains the HTTP version number (HTTP/1.0), a success status code (200), a descriptive reason phrase (OK), and a block of response header fields, all followed by the response body containing the requested document. The response body length is noted in the Content- Length header, and the document’s MIME type is noted in the Content-Type header.

### Connections

Now that we’ve sketched what HTTP’s messages look like, let’s talk for a moment about how messages move from place to place, across Transmission Control Protocol (TCP) connections.

### TCP/IP

HTTP is an application layer protocol. HTTP doesn’t worry about the nitty-gritty details of network communication; instead, it leaves the details of networking to TCP/IP, the popular reliable Internet transport protocol.

![Figure1_8](ScreenshotsForNotes/Chapter1/Figure1_8.PNG)

TCP provides:

* Error-free data transportation
* In-order delivery (data will always arrive in the order in which it was sent)
* Unsegmented data stream (can dribble out data in any size at any time)

The Internet itself is based on TCP/IP, a popular layered set of packet-switched network protocols spoken by computers and network devices around the world. TCP/IP hides the peculiarities and foibles of individual networks and hardware, letting computers and networks of any type talk together reliably.

Once a TCP connection is established, messages exchanged between the client and server computers will never be lost, damaged, or received out of order.

In networking terms, the HTTP protocol is layered over TCP. HTTP uses TCP to transport its message data. Likewise, TCP is layered over IP (see Figure 1-9).

![Figure1_9](ScreenshotsForNotes/Chapter1/Figure1_9.PNG)

## Connections, IP Addresses, and Port Numbers

Before an HTTP client can send a message to a server, it needs to establish a TCP/IP connection between the client and server using Internet protocol (IP) addresses and port numbers.

Setting up a TCP connection is sort of like calling someone at a corporate office. First, you dial the company’s phone number. This gets you to the right organization. Then, you dial the specific extension of the person you’re trying to reach.

In TCP, you need the IP address of the server computer and the TCP port number associated with the specific software program running on the server.

This is all well and good, but how do you get the IP address and port number of the HTTP server in the first place? Why, the URL, of course! We mentioned before that URLs are the addresses for resources, so naturally enough they can provide us with the IP address for the machine that has the resource. Let’s take a look at a few URLs:

```
http://207.200.83.29:80/index.html
http://www.netscape.com:80/index.html
http://www.netscape.com/index.html
```

The first URL has the machine’s IP address, “207.200.83.29”, and port number, “80”.

The second URL doesn’t have a numeric IP address; it has a textual domain name, or hostname (“www.netscape.com”). The hostname is just a human-friendly alias for an IP address. Hostnames can easily be converted into IP addresses through a facility called the Domain Name Service (DNS), so we’re all set here, too. We will talk much more about DNS and URLs in Chapter 2.

The final URL has no port number. When the port number is missing from an HTTP URL, you can assume the default value of port 80.

With the IP address and port number, a client can easily communicate via TCP/IP. Figure 1-10 shows how a browser uses HTTP to display a simple HTML resource that resides on a distant server.

Here are the steps:

a. The browser extracts the server’s hostname from the URL.

b. The browser converts the server’s hostname into the server’s IP address.

c. The browser extracts the port number (if any) from the URL.

d. The browser establishes a TCP connection with the web server.


e. The browser sends an HTTP request message to the server.

f. The server sends an HTTP response back to the browser.

g. The connection is closed, and the browser displays the document.

![Figure1_10](ScreenshotsForNotes/Chapter1/Figure1_10.PNG)

## Protocol Versions

There are several versions of the HTTP protocol in use today. HTTP applications need to work hard to robustly handle different variations of the HTTP protocol. The versions in use are:

* HTTP/0.9
    * The 1991 prototype version of HTTP is known as HTTP/0.9. This protocol contains many serious design flaws and should be used only to interoperate with legacy clients. HTTP/0.9 supports only the GET method, and it does not support MIME typing of multimedia content, HTTP headers, or version numbers. HTTP/0.9 was originally defined to fetch simple HTML objects. It was soon replaced with HTTP/1.0.
* HTTP/1.0
    * 1.0 was the first version of HTTP that was widely deployed. HTTP/1.0 added version numbers, HTTP headers, additional methods, and multimedia object handling. HTTP/1.0 made it practical to support graphically appealing web pages and interactive forms, which helped promote the wide-scale adoption of the World Wide Web. This specification was never well specified. It represented a collection of best practices in a time of rapid commercial and academic evolution of the protocol.
* HTTP/1.0+
    * Many popular web clients and servers rapidly added features to HTTP in the mid-1990s to meet the demands of a rapidly expanding, commercially successful World Wide Web. Many of these features, including long-lasting “keepalive” connections, virtual hosting support, and proxy connection support, were added to HTTP and became unofficial, de facto standards. This informal, extended version of HTTP is often referred to as HTTP/1.0+.
* HTTP/1.1
    * HTTP/1.1 focused on correcting architectural flaws in the design of HTTP, specifying semantics, introducing significant performance optimizations, and removing mis-features. HTTP/1.1 also included support for the more sophisticated web applications and deployments that were under way in the late 1990s. HTTP/1.1 is the current version of HTTP.

## Architectural Components of the Web

In this overview chapter, we’ve focused on how two web applications (web browsers and web servers) send messages back and forth to implement basic transactions. There are many other web applications that you interact with on the Internet. In this section, we’ll outline several other important applications, including:

* Proxies: HTTP intermediaries that sit between clients and servers
* Caches: HTTP storehouses that keep copies of popular web pages close to clients
* Gateways: Special web servers that connect to other applications
* Tunnels: Special proxies that blindly forward HTTP communications
* Agents: Semi-intelligent web clients that make automated HTTP requests

## Proxies

Let’s start by looking at HTTP proxy servers, important building blocks for web security, application integration, and performance optimization.

As shown in Figure 1-11, a proxy sits between a client and a server, receiving all of the client’s HTTP requests and relaying the requests to the server (perhaps after modifying the requests). These applications act as a proxy for the user, accessing the server on the user’s behalf.

![Figure1_11](ScreenshotsForNotes/Chapter1/Figure1_11.PNG)

Proxies are often used for security, acting as trusted intermediaries through which all web traffic flows. Proxies can also filter requests and responses; for example, to detect application viruses in corporate downloads or to filter adult content away from elementary-school students. We’ll talk about proxies in detail in Chapter 6.

## Caches

A web cache or caching proxy is a special type of HTTP proxy server that keeps copies of popular documents that pass through the proxy. The next client requesting the same document can be served from the cache’s personal copy (see Figure 1-12).

![Figure1_12](ScreenshotsForNotes/Chapter1/Figure1_12.PNG)

A client may be able to download a document much more quickly from a nearby cache than from a distant web server. HTTP defines many facilities to make caching more effective and to regulate the freshness and privacy of cached content. We cover caching technology in Chapter 7.

## Gateways

Gateways are special servers that act as intermediaries for other servers. They are often used to convert HTTP traffic to another protocol. A gateway always receives requests as if it was the origin server for the resource. The client may not be aware it is communicating with a gateway.

For example, an HTTP/FTP gateway receives requests for FTP URIs via HTTP requests but fetches the documents using the FTP protocol (see Figure 1-13). The resulting document is packed into an HTTP message and sent to the client. We discuss gateways in Chapter 8.

![Figure1_13](ScreenshotsForNotes/Chapter1/Figure1_13.PNG)

## Tunnels

Tunnels are HTTP applications that, after setup, blindly relay raw data between two connections. HTTP tunnels are often used to transport non-HTTP data over one or more HTTP connections, without looking at the data.

One popular use of HTTP tunnels is to carry encrypted Secure Sockets Layer (SSL) traffic through an HTTP connection, allowing SSL traffic through corporate firewalls that permit only web traffic. As sketched in Figure 1-14, an HTTP/SSL tunnel receives an HTTP request to establish an outgoing connection to a destination address and port, then proceeds to tunnel the encrypted SSL traffic over the HTTP channel so that it can be blindly relayed to the destination server.

## Agents

User agents (or just agents) are client programs that make HTTP requests on the user’s behalf. Any application that issues web requests is an HTTP agent. So far, we’ve talked about only one kind of HTTP agent: web browsers. But there are many other kinds of user agents.

![Figure1_14](ScreenshotsForNotes/Chapter1/Figure1_14.PNG)

For example, there are machine-automated user agents that autonomously wander the Web, issuing HTTP transactions and fetching content, without human supervision. These automated agents often have colorful names, such as “spiders” or “web robots” (see Figure 1-15). Spiders wander the Web to build useful archives of web content, such as a search engine’s database or a product catalog for a comparisonshopping robot. See Chapter 9 for more information.

![Figure1_15](ScreenshotsForNotes/Chapter1/Figure1_15.PNG)

# 2. URLs and Resources

## Navigating the Internet's Resources

URLs are the resource locations that your browser needs to find information. They let people and applications find, use, and share the billions of data resources on the Internet. URLs are the usual human access point to HTTP and other protocols: a person points a browser at a URL and, behind the scenes, the browser sends the appropriate protocol messages to get the resource that the person wants.

URLs actually are a subset of a more general class of resource identifier called a uniform resource identifier, or URI. URIs are a general concept comprised of two main subsets, URLs and URNs. URLs identify resources by describing where resources are located, whereas URNs (which we’ll cover later in this chapter) identify resources by name, regardless of where they currently reside.

The HTTP specification uses the more general concept of URIs as its resource identifiers; in practice, however, HTTP applications deal only with the URL subset of URIs. Throughout this book, we’ll sometimes refer to URIs and URLs interchangeably, but we’re almost always talking about URLs.

Say you want to fetch the URL http://www.joes-hardware.com/seasonal/index-fall.html:

* The first part of the URL (http) is the URL scheme. The scheme tells a web client how to access the resource. In this case, the URL says to use the HTTP protocol.

* The second part of the URL (www.joes-hardware.com) is the server location. This tells the web client where the resource is hosted.

* The third part of the URL (/seasonal/index-fall.html) is the resource path. The path tells what particular local resource on the server is being requested.

See Figure 2-1 for an illustration.

![Figure-2-1](ScreenshotsForNotes/Chapter2/Figure_2_1.PNG)

URLs can direct you to resources available through protocols other than HTTP. They can point you to any resource on the Internet, from a person’s email account:

``` mailto:president@whitehouse.gov ```

to files that are available through other protocols, such as the File Transfer Protocol (FTP):

```ftp://ftp.lots-o-books.com/pub/complete-price-list.xls```

to movies hosted off of streaming video servers:

```rtsp://www.joes-hardware.com:554/interview/cto_video```

URLs provide a way to uniformly name resources. Most URLs have the same “scheme://server location/path” structure. So, for every resource out there and every way to get those resources, you have a single way to name each resource so that anyone can use that name to find it. However, this wasn’t always the case.

## The Dark Days Before URLs

Before the Web and URLs, people relied on a rag-tag assortment of applications to access data distributed throughout the Net. Most people were not lucky enough to have all the right applications or were not savvy and patient enough to use them.

Before URLs came along, if you wanted to share the complete-catalog.xls file with a friend, you would have had to say something like this: “Use FTP to connect to ftp. joes-hardware.com. Log in as anonymous. Then type your username as the password. Change to the pub directory. Switch to binary mode. Now download the file named complete-catalog.xls to your local filesystem and view it there.”

Today, browsers such as Netscape Navigator and Microsoft Internet Explorer bundle much of this functionality into one convenient package. Using URLs, these applications are able to access many resources in a uniform way, through one interface. Instead of the complicated instructions above, you could just say “Point your browser at ftp://ftp.lots-o-books.com/pub/complete-catalog.xls.”

URLs have provided a means for applications to be aware of how to access a resource. In fact, many users are probably unaware of the protocols and access methods their browsers use to get the resources they are requesting.

With web browsers, you no longer need a news reader to read Internet news or an FTP client to access files on FTP servers. You don’t need an electronic mail program to send and receive email messages. URLs have helped to simplify the online world, by allowing the browser to be smart about how to access and handle resources. Applications can use URLs to simplify access to information.

URLs give you and your browser all you need to find a piece of information. They define the particular resource you want, where it is located, and how to get it.

## URL Syntax

URLs provide a means of locating any resource on the Internet, but these resources can be accessed by different schemes (e.g., HTTP, FTP, SMTP), and URL syntax varies from scheme to scheme.

Does this mean that each different URL scheme has a radically different syntax? In practice, no. Most URLs adhere to a general URL syntax, and there is significant overlap in the style and syntax between different URL schemes.

Most URL schemes base their URL syntax on this nine-part general format:

```<scheme>://<user>:<password>@<host>:<port>/<path>;<params>?<query>#<frag>```

Almost no URLs contain all these components. The three most important parts of a URL are the scheme, the host, and the path. Table 2-1 summarizes the various components.

![Table-2-1](ScreenshotsForNotes/Chapter2/Table_2_1.PNG)

For example, consider the URL http://www.joes-hardware.com:80/index.html. The scheme is “http”, the host is “www.joes-hardware.com”, the port is “80”, and the path is “/index.html”.

### Schemes: What Protocol to Use

The scheme is really the main identifier of how to access a given resource; it tells the application interpreting the URL what protocol it needs to speak. In our simple HTTP URL, the scheme is simply “http”.

The scheme component must start with an alphabetic character, and it is separated from the rest of the URL by the first “:” character. Scheme names are caseinsensitive, so the URLs “http://www.joes-hardware.com” and “HTTP://www.joeshardware. com” are equivalent.

### Hosts and Ports

To find a resource on the Internet, an application needs to know what machine is hosting the resource and where on that machine it can find the server that has access to the desired resource. The host and port components of the URL provide these two pieces of information.

The host component identifies the host machine on the Internet that has access to the resource. The name can be provided as a hostname, as above (“www.joes-hardware. com”) or as an IP address. For example, the following two URLs point to the same resource—the first refers to the server by its hostname and the second by its IP address:

```
http://www.joes-hardware.com:80/index.html
http://161.58.228.45:80/index.html
```

The port component identifies the network port on which the server is listening. For HTTP, which uses the underlying TCP protocol, the default port is 80.

### Usernames and Passwords

More interesting components are the user and password components. Many servers require a username and password before you can access data through them. FTP servers are a common example of this. Here are a few examples:

```
ftp://ftp.prep.ai.mit.edu/pub/gnu
ftp://anonymous@ftp.prep.ai.mit.edu/pub/gnu
ftp://anonymous:my_passwd@ftp.prep.ai.mit.edu/pub/gnu
http://joe:joespasswd@www.joes-hardware.com/sales_info.txt
```

The first example has no user or password component, just our standard scheme, host, and path. If an application is using a URL scheme that requires a username and password, such as FTP, it generally will insert a default username and password if they aren’t supplied. For example, if you hand your browser an FTP URL without specifying a username and password, it will insert “anonymous” for your username and send a default password (Internet Explorer sends “IEUser”, while Netscape Navigator sends “mozilla”).

The second example shows a username being specified as “anonymous”. This username, combined with the host component, looks just like an email address. The “@” character separates the user and password components from the rest of the URL.

In the third example, both a username (“anonymous”) and password (“my_passwd”) are specified, separated by the “:” character.

### Paths

The path component of the URL specifies where on the server machine the resource lives. The path often resembles a hierarchical filesystem path. For example:

```http://www.joes-hardware.com:80/seasonal/index-fall.html```

The path in this URL is “/seasonal/index-fall.html”, which resembles a filesystem path on a Unix filesystem. The path is the information that the server needs to locate the resource.* The path component for HTTP URLs can be divided into path segments separated by “/” characters (again, as in a file path on a Unix filesystem). Each path segment can have its own params component.

### Parameters

For many schemes, a simple host and path to the object just aren’t enough. Aside from what port the server is listening to and even whether or not you have access to the resource with a username and password, many protocols require more information to work.

Applications interpreting URLs need these protocol parameters to access the resource. Otherwise, the server on the other side might not service the request or, worse yet, might service it wrong. For example, take a protocol like FTP, which has two modes of transfer, binary and text. You wouldn’t want your binary image transferred in text mode, because the binary image could be scrambled.

To give applications the input parameters they need in order to talk to the server correctly, URLs have a params component. This component is just a list of name/value pairs in the URL, separated from the rest of the URL (and from each other) by “;” characters. They provide applications with any additional information that they need to access the resource. For example:

```ftp://prep.ai.mit.edu/pub/gnu;type=d```

In this example, there is one param, type=d, where the name of the param is “type” and its value is “d”.

As we mentioned earlier, the path component for HTTP URLs can be broken into path segments. Each segment can have its own params. For example:

```http://www.joes-hardware.com/hammers;sale=false/index.html;graphics=true```

In this example there are two path segments, hammers and index.html. The hammers path segment has the param sale, and its value is false. The index.html segment has the param graphics, and its value is true.

### Query Strings

Some resources, such as database services, can be asked questions or queries to narrow down the type of resource being requested.

Let’s say Joe’s Hardware store maintains a list of unsold inventory in a database and allows the inventory to be queried, to see whether products are in stock. The following URL might be used to query a web database gateway to see if item number 12731 is available:

```http://www.joes-hardware.com/inventory-check.cgi?item=12731```

For the most part, this resembles the other URLs we have looked at. What is new is everything to the right of the question mark (?). This is called the query component. The query component of the URL is passed along to a gateway resource, with the path component of the URL identifying the gateway resource. Basically, gateways can be thought of as access points to other applications (we discuss gateways in detail in Chapter 8).

Figure 2-2 shows an example of a query component being passed to a server that is acting as a gateway to Joe’s Hardware’s inventory-checking application. The query is checking whether a particular item, 12731, is in inventory in size large and color blue.

![Figure-2-2](ScreenshotsForNotes/Chapter2/Figure_2_2.PNG)

There is no requirement for the format of the query component, except that some characters are illegal, as we’ll see later in this chapter. By convention, many gateways expect the query string to be formatted as a series of “name=value” pairs, separated by “&” characters:

```http://www.joes-hardware.com/inventory-check.cgi?item=12731&color=blue```

In this example, there are two name/value pairs in the query component: item=12731 and color=blue.

### Fragments

Some resource types, such as HTML, can be divided further than just the resource level. For example, for a single, large text document with sections in it, the URL for the resource would point to the entire text document, but ideally you could specify the sections within the resource.

To allow referencing of parts or fragments of a resource, URLs support a frag component to identify pieces within a resource. For example, a URL could point to a particular image or section within an HTML document.

A fragment dangles off the right-hand side of a URL, preceded by a # character. For example:

```http://www.joes-hardware.com/tools.html#drills```

In this example, the fragment drills references a portion of the /tools.html web page located on the Joe’s Hardware web server. The portion is named “drills”.

Because HTTP servers generally deal only with entire objects,* not with fragments of objects, clients don’t pass fragments along to servers (see Figure 2-3). After your browser gets the entire resource from the server, it then uses the fragment to display the part of the resource in which you are interested.

## URL Shortcuts

Web clients understand and use a few URL shortcuts. Relative URLs are a convenient shorthand for specifying a resource within a resource. Many browsers also support “automatic expansion” of URLs, where the user can type in a key (memorable) part of a URL, and the browser fills in the rest. This is explained in “Expandomatic URLs.”

## Relative URLs

URLs come in two flavors: absolute and relative. So far, we have looked only at absolute URLs. With an absolute URL, you have all the information you need to access a resource.

![Figure-2-3](ScreenshotsForNotes/Chapter2/Figure_2_3.PNG)

On the other hand, relative URLs are incomplete. To get all the information needed to access a resource from a relative URL, you must interpret it relative to another URL, called its base.

Relative URLs are a convenient shorthand notation for URLs. If you have ever written HTML by hand, you have probably found them to be a great shortcut. Example 2-1 contains an example HTML document with an embedded relative URL.

```HTML
<HTML>
<HEAD><TITLE>Joe's Tools</TITLE></HEAD>
<BODY>
<H1> Tools Page </H1>
<H2> Hammers <H2>
<P> Joe's Hardware Online has the largest selection of <A HREF="./hammers.html">hammers
</A> on earth.
</BODY>
</HTML>
```

In Example 2-1, we have an HTML document for the resource:

```http://www.joes-hardware.com/tools.html```

In the HTML document, there is a hyperlink containing the URL ./hammers.html. This URL seems incomplete, but it is a legal relative URL. It can be interpreted relative to the URL of the document in which it is found; in this case, relative to the resource /tools.html on the Joe’s Hardware web server.

The abbreviated relative URL syntax lets HTML authors omit from URLs the scheme, host, and other components. These components can be inferred by the base URL of the resource they are in. URLs for other resources also can be specified in this shorthand.

In Example 2-1, our base URL is:

```http://www.joes-hardware.com/tools.html```

Using this URL as a base, we can infer the missing information. We know the resource is ./hammers.html, but we don’t know the scheme or host. Using the base URL, we can infer that the scheme is http and the host is www.joes-hardware.com. Figure 2-4 illustrates this.

![Figure-2-4](ScreenshotsForNotes/Chapter2/Figure_2_4.PNG)

Relative URLs are only fragments or pieces of URLs. Applications that process URLs (such as your browser) need to be able to convert between relative and absolute URLs.

It is also worth noting that relative URLs provide a convenient way to keep a set of resources (such as HTML pages) portable. If you use relative URLs, you can move a set of documents around and still have their links work, because they will be interpreted relative to the new base. This allows for things like mirroring content on other servers.

### Base URLs

The first step in the conversion process is to find a base URL. The base URL serves as a point of reference for the relative URL. It can come from a few places:

* Explicitly provided in the resource
    * Some resources explicitly specify the base URL. An HTML document, for example, may include a <BASE> HTML tag defining the base URL by which to convert all relative URLs in that HTML document.
* Base URL of the encapsulating resource
    * If a relative URL is found in a resource that does not explicitly specify a base URL, as in Example 2-1, it can use the URL of the resource in which it is embedded as a base (as we did in our example).
* No base URL
    * In some instances, there is no base URL. This often means that you have an absolute URL; however, sometimes you may just have an incomplete or broken URL.

### Resolving relative references

Previously, we showed the basic components and syntax of URLs. The next step in converting a relative URL into an absolute one is to break up both the relative and base URLs into their component pieces.

In effect, you are just parsing the URL, but this is often called decomposing the URL, because you are breaking it up into its components. Once you have broken the base and relative URLs into their components, you can then apply the algorithm pictured in Figure 2-5 to finish the conversion.

![Figure-2-5](ScreenshotsForNotes/Chapter2/Figure_2_5.PNG)

This algorithm converts a relative URL to its absolute form, which can then be used to reference the resource. This algorithm was originally specified in RFC 1808 and later incorporated into RFC 2396.

With our ./hammers.html example from Example 2-1, we can apply the algorithm depicted in Figure 2-5:

1. Path is ./hammers.html; base URL is http://www.joes-hardware.com/tools.html.
2. Scheme is empty; proceed down left half of chart and inherit the base URL scheme (HTTP).
3. At least one component is non-empty; proceed to bottom, inheriting host and port components.
4. Combining the components we have from the relative URL (path: ./hammers.html) with what we have inherited (scheme: http, host: www.joes-hardware.com, port: 80), we get our new absolute URL: http://www.joes-hardware.com/hammers.html.

## Expandomatic URLs

Some browsers try to expand URLs automatically, either after you submit the URL or while you’re typing. This provides users with a shortcut: they don’t have to type in the complete URL, because it automatically expands itself.

These “expandomatic” features come in two flavors:

* *Hostname expansion*
    * In hostname expansion, the browser can often expand the hostname you type in into the full hostname without your help, just by using some simple heuristics. For example if you type “yahoo” in the address box, your browser can automatically insert “www.” and “.com” onto the hostname, creating “www.yahoo.com”. Some browsers will try this if they are unable to find a site that matches “yahoo”, trying a few expansions before giving up. Browsers apply these simple tricks to save you some time and frustration. However, these expansion tricks on hostnames can cause problems for other HTTP applications, such as proxies. In Chapter 6, we will discuss these problems in more detail.
* *History expansion*
    * Another technique that browsers use to save you time typing URLs is to store a history of the URLs that you have visited in the past. As you type in the URL, they can offer you completed choices to select from by matching what you type to the prefixes of the URLs in your history. So, if you were typing in the start of a URL that you had visited previously, such as http://www.joes-, your browser could suggest http://www.joes-hardware.com. You could then select that instead of typing out the complete URL.

Be aware that URL auto-expansion may behave differently when used with proxies.

## Shady Characters

URLs were designed to be portable. They were also designed to uniformly name all the resources on the Internet, which means that they will be transmitted through various protocols. Because all of these protocols have different mechanisms for transmitting their data, it was important for URLs to be designed so that they could be transmitted safely through any Internet protocol.

Safe transmission means that URLs can be transmitted without the risk of losing information. Some protocols, such as the Simple Mail Transfer Protocol (SMTP) for electronic mail, use transmission methods that can strip off certain characters.* To get around this, URLs are permitted to contain only characters from a relatively small, universally safe alphabet.

In addition to wanting URLs to be transportable by all Internet protocols, designers wanted them to be readable by people. So invisible, nonprinting characters also are prohibited in URLs, even though these characters may pass through mailers and otherwise be portable.

To complicate matters further, URLs also need to be complete. URL designers realized there would be times when people would want URLs to contain binary data or characters outside of the universally safe alphabet. So, an escape mechanism was added, allowing unsafe characters to be encoded into safe characters for transport. This section summarizes the universal alphabet and encoding rules for URLs.

## The URL Character Set

Default computer system character sets often have an Anglocentric bias. Historically, many computer applications have used the US-ASCII character set. US-ASCII uses 7 bits to represent most keys available on an English typewriter and a few nonprinting control characters for text formatting and hardware signalling.

US-ASCII is very portable, due to its long legacy. But while it’s convenient to citizens of the U.S., it doesn’t support the inflected characters common in European languages or the hundreds of non-Romanic languages read by billions of people around the world.

Furthermore, some URLs may need to contain arbitrary binary data. Recognizing the need for completeness, the URL designers have incorporated escape sequences. Escape sequences allow the encoding of arbitrary character values or data using a restricted subset of the US-ASCII character set, yielding portability and completeness.

## Encoding Mechanisms

To get around the limitations of a safe character set representation, an encoding scheme was devised to represent characters in a URL that are not safe. The encoding simply represents the unsafe character by an “escape” notation, consisting of a percent sign (%) followed by two hexadecimal digits that represent the ASCII code of the character.

Table 2-2 shows a few examples.

![Table-2-2](ScreenshotsForNotes/Chapter2/Table_2_2.PNG)

## Character Restrictions

Several characters have been reserved to have special meaning inside of a URL. Others are not in the defined US-ASCII printable set. And still others are known to confuse some Internet gateways and protocols, so their use is discouraged.

Table 2-3 lists characters that should be encoded in a URL before you use them for anything other than their reserved purposes.

![Table-2-3-1](ScreenshotsForNotes/Chapter2/Table_2_3_1.PNG) ![Table-2-3-2](ScreenshotsForNotes/Chapter2/Table_2_3_2.PNG)

## A Bit More

You might be wondering why nothing bad has happened when you have used characters that are unsafe. For instance, you can visit Joe’s home page at:

```http://www.joes-hardware.com/~joe```

and not encode the “~” character. For some transport protocols this is not an issue, but it is still unwise for application developers not to encode unsafe characters.

Applications need to walk a fine line. It is best for client applications to convert any unsafe or restricted characters before sending any URL to any other application.* Once all the unsafe characters have been encoded, the URL is in a canonical form that can be shared between applications; there is no need to worry about the other application getting confused by any of the characters’ special meanings.

The original application that gets the URL from the user is best fit to determine which characters need to be encoded. Because each component of the URL may have its own safe/unsafe characters, and which characters are safe/unsafe is schemedependent, only the application receiving the URL from the user really is in a position to determine what needs to be encoded.

Of course, the other extreme is for the application to encode all characters. While this is not recommended, there is no hard and fast rule against encoding characters that are considered safe already; however, in practice this can lead to odd and broken behavior, because some applications may assume that safe characters will not be encoded.

Sometimes, malicious folks encode extra characters in an attempt to get around applications that are doing pattern matching on URLs—for example, web filtering applications. Encoding safe URL components can cause pattern-matching applications to fail to recognize the patterns for which they are searching. In general, applications interpreting URLs must decode the URLs before processing them.

Some URL components, such as the scheme, need to be recognized readily and are required to start with an alphabetic character. Refer back to “URL Syntax” for more guidelines on the use of reserved and unsafe characters within different URL components

## A Sea of Schemes

In this section, we’ll take a look at the more common scheme formats on the Web. Appendix A gives a fairly exhaustive list of schemes and references to their individual documentation.

Table 2-4 summarizes some of the most popular schemes. Reviewing “URL Syntax” will make the syntax portion of the table a little more familiar.

![Table-2-4-1](ScreenshotsForNotes/Chapter2/Table_2_4.PNG) ![Table-2-4-2](ScreenshotsForNotes/Chapter2/Table_2_4_2.PNG) ![Table-2-4-3](ScreenshotsForNotes/Chapter2/Table_2_4_3.PNG)

## The Future URLs are a powerful tool. Their design allows them to name all existing objects and easily encompass new formats. They provide a uniform naming mechanism that can be shared between Internet protocols.

However, they are not perfect. URLs are really addresses, not true names. This means that a URL tells you where something is located, for the moment. It provides you with the name of a specific server on a specific port, where you can find the resource. The downfall of this scheme is that if the resource is moved, the URL is no longer valid. And at that point, it provides no way to locate the object.

What would be ideal is if you had the real name of an object, which you could use to look up that object regardless of its location. As with a person, given the name of the resource and a few other facts, you could track down that resource, regardless of where it moved.

The Internet Engineering Task Force (IETF) has been working on a new standard, uniform resource names (URNs), for some time now, to address just this issue. URNs provide a stable name for an object, regardless of where that object moves (either inside a web server or across web servers).

Persistent uniform resource locators (PURLs) are an example of how URN functionality can be achieved using URLs. The concept is to introduce another level of indirection in looking up a resource, using an intermediary resource locator server that catalogues and tracks the actual URL of a resource. A client can request a persistent URL from the locator, which can then respond with a resource that redirects the client to the actual and current URL for the resource (see Figure 2-6). For more information on PURLs, visit http://purl.oclc.org.

### If Not Now, When?

The ideas behind URNs have been around for some time. Indeed, if you look at the publication dates for some of their specifications, you might ask yourself why they have yet to be adopted.

![Figure-2-6](ScreenshotsForNotes/Chapter2/Figure_2_6.PNG)

The change from URLs to URNs is an enormous task. Standardization is a slow process, often for good reason. Support for URNs will require many changes—consensus from the standards bodies, modifications to various HTTP applications, etc. A tremendous amount of critical mass is required to make such changes, and unfortunately (or perhaps fortunately), there is so much momentum behind URLs that it will be some time before all the stars align to make such a conversion possible.

Throughout the explosive growth of the Web, Internet users—everyone from computer scientists to the average Internet user—have been taught to use URLs. While they suffer from clumsy syntax (for the novice) and persistence problems, people have learned how to use them and how to deal with their drawbacks. URLs have some limitations, but they’re not the web development community’s most pressing problem.

Currently, and for the foreseeable future, URLs are the way to name resources on the Internet. They are everywhere, and they have proven to be a very important part of the Web’s success. It will be a while before any other naming scheme unseats URLs. However, URLs do have their limitations, and it is likely that new standards (possibly URNs) will emerge and be deployed to address some of these limitations

# 3. HTTP Messages

## The flow of messages

HTTP messages are the blocks of data sent between HTTP applications. These blocks of data begin with some text meta-information describing the message contents and meaning, followed by optional data. These messages flow between clients, servers, and proxies. The terms “inbound,” “outbound,” “upstream,” and “downstream” describe message direction.

### Messages commute inbound to the origin server

HTTP uses the terms inbound and outbound to describe transactional direction. Messages travel inbound to the origin server, and when their work is done, they travel outbound back to the user agent (see Figure 3-1).

![Figure-3-1](ScreenshotsForNotes/Chapter3/Figure_3_1.PNG)

### Messages flow downstream

HTTP messages flow like rivers. All messages flow downstream, regardless of whether they are request messages or response messages (see Figure 3-2). The sender of any message is upstream of the receiver. In Figure 3-2, proxy 1 is upstream of proxy 3 for the request but downstream of proxy 3 for the response

![Figure-3-2](ScreenshotsForNotes/Chapter3/Figure_3_2.PNG)

## The parts of a message

HTTP messages are simple, formatted blocks of data. Take a peek at Figure 3-3 for an example. Each message contains either a request from a client or a response from a server. They consist of three parts: a start line describing the message, a block of headers containing attributes, and an optional body containing data.

The start line and headers are just ASCII text, broken up by lines. Each line ends with a two-character end-of-line sequence, consisting of a carriage return (ASCII 13) and a line-feed character (ASCII 10). This end-of-line sequence is written “CRLF.” It is worth pointing out that while the HTTP specification for terminating lines is CRLF, robust applications also should accept just a line-feed character. Some older or broken HTTP applications do not always send both the carriage return and line feed.

The entity body or message body (or just plain “body”) is simply an optional chunk of data. Unlike the start line and headers, the body can contain text or binary data or can be empty.

In the example in Figure 3-3, the headers give you a bit of information about the body. The Content-Type line tells you what the body is—in this example, it is a plain-text document. The Content-Length line tells you how big the body is; here it is a meager 19 bytes.

![Figure-3-3](ScreenshotsForNotes/Chapter3/Figure_3_3.PNG)

### Message syntax

All HTTP messages fall into two types: request messages and response messages. Request messages request an action from a web server. Response messages carry results of a request back to a client. Both request and response messages have the same basic message structure. Figure 3-4 shows request and response messages to get a GIF image.

Here’s the format for a request message:

```
<method> <request-URL> <version>
<headers>

<entity-body>
```

![Figure-3-4](ScreenshotsForNotes/Chapter3/Figure_3_4.PNG)

Here’s the format for a response message (note that the syntax differs only in the start line):

```
<version> <status> <reason-phrase>
<headers>

<entity-body>
```

Here’s a quick description of the various parts:

* ```method```
    * The action that the client wants the server to perform on the resource. It is a single word, like “GET,” “HEAD,” or “POST”. We cover the method in detail later in this chapter.
* ```request-URL```
    * A complete URL naming the requested resource, or the path component of the URL. If you are talking directly to the server, the path component of the URL is usually okay as long as it is the absolute path to the resource—the server can assume itself as the host/port of the URL. Chapter 2 covers URL syntax in detail.
* ```version```
    * The version of HTTP that the message is using. Its format looks like: HTTP/<major>.<minor> where major and minor both are integers. We discuss HTTP versioning a bit more later in this chapter.
* ```status-code```
    * A three-digit number describing what happened during the request. The first digit of each code describes the general class of status (“success,” “error,” etc.). An exhaustive list of status codes defined in the HTTP specification and their meanings is provided later in this chapter.
* ```reason-phrase```
    * A human-readable version of the numeric status code, consisting of all the text until the end-of-line sequence. Example reason phrases for all the status codes defined in the HTTP specification are provided later in this chapter. The reason phrase is meant solely for human consumption, so, for example, response lines containing “HTTP/1.0 200 NOT OK” and “HTTP/1.0 200 OK” should be treated as equivalent success indications, despite the reason phrases suggesting otherwise.
* ```headers```
    * Zero or more headers, each of which is a name, followed by a colon (:), followed by optional whitespace, followed by a value, followed by a CRLF. The headers are terminated by a blank line (CRLF), marking the end of the list of headers and the beginning of the entity body. Some versions of HTTP, such as HTTP/1.1, require certain headers to be present for the request or response message to be valid. The various HTTP headers are covered later in this chapter.
* ```entity-body```
    * The entity body contains a block of arbitrary data. Not all messages contain entity bodies, so sometimes a message terminates with a bare CRLF. We discuss entities in detail in Chapter 15.

Figure 3-5 demonstrates hypothetical request and response messages.

![Figure-3-5](ScreenshotsForNotes/Chapter3/Figure_3_5.PNG)

Note that a set of HTTP headers should always end in a blank line (bare CRLF), even if there are no headers and even if there is no entity body. Historically, however, many clients and servers (mistakenly) omitted the final CRLF if there was no entity body. To interoperate with these popular but noncompliant implementations, clients and servers should accept messages that end without the final CRLF.

## Start Lines

All HTTP messages begin with a start line. The start line for a request message says what to do. The start line for a response message says what happened.

### Request Line

Request messages ask servers to do something to a resource. The start line for a request message, or request line, contains a method describing what operation the server should perform and a request URL describing the resource on which to perform the method. The request line also includes an HTTP version which tells the server what dialect of HTTP the client is speaking.

All of these fields are separated by whitespace. In Figure 3-5a, the request method is GET, the request URL is /test/hi-there.txt, and the version is HTTP/1.1. Prior to HTTP/1.0, request lines were not required to contain an HTTP version.

### Response Line

Response messages carry status information and any resulting data from an operation back to a client. The start line for a response message, or response line, contains the HTTP version that the response message is using, a numeric status code, and a textual reason phrase describing the status of the operation.

All these fields are separated by whitespace. In Figure 3-5b, the HTTP version is HTTP/1.0, the status code is 200 (indicating success), and the reason phrase is OK, meaning the document was returned successfully. Prior to HTTP/1.0, responses were not required to contain a response line.

### Methods

The method begins the start line of requests, telling the server what to do. For example, in the line “GET /specials/saw-blade.gif HTTP/1.0,” the method is GET.

The HTTP specifications have defined a set of common request methods. For example, the GET method gets a document from a server, the POST method sends data to a server for processing, and the OPTIONS method determines the general capabilities of a web server or the capabilities of a web server for a specific resource.

Table 3-1 describes seven of these methods. Note that some methods have a body in the request message, and other methods have bodyless requests.

![Table-3-1](ScreenshotsForNotes/Chapter3/Table_3_1.PNG)

Not all servers implement all seven of the methods in Table 3-1. Furthermore, because HTTP was designed to be easily extensible, other servers may implement their own request methods in addition to these. These additional methods are called extension methods, because they extend the HTTP specification.

### Status Codes

As methods tell the server what to do, status codes tell the client what happened. Status codes live in the start lines of responses. For example, in the line “HTTP/1.0 200 OK,” the status code is 200.

When clients send request messages to an HTTP server, many things can happen. If you are fortunate, the request will complete successfully. You might not always be so lucky. The server may tell you that the resource you requested could not be found, that you don’t have permission to access the resource, or perhaps that the resource has moved someplace else.

Status codes are returned in the start line of each response message. Both a numeric and a human-readable status are returned. The numeric code makes error processing easy for programs, while the reason phrase is easily understood by humans.

The different status codes are grouped into classes by their three-digit numeric codes. Status codes between 200 and 299 represent success. Codes between 300 and 399 indicate that the resource has been moved. Codes between 400 and 499 mean that the client did something wrong in the request. Codes between 500 and 599 mean something went awry on the server.

The status code classes are shown in Table 3-2.

![Table-3-2](ScreenshotsForNotes/Chapter3/Table_3_2.PNG)

Current versions of HTTP define only a few codes for each status category. As the protocol evolves, more status codes will be defined officially in the HTTP specification. If you receive a status code that you don’t recognize, chances are someone has defined it as an extension to the current protocol. You should treat it as a general member of the class whose range it falls into.

For example, if you receive status code 515 (which is outside of the defined range for 5XX codes listed in Table 3-2), you should treat the response as indicating a server error, which is the general class of 5XX messages.

Table 3-3 lists some of the most common status codes that you will see. We will explain all the current HTTP status codes in detail later in this chapter.

![Table-3-3](ScreenshotsForNotes/Chapter3/Table_3_3.PNG)

### Reasons phrases

The reason phrase is the last component of the start line of the response. It provides a textual explanation of the status code. For example, in the line “HTTP/1.0 200 OK,” the reason phrase is OK.

Reason phrases are paired one-to-one with status codes. The reason phrase provides a human-readable version of the status code that application developers can pass along to their users to indicate what happened during the request.

The HTTP specification does not provide any hard and fast rules for what reason phrases should look like. Later in this chapter, we list the status codes and some suggested reason phrases.

### Version numbers

Version numbers appear in both request and response message start lines in the format HTTP/x.y. They provide a means for HTTP applications to tell each other what version of the protocol they conform to.

Version numbers are intended to provide applications speaking HTTP with a clue about each other’s capabilities and the format of the message. An HTTP Version 1.2 application communicating with an HTTP Version 1.1 application should know that it should not use any new 1.2features, as they likely are not implemented by the application speaking the older version of the protocol.

The version number indicates the highest version of HTTP that an application supports. In some cases this leads to confusion between applications,* because HTTP/1.0 applications interpret a response with HTTP/1.1 in it to indicate that the response is a 1.1 response, when in fact that’s just the level of protocol used by the responding application.

Note that version numbers are not treated as fractional numbers. Each number in the version (for example, the “1” and “0” in HTTP/1.0) is treated as a separate number. So, when comparing HTTP versions, each number must be compared separately in order to determine which is the higher version. For example, HTTP/2.22 is a higher version than HTTP/2.3, because 22 is a larger number than 3.

## Headers

The previous section focused on the first line of request and response messages (methods, status codes, reason phrases, and version numbers). Following the start line comes a list of zero, one, or many HTTP header fields (see Figure 3-5).

HTTP header fields add additional information to request and response messages. They are basically just lists of name/value pairs. For example, the following header line assigns the value 19 to the Content-Length header field:

```
Content-length: 19
```

### Header classifications

The HTTP specification defines several header fields. Applications also are free to invent their own home-brewed headers. HTTP headers are classified into:

* *General headers*

    * Can appear in both request and response messages

* *Request headers*

    * Provide more information about the request

* *Response headers*

    * Provide more information about the response

* *Entity headers*

    * Describe body size and contents, or the resource itself

* *Extension headers*

    * New headers that are not defined in the specification      Each HTTP header has a simple syntax: a name, followed by a colon (:), followed by optional whitespace, followed by the field value, followed by a CRLF. Table 3-4 lists some common header examples.

![Table-3-4](ScreenshotsForNotes/Chapter3/Table_3_4.PNG)

### Header Continuation Lines

Long header lines can be made more readable by breaking them into multiple lines, preceding each extra line with at least one space or tab character.

For example:

```
HTTP/1.0 200 OK
Content-Type: image/gif
Content-Length: 8572
Server: Test Server
    Version 1.0
```

In this example, the response message contains a Server header whose value is broken into continuation lines. The complete value of the header is “Test Server Version 1.0”.

We’ll briefly describe all the HTTP headers later in this chapter. We also provide a more detailed reference summary of all the headers in Appendix C.

## Entity Bodies

The third part of an HTTP message is the optional entity body. Entity bodies are the payload of HTTP messages. They are the things that HTTP was designed to transport.

HTTP messages can carry many kinds of digital data: images, video, HTML documents, software applications, credit card transactions, electronic mail, and so on.

### Version 0.9 messages

HTTP Version 0.9 was an early version of the HTTP protocol. It was the starting point for the request and response messages that HTTP has today, but with a far simpler protocol (see Figure 3-6).

![Figure-3-6](ScreenshotsForNotes/Chapter3/Figure_3_6.PNG)

HTTP/0.9 messages also consisted of requests and responses, but the request contained merely the method and the request URL, and the response contained only the entity. No version information (it was the first and only version at the time), no status code or reason phrase, and no headers were included.

However, this simplicity did not allow for much flexibility or the implementation of most of the HTTP features and applications described in this book. We briefly describe it here because there are still clients, servers, and other applications that use it, and application writers should be aware of its limitations.

## Methods

Let’s talk in more detail about some of the basic HTTP methods, listed earlier in Table 3-1. Note that not all methods are implemented by every server. To be compliant with HTTP Version 1.1, a server need implement only the GET and HEAD methods for its resources.

Even when servers do implement all of these methods, the methods most likely have restricted uses. For example, servers that support DELETE or PUT (described later in this section) would not want just anyone to be able to delete or store resources. These restrictions generally are set up in the server’s configuration, so they vary from site to site and from server to server.

### Safe Methods

HTTP defines a set of methods that are called safe methods. The GET and HEAD methods are said to be safe, meaning that no action should occur as a result of an HTTP request that uses either the GET or HEAD method.

By no action, we mean that nothing will happen on the server as a result of the HTTP request. For example, consider when you are shopping online at Joe’s Hardware and you click on the “submit purchase” button. Clicking on the button submits a POST request (discussed later) with your credit card information, and an action is performed on the server on your behalf. In this case, the action is your credit card being charged for your purchase.

There is no guarantee that a safe method won’t cause an action to be performed (in practice, that is up to the web developers). Safe methods are meant to allow HTTP application developers to let users know when an unsafe method that may cause some action to be performed is being used. In our Joe’s Hardware example, your web browser may pop up a warning message letting you know that you are making a request with an unsafe method and that, as a result, something might happen on the server (e.g., your credit card being charged).

### GET

GET is the most common method. It usually is used to ask a server to send a resource. HTTP/1.1 requires servers to implement this method. Figure 3-7 shows an example of a client making an HTTP request with the GET method.

![Figure-3-7](ScreenshotsForNotes/Chapter3/Figure_3_7.PNG)

### HEAD

The HEAD method behaves exactly like the GET method, but the server returns only the headers in the response. No entity body is ever returned. This allows a client to inspect the headers for a resource without having to actually get the resource. Using HEAD, you can:

* Find out about a resource (e.g., determine its type) without getting it.

* See if an object exists, by looking at the status code of the response.

* Test if the resource has been modified, by looking at the headers.

Server developers must ensure that the headers returned are exactly those that a GET request would return. The HEAD method also is required for HTTP/1.1 compliance. Figure 3-8 shows the HEAD method in action.

![Figure-3-8](ScreenshotsForNotes/Chapter3/Figure_3_8.PNG)

### PUT

The PUT method writes documents to a server, in the inverse of the way that GET reads documents from a server. Some publishing systems let you create web pages and install them directly on a web server using PUT (see Figure 3-9).

![Figure-3-9](ScreenshotsForNotes/Chapter3/Figure_3_9.PNG)

The semantics of the PUT method are for the server to take the body of the request and either use it to create a new document named by the requested URL or, if that URL already exists, use the body to replace it.

Because PUT allows you to change content, many web servers require you to log in with a password before you can perform a PUT. You can read more about password authentication in Chapter 12.

### POST

The POST method was designed to send input data to the server.* In practice, it is often used to support HTML forms. The data from a filled-in form typically is sent to the server, which then marshals it off to where it needs to go (e.g., to a server gateway program, which then processes it). Figure 3-10 shows a client making an HTTP request—sending form data to a server—with the POST method.

***POST is used to send data to a server. PUT is used to deposit data into a resource on the server (e.g., a file).***

### TRACE

When a client makes a request, that request may have to travel through firewalls, proxies, gateways, or other applications. Each of these has the opportunity to modify the original HTTP request. The TRACE method allows clients to see how its request looks when it finally makes it to the server.

A TRACE request initiates a “loopback” diagnostic at the destination server. The server at the final leg of the trip bounces back a TRACE response, with the virgin request message it received in the body of its response. A client can then see how, or if, its original message was munged or modified along the request/response chain of any intervening HTTP applications (see Figure 3-11).

![Figure-3-10](ScreenshotsForNotes/Chapter3/Figure_3_10.PNG)

The TRACE method is used primarily for diagnostics; i.e., verifying that requests are going through the request/response chain as intended. It’s also a good tool for seeing the effects of proxies and other applications on your requests.

As good as TRACE is for diagnostics, it does have the drawback of assuming that intervening applications will treat different types of requests (different methods— GET, HEAD, POST, etc.) the same. Many HTTP applications do different things depending on the method—for example, a proxy might pass a POST request directly to the server but attempt to send a GET request to another HTTP application (such as a web cache). TRACE does not provide a mechanism to distinguish methods. Generally, intervening applications make the call as to how they process a TRACE request.

![Figure-3-11](ScreenshotsForNotes/Chapter3/Figure_3_11.PNG)

No entity body can be sent with a TRACE request. The entity body of the TRACE response contains, verbatim, the request that the responding server received.

### OPTIONS

The OPTIONS method asks the server to tell us about the various supported capabilities of the web server. You can ask a server about what methods it supports in general or for particular resources. (Some servers may support particular operations only on particular kinds of objects).

This provides a means for client applications to determine how best to access various resources without actually having to access them. Figure 3-12shows a request scenario using the OPTIONS method.

![Figure-3-12](ScreenshotsForNotes/Chapter3/Figure_3_12.PNG)

### DELETE

The DELETE method does just what you would think—it asks the server to delete the resources specified by the request URL. However, the client application is not guaranteed that the delete is carried out. This is because the HTTP specification allows the server to override the request without telling the client. Figure 3-13 shows an example of the DELETE method.

![Figure-3-13](ScreenshotsForNotes/Chapter3/Figure_3_13.PNG)0

### Extension Methods

HTTP was designed to be field-extensible, so new features wouldn’t cause older software to fail. Extension methods are methods that are not defined in the HTTP/1.1 specification. They provide developers with a means of extending the capabilities of the HTTP services their servers implement on the resources that the servers manage. Some common examples of extension methods are listed in Table 3-5. These methods are all part of the WebDAV HTTP extension (see Chapter 19) that helps support publishing of web content to web servers over HTTP.

![Table-3-5](ScreenshotsForNotes/Chapter3/Table_3_5.PNG)

It’s important to note that not all extension methods are defined in a formal specification. If you define an extension method, it’s likely not to be understood by most HTTP applications. Likewise, it’s possible that your HTTP applications could run into extension methods being used by other applications that it does not understand.

In these cases, it is best to be tolerant of extension methods. Proxies should try to relay messages with unknown methods through to downstream servers if they are capable of doing that without breaking end-to-end behavior. Otherwise, they should respond with a 501 Not Implemented status code. Dealing with extension methods (and HTTP extensions in general) is best done with the old rule, “be conservative in what you send, be liberal in what you accept.”

## Status Codes

HTTP status codes are classified into five broad categories, as shown earlier in Table 3-2. This section summarizes the HTTP status codes for each of the five classes.

The status codes provide an easy way for clients to understand the results of their transactions. In this section, we also list example reason phrases, though there is no real guidance on the exact text for reason phrases. We include the recommended reason phrases from the HTTP/1.1 specification.

### 100-199: Informational Status Codes

HTTP/1.1 introduced the informational status codes to the protocol. They are relatively new and subject to a bit of controversy about their complexity and perceived value. Table 3-6 lists the defined informational status codes.

![Table-3-6](ScreenshotsForNotes/Chapter3/Table_3_6.PNG)

The 100 Continue status code, in particular, is a bit confusing. It’s intended to optimize the case where an HTTP client application has an entity body to send to a server but wants to check that the server will accept the entity before it sends it. We discuss it here in a bit more detail (how it interacts with clients, servers, and proxies) because it tends to confuse HTTP programmers.

#### Clients and 100 Continue

If a client is sending an entity to a server and is willing to wait for a 100 Continue response before it sends the entity, the client needs to send an Expect request header (see Appendix C) with the value 100-continue. If the client is not sending an entity, it shouldn’t send a 100-continue Expect header, because this will only confuse the server into thinking that the client might be sending an entity.

100-continue, in many ways, is an optimization. A client application should really use 100-continue only to avoid sending a server a large entity that the server will not be able to handle or use.

Because of the initial confusion around the 100 Continue status (and given some of the older implementations out there), clients that send an Expect header for 100- continue should not wait forever for the server to send a 100 Continue response. After some timeout, the client should just send the entity.

In practice, client implementors also should be prepared to deal with unexpected 100 Continue responses (annoying, but true). Some errant HTTP applications send this code inappropriately.

#### Servers and 100 Continue

If a server receives a request with the Expect header and 100-continue value, it should respond with either the 100 Continue response or an error code (see Table 3-9). Servers should never send a 100 Continue status code to clients that do not send the 100- continue expectation. However, as we noted above, some errant servers do this.

If for some reason the server receives some (or all) of the entity before it has had a chance to send a 100 Continue response, it does not need to send this status code, because the client already has decided to continue. When the server is done reading the request, however, it still needs to send a final status code for the request (it can just skip the 100 Continue status).

Finally, if a server receives a request with a 100-continue expectation and it decides to end the request before it has read the entity body (e.g., because an error has occurred), it should not just send a response and close the connection, as this can prevent the client from receiving the response (see “TCP close and reset errors” in Chapter 4).

#### Proxies and 100 Continue

A proxy that receives from a client a request that contains the 100-continue expectation needs to do a few things. If the proxy either knows that the next-hop server (discussed in Chapter 6) is HTTP/1.1-compliant or does not know what version the next-hop server is compliant with, it should forward the request with the Expect header in it. If it knows that the next-hop server is compliant with a version of HTTP earlier than 1.1, it should respond with the 417 Expectation Failed error.

If a proxy decides to include an Expect header and 100-continue value in its request on behalf of a client that is compliant with HTTP/1.0 or earlier, it should not forward the 100 Continue response (if it receives one from the server) to the client, because the client won’t know what to make of it.

It can pay for proxies to maintain some state about next-hop servers and the versions of HTTP they support (at least for servers that have received recent requests), so they can better handle requests received with a 100-continue expectation.

### 200–299: Success Status Codes

When clients make requests, the requests usually are successful. Servers have an array of status codes to indicate success, matched up with different types of requests. Table 3-7 lists the defined success status codes.

![Table-3-7](ScreenshotsForNotes/Chapter3/Table_3_7.PNG)

### 300–399: Redirection Status Codes

The redirection status codes either tell clients to use alternate locations for the resources they’re interested in or provide an alternate response instead of the content. If a resource has moved, a redirection status code and an optional Location header can be sent to tell the client that the resource has moved and where it can now be found (see Figure 3-14). This allows browsers to go to the new location transparently, without bothering their human users.

![Figure-3-14](ScreenshotsForNotes/Chapter3/Figure_3_14.PNG)

Some of the redirection status codes can be used to validate an application’s local copy of a resource with the origin server. For example, an HTTP application can check if the local copy of its resource is still up-to-date or if the resource has been modified on the origin server. Figure 3-15 shows an example of this. The client sends a special If-Modified-Since header saying to get the document only if it has been modified since October 1997. The document has not changed since this date, so the server replies with a 304 status code instead of the contents.

![Figure-3-15](ScreenshotsForNotes/Chapter3/Figure_3_15.PNG)

In general, it’s good practice for responses to non-HEAD requests that include a redirection status code to include an entity with a description and links to the redirected URL(s)—see the first response message in Figure 3-14. Table 3-8 lists the defined redirection status codes.

![Table-3-8](ScreenshotsForNotes/Chapter3/Table_3_8_1.PNG) ![Table-3-8](ScreenshotsForNotes/Chapter3/Table_3_8_2.PNG)

From Table 3-8, you may have noticed a bit of overlap between the 302, 303, and 307 status codes. There is some nuance to how these status codes are used, most of which stems from differences in the ways that HTTP/1.0 and HTTP/1.1 applications treat these status codes.

When an HTTP/1.0 client makes a POST request and receives a 302redirect status code in response, it will follow the redirect URL in the Location header with a GET request to that URL (instead of making a POST request, as it did in the original request).

HTTP/1.0 servers expect HTTP/1.0 clients to do this—when an HTTP/1.0 server sends a 302status code after receiving a POST request from an HTTP/1.0 client, the server expects that client to follow the redirect with a GET request to the redirected URL.

The confusion comes in with HTTP/1.1. The HTTP/1.1 specification uses the 303 status code to get this same behavior (servers send the 303 status code to redirect a client’s POST request to be followed with a GET request).

To get around the confusion, the HTTP/1.1 specification says to use the 307 status code in place of the 302status code for temporary redirects to HTTP/1.1 clients. Servers can then save the 302 status code for use with HTTP/1.0 clients.

What this all boils down to is that servers need to check a client’s HTTP version to properly select which redirect status code to send in a redirect response.

### 400–499: Client Error Status Codes

Sometimes a client sends something that a server just can’t handle, such as a badly formed request message or, most often, a request for a URL that does not exist.

We’ve all seen the infamous 404 Not Found error code while browsing—this is just the server telling us that we have requested a resource about which it knows nothing.

Many of the client errors are dealt with by your browser, without it ever bothering you. A few, like 404, might still pass through. Table 3-9 shows the various client error status codes.

![Table-3-9](ScreenshotsForNotes/Chapter3/Table_3_9.PNG) ![Table-3-9](ScreenshotsForNotes/Chapter3/Table_3_9_2.PNG)

### 500–599: Server Error Status Codes

Sometimes a client sends a valid request, but the server itself has an error. This could be a client running into a limitation of the server or an error in one of the server’s subcomponents, such as a gateway resource.

Proxies often run into problems when trying to talk to servers on a client’s behalf. Proxies issue 5XX server error status codes to describe the problem (Chapter 6 covers this in detail). Table 3-10 lists the defined server error status codes.

![Table-3-10](ScreenshotsForNotes/Chapter3/Table_3_10_1.PNG) ![Table-3-10](ScreenshotsForNotes/Chapter3/Table_3_10_2.PNG)

## Headers

Headers and methods work together to determine what clients and servers do. This section quickly sketches the purposes of the standard HTTP headers and some headers that are not explicitly defined in the HTTP/1.1 specification (RFC 2616). Appendix C summarizes all these headers in more detail.

There are headers that are specific for each type of message and headers that are more general in purpose, providing information in both request and response messages. Headers fall into five main classes:

* *General headers*

    * These are generic headers used by both clients and servers. They serve general purposes that are useful for clients, servers, and other applications to supply to one another. For example, the Date header is a general-purpose header that allows both sides to indicate the time and date at which the message was constructed: ```Date: Tue, 3 Oct 1974 02:16:00 GMT```

* *Request headers*

    * As the name implies, request headers are specific to request messages. They provide extra information to servers, such as what type of data the client is willing to receive. For example, the following Accept header tells the server that the client will accept any media type that matches its request: ```Accept: */*```

* *Response headers*

    * Response messages have their own set of headers that provide information to the client (e.g., what type of server the client is talking to). For example, the following Server header tells the client that it is talking to a Version 1.0 Tiki-Hut server: ```Server: Tiki-Hut/1.0```

* *Entity headers*

    * Entity headers refer to headers that deal with the entity body. For instance, entity headers can tell the type of the data in the entity body. For example, the following Content-Type header lets the application know that the data is an HTML document in the iso-latin-1 character set: ```Content-Type: text/html; charset=iso-latin-1```

* *Extension headers*

    * Extension headers are nonstandard headers that have been created by application developers but not yet added to the sanctioned HTTP specification. HTTP programs need to tolerate and forward extension headers, even if they don’t know what the headers mean

### General Headers

Some headers provide very basic information about a message. These headers are called general headers. They are the fence straddlers, supplying useful information about a message regardless of its type.

For example, whether you are constructing a request message or a response message, the date and time the message is created means the same thing, so the header that provides this kind of information is general to both types of messages. Table 3-11 lists the general informational headers.

![Table-3-11](ScreenshotsForNotes/Chapter3/Table_3_11.PNG)

#### General caching headers

HTTP/1.0 introduced the first headers that allowed HTTP applications to cache local copies of objects instead of always fetching them directly from the origin server. The latest version of HTTP has a very rich set of cache parameters. In Chapter 7, we cover caching in depth. Table 3-12 lists the basic caching headers.

![Table-3-12](ScreenshotsForNotes/Chapter3/Table_3_12_1.PNG)

### Request Headers

Request headers are headers that make sense only in a request message. They give information about who or what is sending the request, where the request originated, or what the preferences and capabilities of the client are. Servers can use the information the request headers give them about the client to try to give the client a better response. Table 3-13 lists the request informational headers.

![Table-3-13](ScreenshotsForNotes/Chapter3/Table_3_13.PNG)

#### Accept headers

Accept headers give the client a way to tell servers their preferences and capabilities: what they want, what they can use, and, most importantly, what they don’t want. Servers can then use this extra information to make more intelligent decisions about what to send. Accept headers benefit both sides of the connection. Clients get what they want, and servers don’t waste their time and bandwidth sending something the client can’t use. Table 3-14 lists the various accept headers.

![Table-3-14](ScreenshotsForNotes/Chapter3/Table_3_14.PNG)

#### Conditional request headers

Sometimes, clients want to put some restrictions on a request. For instance, if the client already has a copy of a document, it might want to ask a server to send the document only if it is different from the copy the client already has. Using conditional request headers, clients can put such restrictions on requests, requiring the server to make sure that the conditions are true before satisfying the request. Table 3-15 lists the various conditional request headers.

![Table-1-15](ScreenshotsForNotes/Chapter3/Table_3_15.PNG)

#### Request security headers

HTTP natively supports a simple challenge/response authentication scheme for requests. It attempts to make transactions slightly more secure by requiring clients to authenticate themselves before getting access to certain resources. We discuss this challenge/response scheme in Chapter 14, along with other security schemes that have been implemented on top of HTTP. Table 3-16 lists the request security headers.

![Table-3-16](ScreenshotsForNotes/Chapter3/Table_3_16.PNG)

#### Proxy request headers

As proxies become increasingly common on the Internet, a few headers have been defined to help them function better. In Chapter 6, we discuss these headers in detail. Table 3-17 lists the proxy request headers.

![Table-3-17](ScreenshotsForNotes/Chapter3/Table_3_17.PNG)

### Response Headers

Response messages have their own set of response headers. Response headers provide clients with extra information, such as who is sending the response, the capabilities of the responder, or even special instructions regarding the response. These headers help the client deal with the response and make better requests in the future. Table 3-18 lists the response informational headers.

![Table-3-18](ScreenshotsForNotes/Chapter3/Table_3_18.PNG)

#### Negotiation headers

HTTP/1.1 provides servers and clients with the ability to negotiate for a resource if multiple representations are available—for instance, when there are both French and German translations of an HTML document on a server. Chapter 17 walks through negotiation in detail. Here are a few headers servers use to convey information about resources that are negotiable. Table 3-19 lists the negotiation headers.

![Table-3-19](ScreenshotsForNotes/Chapter3/Table_3_19.PNG)

#### Response security headers

You’ve already seen the request security headers, which are basically the response side of HTTP’s challenge/response authentication scheme. We talk about security in detail in Chapter 14. For now, here are the basic challenge headers. Table 3-20 lists the response security headers.

![Table-3-20](ScreenshotsForNotes/Chapter3/Table_3_20.PNG)

### Entity headers

There are many headers to describe the payload of HTTP messages. Because both request and response messages can contain entities, these headers can appear in either type of message.

Entity headers provide a broad range of information about the entity and its content, from information about the type of the object to valid request methods that can be made on the resource. In general, entity headers tell the receiver of the message what it’s dealing with. Table 3-21 lists the entity informational headers.

![Table-3-21](ScreenshotsForNotes/Chapter3/Table_3_21.PNG)

#### Content headers

The content headers provide specific information about the content of the entity, revealing its type, size, and other information useful for processing it. For instance, a web browser can look at the content type returned and know how to display the object. Table 3-22 lists the various content headers.

![Table-3-22](ScreenshotsForNotes/Chapter3/Table_3_22_1.PNG) ![Table-3-22](ScreenshotsForNotes/Chapter3/Table_3_22_2.PNG)

#### Entity caching headers

The general caching headers provide directives about how or when to cache. The entity caching headers provide information about the entity being cached—for example, information needed to validate whether a cached copy of the resource is still valid and hints about how better to estimate when a cached resource may no longer be valid.

In Chapter 7, we dive deep into the heart of caching HTTP requests and responses. We will see these headers again there. Table 3-23 lists the entity caching headers.

![Table-3-23](ScreenshotsForNotes/Chapter3/Table_3_23.PNG)


# 4. Connection Management

## TCP Connections

Just about all of the world’s HTTP communication is carried over TCP/IP, a popular layered set of packet-switched network protocols spoken by computers and network devices around the globe. A client application can open a TCP/IP connection to a server application, running just about anywhere in the world. Once the connection is established, messages exchanged between the client’s and server’s computers will never be lost, damaged, or received out of order.

Say you want the latest power tools price list from Joe’s Hardware store:

```http://www.joes-hardware.com:80/power-tools.html```

When given this URL, your browser performs the steps shown in Figure 4-1. In Steps 1–3, the IP address and port number of the server are pulled from the URL. A TCPconnection is made to the web server in Step 4, and a request message is sent across the connection in Step 5. The response is read in Step 6, and the connection is closed in Step 7.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_1.PNG)

## TCP Reliable Data Pipes

HTTP connections really are nothing more than TCP connections, plus a few rules about how to use them. TCP connections are the reliable connections of the Internet. To send data accurately and quickly, you need to know the basics of TCP.

TCP gives HTTP a reliable bit pipe. Bytes stuffed in one side of a TCP connection come out the other side correctly, and in the right order (see Figure 4-2).

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_2.PNG)

## TCP Streams Are Segmented and Shipped by IP Packets

TCP sends its data in little chunks called IP packets (or IP datagrams). In this way, HTTP is the top layer in a “protocol stack” of “HTTP over TCP over IP,” as depicted in Figure 4-3a. A secure variant, HTTPS, inserts a cryptographic encryption layer (called TLS or SSL) between HTTP and TCP (Figure 4-3b).

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_3.PNG)

When HTTP wants to transmit a message, it streams the contents of the message data, in order, through an open TCP connection. TCP takes the stream of data, chops up the data stream into chunks called segments, and transports the segments across the Internet inside envelopes called IP packets (see Figure 4-4). This is all handled by the TCP/IP software; the HTTP programmer sees none of it.

Each TCP segment is carried by an IP packet from one IP address to another IP address. Each of these IP packets contains:

* An IP packet header (usually 20 bytes)

* A TCP segment header (usually 20 bytes)

* A chunk of TCP data (0 or more bytes)

The IP header contains the source and destination IP addresses, the size, and other flags. The TCP segment header contains TCP port numbers, TCP control flags, and numeric values used for data ordering and integrity checking.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_4.PNG)

## Keeping TCP Connections Straight

A computer might have several TCP connections open at any one time. TCP keeps all these connections straight through port numbers.

Port numbers are like employees’ phone extensions. Just as a company’s main phone number gets you to the front desk and the extension gets you to the right employee, the IP address gets you to the right computer and the port number gets you to the right application. A TCP connection is distinguished by four values:

```<source-IP-address, source-port, destination-IP-address, destination-port>```

Together, these four values uniquely define a connection. Two different TCP connections are not allowed to have the same values for all four address components (but different connections can have the same values for some of the components).

In Figure 4-5, there are four connections: A, B, C and D. The relevant information for each port is listed in Table 4-1.

![Table](ScreenshotsForNotes/Chapter4/Table_4_1.PNG) ![Figure](ScreenshotsForNotes/Chapter4/Figure_4_5.PNG)

Note that some of the connections share the same destination port number (C and D both have destination port 80). Some of the connections have the same source IP address (B and C). Some have the same destination IP address (A and B, and C and D). But no two different connections share all four identical values.

## Programming with TCP Sockets

Operating systems provide different facilities for manipulating their TCP connections. Let’s take a quick look at one TCP programming interface, to make things concrete. Table 4-2shows some of the primary interfaces provided by the sockets API. This sockets API hides all the details of TCP and IP from the HTTP programmer. The sockets API was first developed for the Unix operating system, but variants are now available for almost every operating system and language.

![Table](ScreenshotsForNotes/Chapter4/Table_4_2_1.PNG) ![Table](ScreenshotsForNotes/Chapter4/Table_4_2_2.PNG)



The sockets API lets you create TCP endpoint data structures, connect these endpoints to remote server TCP endpoints, and read and write data streams. The TCP API hides all the details of the underlying network protocol handshaking and the segmentation and reassembly of the TCP data stream to and from IP packets.

In Figure 4-1, we showed how a web browser could download the power-tools.html web page from Joe’s Hardware store using HTTP. The pseudocode in Figure 4-6 sketches how we might use the sockets API to highlight the steps the client and server could perform to implement this HTTP transaction.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_6.PNG)

We begin with the web server waiting for a connection (Figure 4-6, S4). The client determines the IP address and port number from the URL and proceeds to establish a TCP connection to the server (Figure 4-6, C3). Establishing a connection can take a while, depending on how far away the server is, the load on the server, and the congestion of the Internet.

Once the connection is set up, the client sends the HTTP request (Figure 4-6, C5) and the server reads it (Figure 4-6, S6). Once the server gets the entire request message, it processes the request, performs the requested action (Figure 4-6, S7), and writes the data back to the client. The client reads it (Figure 4-6, C6) and processes the response data (Figure 4-6, C7).

## TCP Performance Considerations

Because HTTP is layered directly on TCP, the performance of HTTP transactions depends critically on the performance of the underlying TCP plumbing. This section highlights some significant performance considerations of these TCP connections. By understanding some of the basic performance characteristics of TCP, you’ll better appreciate HTTP’s connection optimization features, and you’ll be able to design and implement higher-performance HTTP applications.

## HTTP Transaction Delays

Let’s start our TCP performance tour by reviewing what networking delays occur in the course of an HTTP request. Figure 4-7 depicts the major connect, transfer, and processing delays for an HTTP transaction.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_7.PNG)

Notice that the transaction processing time can be quite small compared to the time required to set up TCP connections and transfer the request and response messages. Unless the client or server is overloaded or executing complex dynamic resources, most HTTP delays are caused by TCP network delays.

There are several possible causes of delay in an HTTP transaction:

1. A client first needs to determine the IP address and port number of the web server from the URI. If the hostname in the URI was not recently visited, it may take tens of seconds to convert the hostname from a URI into an IP address using the DNS resolution infrastructure.

2. Next, the client sends a TCP connection request to the server and waits for the server to send back a connection acceptance reply. Connection setup delay occurs for every new TCP connection. This usually takes at most a second or two, but it can add up quickly when hundreds of HTTP transactions are made.

3. Once the connection is established, the client sends the HTTP request over the newly established TCP pipe. The web server reads the request message from the TCP connection as the data arrives and processes the request. It takes time for the request message to travel over the Internet and get processed by the server.

4. The web server then writes back the HTTP response, which also takes time.

The magnitude of these TCP network delays depends on hardware speed, the load of the network and server, the size of the request and response messages, and the distance between client and server. The delays also are significantly affected by technical intricacies of the TCP protocol.

## Performance Focus Areas

The remainder of this section outlines some of the most common TCP-related delays affecting HTTP programmers, including the causes and performance impacts of:

* The TCP connection setup handshake

* TCP slow-start congestion control

* Nagle’s algorithm for data aggregation

* TCP’s delayed acknowledgment algorithm for piggybacked acknowledgments

* ```TIME_WAIT``` delays and port exhaustion

If you are writing high-performance HTTP software, you should understand each of these factors. If you don’t need this level of performance optimization, feel free to skip ahead.

## TCP Connection Handshake Delays

When you set up a new TCP connection, even before you send any data, the TCP software exchanges a series of IP packets to negotiate the terms of the connection (see Figure 4-8). These exchanges can significantly degrade HTTP performance if the connections are used for small data transfers.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_8.PNG)

Here are the steps in the TCP connection handshake:

1. To request a new TCP connection, the client sends a small TCP packet (usually 40–60 bytes) to the server. The packet has a special “SYN” flag set, which means it’s a connection request. This is shown in Figure 4-8a.

2. If the server accepts the connection, it computes some connection parameters and sends a TCP packet back to the client, with both the “SYN” and “ACK” flags set, indicating that the connection request is accepted (see Figure 4-8b).

3. Finally, the client sends an acknowledgment back to the server, letting it know that the connection was established successfully (see Figure 4-8c). Modern TCP stacks let the client send data in this acknowledgment packet.

The HTTP programmer never sees these packets—they are managed invisibly by the TCP/IP software. All the HTTP programmer sees is a delay when creating a new TCP connection.

The SYN/SYN+ACK handshake (Figure 4-8a and b) creates a measurable delay when HTTP transactions do not exchange much data, as is commonly the case. The TCP connect ACK packet (Figure 4-8c) often is large enough to carry the entire HTTP request message,* and many HTTP server response messages fit into a single IP packet (e.g., when the response is a small HTML file of a decorative graphic, or a 304 Not Modified response to a browser cache request).

The end result is that small HTTP transactions may spend 50% or more of their time doing TCP setup. Later sections will discuss how HTTP allows reuse of existing connections to eliminate the impact of this TCP setup delay.

## Delayed Acknowledgments

Because the Internet itself does not guarantee reliable packet delivery (Internet routers are free to destroy packets at will if they are overloaded), TCP implements its own acknowledgment scheme to guarantee successful data delivery.

Each TCP segment gets a sequence number and a data-integrity checksum. The receiver of each segment returns small acknowledgment packets back to the sender when segments have been received intact. If a sender does not receive an acknowledgment within a specified window of time, the sender concludes the packet was destroyed or corrupted and resends the data.

Because acknowledgments are small, TCP allows them to “piggyback” on outgoing data packets heading in the same direction. By combining returning acknowledgments with outgoing data packets, TCP can make more efficient use of the network. To increase the chances that an acknowledgment will find a data packet headed in the same direction, many TCP stacks implement a “delayed acknowledgment” algorithm. Delayed acknowledgments hold outgoing acknowledgments in a buffer for a certain window of time (usually 100–200 milliseconds), looking for an outgoing data packet on which to piggyback. If no outgoing data packet arrives in that time, the acknowledgment is sent in its own packet.

Unfortunately, the bimodal request-reply behavior of HTTP reduces the chances that piggybacking can occur. There just aren’t many packets heading in the reverse direction when you want them. Frequently, the disabled acknowledgment algorithms introduce significant delays. Depending on your operating system, you may be able to adjust or disable the delayed acknowledgment algorithm.

Before you modify any parameters of your TCP stack, be sure you know what you are doing. Algorithms inside TCP were introduced to protect the Internet from poorly designed applications. If you modify any TCP configurations, be absolutely sure your application will not create the problems the algorithms were designed to avoid.

## TCP Slow Start

The performance of TCP data transfer also depends on the age of the TCP connection. TCP connections “tune” themselves over time, initially limiting the maximum speed of the connection and increasing the speed over time as data is transmitted successfully. This tuning is called TCP slow start, and it is used to prevent sudden overloading and congestion of the Internet.

TCP slow start throttles the number of packets a TCP endpoint can have in flight at any one time. Put simply, each time a packet is received successfully, the sender gets permission to send two more packets. If an HTTP transaction has a large amount of data to send, it cannot send all the packets at once. It must send one packet and wait for an acknowledgment; then it can send two packets, each of which must be acknowledged, which allows four packets, etc. This is called “opening the congestion window.”

Because of this congestion-control feature, new connections are slower than “tuned” connections that already have exchanged a modest amount of data. Because tuned connections are faster, HTTP includes facilities that let you reuse existing connections. We’ll talk about these HTTP “persistent connections” later in this chapter.

## Nagle's Algorithm and TCP_NODELAY

TCP has a data stream interface that permits applications to stream data of any size to the TCP stack—even a single byte at a time! But because each TCP segment carries at least 40 bytes of flags and headers, network performance can be degraded severely if TCP sends large numbers of packets containing small amounts of data.

Nagle’s algorithm (named for its creator, John Nagle) attempts to bundle up a large amount of TCP data before sending a packet, aiding network efficiency. The algorithm is described in RFC 896, “Congestion Control in IP/TCP Internetworks.”

Nagle’s algorithm discourages the sending of segments that are not full-size (a maximum-size packet is around 1,500 bytes on a LAN, or a few hundred bytes across the Internet). Nagle’s algorithm lets you send a non-full-size packet only if all other packets have been acknowledged. If other packets are still in flight, the partial data is buffered. This buffered data is sent only when pending packets are acknowledged or when the buffer has accumulated enough data to send a full packet.†

Nagle’s algorithm causes several HTTP performance problems. First, small HTTP messages may not fill a packet, so they may be delayed waiting for additional data that will never arrive. Second, Nagle’s algorithm interacts poorly with disabled acknowledgments—Nagle’s algorithm will hold up the sending of data until an acknowledgment arrives, but the acknowledgment itself will be delayed 100–200 milliseconds by the delayed acknowledgment algorithm.‡

HTTP applications often disable Nagle’s algorithm to improve performance, by setting the TCP_NODELAY parameter on their stacks. If you do this, you must ensure that you write large chunks of data to TCP so you don’t create a flurry of small packets.

## TIME_WAIT Accumulation and Port Exhaustion

TIME_WAIT port exhaustion is a serious performance problem that affects performance benchmarking but is relatively uncommon in real deployments. It warrants special attention because most people involved in performance benchmarking eventually run into this problem and get unexpectedly poor performance.

When a TCP endpoint closes a TCP connection, it maintains in memory a small control block recording the IP addresses and port numbers of the recently closed connection. This information is maintained for a short time, typically around twice the estimated maximum segment lifetime (called “2MSL”; often two minutes*), to make sure a new TCP connection with the same addresses and port numbers is not created during this time. This prevents any stray duplicate packets from the previous connection from accidentally being injected into a new connection that has the same addresses and port numbers. In practice, this algorithm prevents two connections with the exact same IP addresses and port numbers from being created, closed, and recreated within two minutes.

Today’s higher-speed routers make it extremely unlikely that a duplicate packet will show up on a server’s doorstep minutes after a connection closes. Some operating systems set 2MSL to a smaller value, but be careful about overriding this value. Packets do get duplicated, and TCP data will be corrupted if a duplicate packet from a past connection gets inserted into a new stream with the same connection values.

The 2MSL connection close delay normally is not a problem, but in benchmarking situations, it can be. It’s common that only one or a few test load-generation computers are connecting to a system under benchmark test, which limits the number of client IP addresses that connect to the server. Furthermore, the server typically is listening on HTTP’s default TCP port, 80. These circumstances limit the available combinations of connection values, at a time when port numbers are blocked from reuse by TIME_WAIT.

In a pathological situation with one client and one web server, of the four values that make up a TCP connection:

```<source-IP-address, source-port, destination-IP-address, destination-port>```

three of them are fixed—only the source port is free to change:

```<client-IP, source-port, server-IP, 80>```

Each time the client connects to the server, it gets a new source port in order to have a unique connection. But because a limited number of source ports are available (say, 60,000) and no connection can be reused for 2MSL seconds (say, 120 seconds), this limits the connect rate to 60,000 / 120 = 500 transactions/sec. If you keep making optimizations, and your server doesn’t get faster than about 500 transactions/ sec, make sure you are not experiencing TIME_WAIT port exhaustion. You can fix this problem by using more client load-generator machines or making sure the client and server rotate through several virtual IP addresses to add more connection combinations.

Even if you do not suffer port exhaustion problems, be careful about having large numbers of open connections or large numbers of control blocks allocated for connection in wait states. Some operating systems slow down dramatically when there are numerous open connections or control blocks.

## The Oft-Misunderstood Connection Header

HTTP allows a chain of HTTP intermediaries between the client and the ultimate origin server (proxies, caches, etc.). HTTP messages are forwarded hop by hop from the client, through intermediary devices, to the origin server (or the reverse).

In some cases, two adjacent HTTP applications may want to apply a set of options to their shared connection. The HTTP Connection header field has a comma-separated list of connection tokens that specify options for the connection that aren’t propagated to other connections. For example, a connection that must be closed after sending the next message can be indicated by Connection: close.

The Connection header sometimes is confusing, because it can carry three different types of tokens:

* HTTP header field names, listing headers relevant for only this connection

* Arbitrary token values, describing nonstandard options for this connection

* The value close, indicating the persistent connection will be closed when done

If a connection token contains the name of an HTTP header field, that header field contains connection-specific information and must not be forwarded. Any header fields listed in the Connection header must be deleted before the message is forwarded. Placing a hop-by-hop header name in a Connection header is known as “protecting the header,” because the Connection header protects against accidental forwarding of the local header. An example is shown in Figure 4-9.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_9.PNG)

When an HTTP application receives a message with a Connection header, the receiver parses and applies all options requested by the sender. It then deletes the Connection header and all headers listed in the Connection header before forwarding the message to the next hop. In addition, there are a few hop-by-hop headers that might not be listed as values of a Connection header, but must not be proxied. These include Proxy-Authenticate, Proxy-Connection, Transfer-Encoding, and Upgrade. For more about the Connection header, see Appendix C.

## Serial Transaction Delays

TCP performance delays can add up if the connections are managed naively. For example, suppose you have a web page with three embedded images. Your browser needs to issue four HTTP transactions to display this page: one for the top-level HTML and three for the embedded images. If each transaction requires a new connection, the connection and slow-start delays can add up (see Figure 4-10).

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_10.PNG)

In addition to the real delay imposed by serial loading, there is also a psychological perception of slowness when a single image is loading and nothing is happening on the rest of the page. Users prefer multiple images to load at the same time.

Another disadvantage of serial loading is that some browsers are unable to display anything onscreen until enough objects are loaded, because they don’t know the sizes of the objects until they are loaded, and they may need the size information to decide where to position the objects on the screen. In this situation, the browser may be making good progress loading objects serially, but the user may be faced with a blank white screen, unaware that any progress is being made at all.

Several current and emerging techniques are available to improve HTTP connection performance. The next several sections discuss four such techniques:

* *Parallel connections*
    * Concurrent HTTP requests across multiple TCP connections
* *Persistent connections*
    * Reusing TCP connections to eliminate connect/close delays
* *Pipelined connections*
    * Concurrent HTTP requests across a shared TCP connection
* *Multiplexed connections*
    * Interleaving chunks of requests and responses (experimental) 

## Parallel Connections

As we mentioned previously, a browser could naively process each embedded object serially by completely requesting the original HTML page, then the first embedded object, then the second embedded object, etc. But this is too slow!

HTTP allows clients to open multiple connections and perform multiple HTTP transactions in parallel, as sketched in Figure 4-11. In this example, four embedded images are loaded in parallel, with each transaction getting its own TCP connection.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_11.PNG)

### Parallel Connections May Make Pages Load Faster

Composite pages consisting of embedded objects may load faster if they take advantage of the dead time and bandwidth limits of a single connection. The delays can be overlapped, and if a single connection does not saturate the client’s Internet bandwidth, the unused bandwidth can be allocated to loading additional objects.

Figure 4-12 shows a timeline for parallel connections, which is significantly faster than Figure 4-10. The enclosing HTML page is loaded first, and then the remaining three transactions are processed concurrently, each with their own connection. Because the images are loaded in parallel, the connection delays are overlapped.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_12.PNG)

### Parallel Connections Are Not Always Faster

Even though parallel connections may be faster, however, they are not always faster. When the client’s network bandwidth is scarce (for example, a browser connected to the Internet through a 28.8-Kbps modem), most of the time might be spent just transferring data. In this situation, a single HTTP transaction to a fast server could easily consume all of the available modem bandwidth. If multiple objects are loaded in parallel, each object will just compete for this limited bandwidth, so each object will load proportionally slower, yielding little or no performance advantage.

Also, a large number of open connections can consume a lot of memory and cause performance problems of their own. Complex web pages may have tens or hundreds of embedded objects. Clients might be able to open hundreds of connections, but few web servers will want to do that, because they often are processing requests for many other users at the same time. A hundred simultaneous users, each opening 100 connections, will put the burden of 10,000 connections on the server. This can cause significant server slowdown. The same situation is true for high-load proxies.

In practice, browsers do use parallel connections, but they limit the total number of parallel connections to a small number (often four). Servers are free to close excessive connections from a particular client.

### Parallel Connections May "Feel" Faster

Okay, so parallel connections don’t always make pages load faster. But even if they don’t actually speed up the page transfer, as we said earlier, parallel connections often make users feel that the page loads faster, because they can see progress being made as multiple component objects appear onscreen in parallel.† Human beings perceive that web pages load faster if there’s lots of action all over the screen, even if a stopwatch actually shows the aggregate page download time to be slower!

## Persistent Connections

Web clients often open connections to the same site. For example, most of the embedded images in a web page often come from the same web site, and a significant number of hyperlinks to other objects often point to the same site. Thus, an application that initiates an HTTP request to a server likely will make more requests to that server in the near future (to fetch the inline images, for example). This property is called site locality.

For this reason, HTTP/1.1 (and enhanced versions of HTTP/1.0) allows HTTP devices to keep TCP connections open after transactions complete and to reuse the preexisting connections for future HTTP requests. TCP connections that are kept open after transactions complete are called persistent connections. Nonpersistent connections are closed after each transaction. Persistent connections stay open across transactions, until either the client or the server decides to close them.

By reusing an idle, persistent connection that is already open to the target server, you can avoid the slow connection setup. In addition, the already open connection can avoid the slow-start congestion adaptation phase, allowing faster data transfers.

### Persistent Versus Parallel Connections

As we’ve seen, parallel connections can speed up the transfer of composite pages. But parallel connections have some disadvantages:

* Each transaction opens/closes a new connection, costing time and bandwidth.

* Each new connection has reduced performance because of TCP slow start.

* There is a practical limit on the number of open parallel connections.

Persistent connections offer some advantages over parallel connections. They reduce the delay and overhead of connection establishment, keep the connections in a tuned state, and reduce the potential number of open connections. However, persistent connections need to be managed with care, or you may end up accumulating a large number of idle connections, consuming local resources and resources on remote clients and servers.

Persistent connections can be most effective when used in conjunction with parallel connections. Today, many web applications open a small number of parallel connections, each persistent. There are two types of persistent connections: the older HTTP/1.0+ “keep-alive” connections and the modern HTTP/1.1 “persistent” connections. We’ll look at both flavors in the next few sections.

## HTTP/1.0+Keep-Alive Connections

Many HTTP/1.0 browsers and servers were extended (starting around 1996) to support an early, experimental type of persistent connections called keep-alive connections. These early persistent connections suffered from some interoperability design problems that were rectified in later revisions of HTTP/1.1, but many clients and servers still use these earlier keep-alive connections.

Some of the performance advantages of keep-alive connections are visible in Figure 4-13, which compares the timeline for four HTTP transactions over serial connections against the same transactions over a single persistent connection. The timeline is compressed because the connect and close overheads are removed.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_13.PNG)

## Keep-Alive Operation

Keep-alive is deprecated and no longer documented in the current HTTP/1.1 specification. However, keep-alive handshaking is still in relatively common use by browsers and servers, so HTTP implementors should be prepared to interoperate with it. We’ll take a quick look at keep-alive operation now. Refer to older versions of the HTTP/1.1 specification (such as RFC 2068) for a more complete explanation of keep-alive handshaking.

Clients implementing HTTP/1.0 keep-alive connections can request that a connection be kept open by including the Connection: Keep-Alive request header.

If the server is willing to keep the connection open for the next request, it will respond with the same header in the response (see Figure 4-14). If there is no Connection: keep-alive header in the response, the client assumes that the server does not support keep-alive and that the server will close the connection when the response message is sent back.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_14.PNG)

### Keep-Alive Options

Note that the keep-alive headers are just requests to keep the connection alive. Clients and servers do not need to agree to a keep-alive session if it is requested. They can close idle keep-alive connections at any time and are free to limit the number of transactions processed on a keep-alive connection.

The keep-alive behavior can be tuned by comma-separated options specified in the Keep-Alive general header:

* The timeout parameter is sent in a Keep-Alive response header. It estimates how long the server is likely to keep the connection alive for. This is not a guarantee.

* The max parameter is sent in a Keep-Alive response header. It estimates how many more HTTP transactions the server is likely to keep the connection alive for. This is not a guarantee.

* The Keep-Alive header also supports arbitrary unprocessed attributes, primarily for diagnostic and debugging purposes. The syntax is name [= value].

The Keep-Alive header is completely optional but is permitted only when Connection: Keep-Alive also is present. Here’s an example of a Keep-Alive response header indicating that the server intends to keep the connection open for at most five more transactions, or until it has sat idle for two minutes:

```HTTP
Connection: Keep-Alive
Keep-Alive: max=5, timeout=120
```

### Keep-Alive Connection Restrictions and Rules

Here are some restrictions and clarifications regarding the use of keep-alive connections:

* Keep-alive does not happen by default in HTTP/1.0. The client must send a Connection: Keep-Alive request header to activate keep-alive connections.

* The Connection: Keep-Alive header must be sent with all messages that want to continue the persistence. If the client does not send a Connection: Keep-Alive header, the server will close the connection after that request.

* Clients can tell if the server will close the connection after the response by detecting the absence of the Connection: Keep-Alive response header.

* The connection can be kept open only if the length of the message’s entity body can be determined without sensing a connection close—this means that the entity body must have a correct Content-Length, have a multipart media type, or be encoded with the chunked transfer encoding. Sending the wrong Content-Length back on a keep-alive channel is bad, because the other end of the transaction will not be able to accurately detect the end of one message and the start of another.

* Proxies and gateways must enforce the rules of the Connection header; the proxy or gateway must remove any header fields named in the Connection header, and the Connection header itself, before forwarding or caching the message.

* Formally, keep-alive connections should not be established with a proxy server that isn’t guaranteed to support the Connection header, to prevent the problem with dumb proxies described below. This is not always possible in practice.

* Technically, any Connection header fields (including Connection: Keep-Alive) received from an HTTP/1.0 device should be ignored, because they may have been forwarded mistakenly by an older proxy server. In practice, some clients and servers bend this rule, although they run the risk of hanging on older proxies.

* Clients must be prepared to retry requests if the connection closes before they receive the entire response, unless the request could have side effects if repeated.

## Keep-Alive and Dumb Proxies

Let’s take a closer look at the subtle problem with keep-alive and dumb proxies. A web client’s Connection: Keep-Alive header is intended to affect just the single TCP link leaving the client. This is why it is named the “connection” header. If the client is talking to a web server, the client sends a Connection: Keep-Alive header to tell the server it wants keep-alive. The server sends a Connection: Keep-Alive header back if it supports keep-alive and doesn’t send it if it doesn’t.

## The Connection header and blind relays

The problem comes with proxies—in particular, proxies that don’t understand the Connection header and don’t know that they need to remove the header before proxying it down the chain. Many older or simple proxies act as blind relays, tunneling bytes from one connection to another, without specially processing the Connection header.

Imagine a web client talking to a web server through a dumb proxy that is acting as a blind relay. This situation is depicted in Figure 4-15.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_15.PNG)

Here’s what’s going on in this figure:

1. In Figure 4-15a, a web client sends a message to the proxy, including the Connection: Keep-Alive header, requesting a keep-alive connection if possible. The client waits for a response to learn if its request for a keep-alive channel was granted.

2. The dumb proxy gets the HTTP request, but it doesn’t understand the Connection header (it just treats it as an extension header). The proxy has no idea what keep-alive is, so it passes the message verbatim down the chain to the server (Figure 4-15b). But the Connection header is a hop-by-hop header; it applies to only a single transport link and shouldn’t be passed down the chain. Bad things are about to happen.

3. In Figure 4-15b, the relayed HTTP request arrives at the web server. When the web server receives the proxied Connection: Keep-Alive header, it mistakenly concludes that the proxy (which looks like any other client to the server) wants to speak keep-alive! That’s fine with the web server—it agrees to speak keepalive and sends a Connection: Keep-Alive response header back in Figure 4-15c. So, at this point, the web server thinks it is speaking keep-alive with the proxy and will adhere to rules of keep-alive. But the proxy doesn’t know the first thing about keep-alive. Uh-oh.

4. In Figure 4-15d, the dumb proxy relays the web server’s response message back to the client, passing along the Connection: Keep-Alive header from the web server. The client sees this header and assumes the proxy has agreed to speak keep-alive. So at this point, both the client and server believe they are speaking keep-alive, but the proxy they are talking to doesn’t know anything about keep-alive.

5. Because the proxy doesn’t know anything about keep-alive, it reflects all the data it receives back to the client and then waits for the origin server to close the connection. But the origin server will not close the connection, because it believes the proxy explicitly asked the server to keep the connection open. So the proxy will hang waiting for the connection to close.

6. When the client gets the response message back in Figure 4-15d, it moves right along to the next request, sending another request to the proxy on the keep-alive connection (see Figure 4-15e). Because the proxy never expects another request on the same connection, the request is ignored and the browser just spins, making no progress.

7. This miscommunication causes the browser to hang until the client or server times out the connection and closes it.

## Proxies and hop-by-hop headers

To avoid this kind of proxy miscommunication, modern proxies must never proxy the Connection header or any headers whose names appear inside the Connection values. So if a proxy receives a Connection: Keep-Alive header, it shouldn’t proxy either the Connection header or any headers named Keep-Alive.

In addition, there are a few hop-by-hop headers that might not be listed as values of a Connection header, but must not be proxied or served as a cache response either. These include Proxy-Authenticate, Proxy-Connection, Transfer-Encoding, and Upgrade. For more information, refer back to “The Oft-Misunderstood Connection Header.”

## The Proxy-Connection Hack

Browser and proxy implementors at Netscape proposed a clever workaround to the blind relay problem that didn’t require all web applications to support advanced versions of HTTP. The workaround introduced a new header called Proxy-Connection and solved the problem of a single blind relay interposed directly after the client— but not all other situations. Proxy-Connection is implemented by modern browsers when proxies are explicitly configured and is understood by many proxies.

The idea is that dumb proxies get into trouble because they blindly forward hop-byhop headers such as Connection: Keep-Alive. Hop-by-hop headers are relevant only for that single, particular connection and must not be forwarded. This causes trouble when the forwarded headers are misinterpreted by downstream servers as requests from the proxy itself to control its connection.

In the Netscape workaround, browsers send nonstandard Proxy-Connection extension headers to proxies, instead of officially supported and well-known Connection headers. If the proxy is a blind relay, it relays the nonsense Proxy-Connection header to the web server, which harmlessly ignores the header. But if the proxy is a smart proxy (capable of understanding persistent connection handshaking), it replaces the nonsense Proxy-Connection header with a Connection header, which is then sent to the server, having the desired effect.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_16.PNG)

Figure 4-16a–d shows how a blind relay harmlessly forwards Proxy-Connection headers to the web server, which ignores the header, causing no keep-alive connection to be established between the client and proxy or the proxy and server. The smart proxy in Figure 4-16e–h understands the Proxy-Connection header as a request to speak keep-alive, and it sends out its own Connection: Keep-Alive headers to establish keep-alive connections.

This scheme works around situations where there is only one proxy between the client and server. But if there is a smart proxy on either side of the dumb proxy, the problem will rear its ugly head again, as shown in Figure 4-17.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_17.PNG)

Furthermore, it is becoming quite common for “invisible” proxies to appear in networks, either as firewalls, intercepting caches, or reverse proxy server accelerators. Because these devices are invisible to the browser, the browser will not send them Proxy-Connection headers. It is critical that transparent web applications implement persistent connections correctly.

## HTTP/1.1 Persistent Connections

HTTP/1.1 phased out support for keep-alive connections, replacing them with an improved design called persistent connections. The goals of persistent connections are the same as those of keep-alive connections, but the mechanisms behave better.

Unlike HTTP/1.0+ keep-alive connections, HTTP/1.1 persistent connections are active by default. HTTP/1.1 assumes all connections are persistent unless otherwise indicated. HTTP/1.1 applications have to explicitly add a Connection: close header to a message to indicate that a connection should close after the transaction is complete. This is a significant difference from previous versions of the HTTP protocol, where keep-alive connections were either optional or completely unsupported.

An HTTP/1.1 client assumes an HTTP/1.1 connection will remain open after a response, unless the response contains a Connection: close header. However, clients and servers still can close idle connections at any time. Not sending Connection: close does not mean that the server promises to keep the connection open forever.

### Persistent Connection Restrictions and Rules

Here are the restrictions and clarifications regarding the use of persistent connections:

* After sending a Connection: close request header, the client can’t send more requests on that connection.

* If a client does not want to send another request on the connection, it should send a Connection: close request header in the final request.

* The connection can be kept persistent only if all messages on the connection have a correct, self-defined message length—i.e., the entity bodies must have correct Content-Lengths or be encoded with the chunked transfer encoding.

* HTTP/1.1 proxies must manage persistent connections separately with clients and servers—each persistent connection applies to a single transport hop.

* HTTP/1.1 proxy servers should not establish persistent connections with an HTTP/1.0 client (because of the problems of older proxies forwarding Connection headers) unless they know something about the capabilities of the client. This is, in practice, difficult, and many vendors bend this rule.

* Regardless of the values of Connection headers, HTTP/1.1 devices may close the connection at any time, though servers should try not to close in the middle of transmitting a message and should always respond to at least one request before closing.

* HTTP/1.1 applications must be able to recover from asynchronous closes. Clients should retry the requests as long as they don’t have side effects that could accumulate.

* Clients must be prepared to retry requests if the connection closes before they receive the entire response, unless the request could have side effects if repeated.

* A single user client should maintain at most two persistent connections to any server or proxy, to prevent the server from being overloaded. Because proxies may need more connections to a server to support concurrent users, a proxy should maintain at most 2N connections to any server or parent proxy, if there are N users trying to access the servers.

## Pipelinde Connections

HTTP/1.1 permits optional request pipelining over persistent connections. This is a further performance optimization over keep-alive connections. Multiple requests can be enqueued before the responses arrive. While the first request is streaming across the network to a server on the other side of the globe, the second and third requests can get underway. This can improve performance in high-latency network conditions, by reducing network round trips.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_18.PNG)

Figure 4-18a-c shows how persistent connections can eliminate TCP connection delays and how pipelined requests (Figure 4-18c) can eliminate transfer latencies.

There are several restrictions for pipelining:

* HTTP clients should not pipeline until they are sure the connection is persistent.

* HTTP responses must be returned in the same order as the requests. HTTP messages are not tagged with sequence numbers, so there is no way to match responses with requests if the responses are received out of order.

* HTTP clients must be prepared for the connection to close at any time and be prepared to redo any pipelined requests that did not finish. If the client opens a persistent connection and immediately issues 10 requests, the server is free to close the connection after processing only, say, 5 requests. The remaining 5 requests will fail, and the client must be willing to handle these premature closes and reissue the requests.

* HTTP clients should not pipeline requests that have side effects (such as POSTs). In general, on error, pipelining prevents clients from knowing which of a series of pipelined requests were executed by the server. Because nonidempotent requests such as POSTs cannot safely be retried, you run the risk of some methods never being executed in error conditions.

## The Mysteries of Connection Close

Connection management—particularly knowing when and how to close connections— is one of the practical black arts of HTTP. This issue is more subtle than many developers first realize, and little has been written on the subject.

## "At Will" Disconnection

Any HTTP client, server, or proxy can close a TCP transport connection at any time. The connections normally are closed at the end of a message,* but during error conditions, the connection may be closed in the middle of a header line or in other strange places.

This situation is common with pipelined persistent connections. HTTP applications are free to close persistent connections after any period of time. For example, after a persistent connection has been idle for a while, a server may decide to shut it down.

However, the server can never know for sure that the client on the other end of the line wasn’t about to send data at the same time that the “idle” connection was being shut down by the server. If this happens, the client sees a connection error in the middle of writing its request message.

## Content-Length and Truncation

Each HTTP response should have an accurate Content-Length header to describe the size of the response body. Some older HTTP servers omit the Content-Length header or include an erroneous length, depending on a server connection close to signify the actual end of data.

When a client or proxy receives an HTTP response terminating in connection close, and the actual transferred entity length doesn’t match the Content-Length (or there is no Content-Length), the receiver should question the correctness of the length.

If the receiver is a caching proxy, the receiver should not cache the response (to minimize future compounding of a potential error). The proxy should forward the questionable message intact, without attempting to “correct” the Content-Length, to maintain semantic transparency.

## Connection Close Tolerance, Retries, and Idempotency

Connections can close at any time, even in non-error conditions. HTTP applications have to be ready to properly handle unexpected closes. If a transport connection closes while the client is performing a transaction, the client should reopen the connection and retry one time, unless the transaction has side effects. The situation is worse for pipelined connections. The client can enqueue a large number of requests, but the origin server can close the connection, leaving numerous requests unprocessed and in need of rescheduling.

Side effects are important. When a connection closes after some request data was sent but before the response is returned, the client cannot be 100% sure how much of the transaction actually was invoked by the server. Some transactions, such as GETting a static HTML page, can be repeated again and again without changing anything. Other transactions, such as POSTing an order to an online book store, shouldn’t be repeated, or you may risk multiple orders.

***A transaction is idempotent if it yields the same result regardless of whether it is executed once or many times.*** Implementors can assume the GET, HEAD, PUT, DELETE, TRACE, and OPTIONS methods share this property.* Clients shouldn’t pipeline nonidempotent requests (such as POSTs). Otherwise, a premature termination of the transport connection could lead to indeterminate results. If you want to send a nonidempotent request, you should wait for the response status for the previous request.

Nonidempotent methods or sequences must not be retried automatically, although user agents may offer a human operator the choice of retrying the request. For example, most browsers will offer a dialog box when reloading a cached POST response, asking if you want to post the transaction again.

## Graceful Connection Close

TCP connections are bidirectional, as shown in Figure 4-19. Each side of a TCP connection has an input queue and an output queue, for data being read or written. Data placed in the output of one side will eventually show up on the input of the other side.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_19.PNG)

### Full and half closes

An application can close either or both of the TCP input and output channels. A close( ) sockets call closes both the input and output channels of a TCP connection.This is called a “full close” and is depicted in Figure 4-20a. You can use the shutdown( ) sockets call to close either the input or output channel individually. This is called a “half close” and is depicted in Figure 4-20b.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_20.PNG)

### TCP close and reset errors

Simple HTTP applications can use only full closes. But when applications start talking to many other types of HTTP clients, servers, and proxies, and when they start using pipelined persistent connections, it becomes important for them to use half closes to prevent peers from getting unexpected write errors.

In general, closing the output channel of your connection is always safe. The peer on the other side of the connection will be notified that you closed the connection by getting an end-of-stream notification once all the data has been read from its buffer.

Closing the input channel of your connection is riskier, unless you know the other side doesn’t plan to send any more data. If the other side sends data to your closed input channel, the operating system will issue a TCP “connection reset by peer” message back to the other side’s machine, as shown in Figure 4-21. Most operating systems treat this as a serious error and erase any buffered data the other side has not read yet. This is very bad for pipelined connections.

![Figure](ScreenshotsForNotes/Chapter4/Figure_4_21.PNG)

Say you have sent 10 pipelined requests on a persistent connection, and the responses already have arrived and are sitting in your operating system’s buffer (but the application hasn’t read them yet). Now say you send request #11, but the server decides you’ve used this connection long enough, and closes it. Your request #11 will arrive at a closed connection and will reflect a reset back to you. This reset will erase your input buffers.

When you finally get to reading data, you will get a connection reset by peer error, and the buffered, unread response data will be lost, even though much of it successfully arrived at your machine.

### Graceful close

The HTTP specification counsels that when clients or servers want to close a connection unexpectedly, they should “issue a graceful close on the transport connection,” but it doesn’t describe how to do that.

In general, applications implementing graceful closes will first close their output channels and then wait for the peer on the other side of the connection to close its output channels. When both sides are done telling each other they won’t be sending any more data (i.e., closing output channels), the connection can be closed fully, with no risk of reset.

Unfortunately, there is no guarantee that the peer implements or checks for half closes. For this reason, applications wanting to close gracefully should half close their output channels and periodically check the status of their input channels (looking for data or for the end of the stream). If the input channel isn’t closed by the peer within some timeout period, the application may force connection close to save resources

---
---

# Part II: HTTP Architecture

---
---

# 5. Web Servers

## Web Servers Come in All Shapes and Sizes

A web server processes HTTP requests and serves responses. The term “web server” can refer either to web server software or to the particular device or computer dedicated to serving the web pages.

Web servers comes in all flavors, shapes, and sizes. There are trivial 10-line Perl script web servers, 50-MB secure commerce engines, and tiny servers-on-a-card. But whatever the functional differences, all web servers receive HTTP requests for resources and serve content back to the clients (look back to Figure 1-5).

## Web Server Implementations

Web servers implement HTTP and the related TCP connection handling. They also manage the resources served by the web server and provide administrative features to configure, control, and enhance the web server.

The web server logic implements the HTTP protocol, manages web resources, and provides web server administrative capabilities. The web server logic shares responsibilities for managing TCP connections with the operating system. The underlying operating system manages the hardware details of the underlying computer system and provides TCP/IP network support, filesystems to hold web resources, and process management to control current computing activities.

Web servers are available in many forms:

* You can install and run general-purpose software web servers on standard computer systems.

* If you don’t want the hassle of installing software, you can purchase a web server appliance, in which the software comes preinstalled and preconfigured on a computer, often in a snazzy-looking chassis.

* Given the miracles of microprocessors, some companies even offer embedded web servers implemented in a small number of computer chips, making them perfect administration consoles for consumer devices.

## General-Purpose Software Web Servers

General-purpose software web servers run on standard, network-enabled computer systems. You can choose open source software (such as Apache or W3C’s Jigsaw) or commercial software (such as Microsoft’s and iPlanet’s web servers). Web server software is available for just about every computer and operating system.

## Web Server Appliances

Web server appliances are prepackaged software/hardware solutions. The vendor preinstalls a software server onto a vendor-chosen computer platform and preconfigures the software

Appliance solutions remove the need to install and configure software and often greatly simplify administration. However, the web server often is less flexible and feature-rich, and the server hardware is not easily repurposeable or upgradable.

## Embedded Web Servers

Embedded servers are tiny web servers intended to be embedded into consumer products (e.g., printers or home appliances). Embedded web servers allow users to administer their consumer devices using a convenient web browser interface.

Some embedded web servers can even be implemented in less than one square inch, but they usually offer a minimal feature set.

## What Real Web Servers Do

State-ofthe- art commercial web servers are much more complicated, but they do perform several common tasks, as shown in Figure 5-3:

1. Set up connection—accept a client connection, or close if the client is unwanted.

2. Receive request—read an HTTP request message from the network.

3. Process request—interpret the request message and take action.

4. Access resource—access the resource specified in the message.

5. Construct response—create the HTTP response message with the right headers.

6. Send response—send the response back to the client.

7. Log transaction—place notes about the completed transaction in a log file.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_3.PNG)

## Step 1: Accepting Client Connections

If a client already has a persistent connection open to the server, it can use that connection to send its request. Otherwise, the client needs to open a new connection to the server (refer back to Chapter 4 to review HTTP connection-management technology).

### Handling New Connections

When a client requests a TCP connection to the web server, the web server establishes the connection and determines which client is on the other side of the connection, extracting the IP address from the TCP connection.* Once a new connection is established and accepted, the server adds the new connection to its list of existing web server connections and prepares to watch for data on the connection.

The web server is free to reject and immediately close any connection. Some web servers close connections because the client IP address or hostname is unauthorized or is a known malicious client. Other identification techniques can also be used.

### Client Hostname Identification

Most web servers can be configured to convert client IP addresses into client hostnames, using “reverse DNS.” Web servers can use the client hostname for detailed access control and logging. Be warned that hostname lookups can take a very long time, slowing down web transactions. Many high-capacity web servers either disable hostname resolution or enable it only for particular content.

### Determining the Client User Through ident

Some web servers also support the IETF ident protocol. The ident protocol lets servers find out what username initiated an HTTP connection. This information is particularly useful for web server logging—the second field of the popular Common Log Format contains the ident username of each HTTP request.*

If a client supports the ident protocol, the client listens on TCP port 113 for ident requests. Figure 5-4 shows how the ident protocol works. In Figure 5-4a, the client opens an HTTP connection. The server then opens its own connection back to the client’s identd server port (113), sends a simple request asking for the username corresponding to the new connection (specified by client and server port numbers), and retrieves from the client the response containing the username.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_4.PNG)

ident can work inside organizations, but it does not work well across the public Internet for many reasons, including:

* Many client PCs don’t run the identd Identification Protocol daemon software.

* The ident protocol significantly delays HTTP transactions.

* Many firewalls won’t permit incoming ident traffic.

* The ident protocol is insecure and easy to fabricate.

* The ident protocol doesn’t support virtual IP addresses well.

* There are privacy concerns about exposing client usernames.

## Step 2: Receiving Request Messages

As the data arrives on connections, the web server reads out the data from the network connection and parses out the pieces of the request message (Figure 5-5).

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_5.PNG)

When parsing the request message, the web server:

* Parses the request line looking for the request method, the specified resource identifier (URI), and the version number,* each separated by a single space, and ending with a carriage-return line-feed (CRLF) sequence†

* Reads the message headers, each ending in CRLF

* Detects the end-of-headers blank line, ending in CRLF (if present)

* Reads the request body, if any (length specified by the Content-Length header)

When parsing request messages, web servers receive input data erratically from the network. The network connection can stall at any point. The web server needs to read data from the network and temporarily store the partial message data in memory until it receives enough data to parse it and make sense of it.

### Internal Representations of Messages

Some web servers also store the request messages in internal data structures that make the message easy to manipulate. For example, the data structure might contain pointers and lengths of each piece of the request message, and the headers might be stored in a fast lookup table so the specific values of particular headers can be accessed quickly (Figure 5-6).

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_6.PNG)

### Connection Input/Output Processing Architectures

High-performance web servers support thousands of simultaneous connections. These connections let the web server communicate with clients around the world, each with one or more connections open to the server. Some of these connections may be sending requests rapidly to the web server, while other connections trickle requests slowly or infrequently, and still others are idle, waiting quietly for some future activity.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_7.PNG)

Web servers constantly watch for new web requests, because requests can arrive at any time. Different web server architectures service requests in different ways, as Figure 5-7 illustrates:

* *Single-threaded web servers*(Figure 5-7a)

    * Single-threaded web servers process one request at a time until completion. When the transaction is complete, the next connection is processed. This architecture is simple to implement, but during processing, all the other connections are ignored. This creates serious performance problems and is appropriate only for low-load servers and diagnostic tools like type-o-serve.

* *Multiprocess and multithreaded web servers* (Figure 5-7b)

    * Multiprocess and multithreaded web servers dedicate multiple processes or higher-efficiency threads to process requests simultaneously.* The threads/ processes may be created on demand or in advance.† Some servers dedicate a thread/process for every connection, but when a server processes hundreds, thousands, or even tens of thousands of simultaneous connections, the resulting number of processes or threads may consume too much memory or system resources. Thus, many multithreaded web servers put a limit on the maximum number of threads/processes.

* *Multiplexed I/O servers* (Figure 5-7c)

    * To support large numbers of connections, many web servers adopt multiplexed architectures. In a multiplexed architecture, all the connections are simultaneously watched for activity. When a connection changes state (e.g., when data becomes available or an error condition occurs), a small amount of processing is performed on the connection; when that processing is complete, the connection is returned to the open connection list for the next change in state. Work is done on a connection only when there is something to be done; threads and processes are not tied up waiting on idle connections.

* *Multiplexed multithreaded web servers* (Figure 5-7d)

    * Some systems combine multithreading and multiplexing to take advantage of multiple CPUs in the computer platform. Multiple threads (often one per physical processor) each watch the open connections (or a subset of the open connections) and perform a small amount of work on each connection.

## Step 3: Processing Requests

Once the web server has received a request, it can process the request using the method, resource, headers, and optional body.

Some methods (e.g., POST) require entity body data in the request message. Other methods (e.g., OPTIONS) allow a request body but don’t require one. A few methods (e.g., GET) forbid entity body data in request messages.

## Step 4: Mapping and Accessing Resources

Web servers are resource servers. They deliver precreated content, such as HTML pages or JPEG images, as well as dynamic content from resource-generating applications running on the servers.

Before the web server can deliver content to the client, it needs to identify the source of the content, by mapping the URI from the request message to the proper content or content generator on the web server.

### Docroots

Web servers support different kinds of resource mapping, but the simplest form of resource mapping uses the request URI to name a file in the web server’s filesystem. Typically, a special folder in the web server filesystem is reserved for web content. This folder is called the document root, or docroot. The web server takes the URI from the request message and appends it to the document root.

In Figure 5-8, a request arrives for /specials/saw-blade.gif. The web server in this example has document root /usr/local/httpd/files. The web server returns the file /usr/ local/httpd/files/specials/saw-blade.gif.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_8.PNG)

### Virtually hosted docroots

Virtually hosted web servers host multiple web sites on the same web server, giving each site its own distinct document root on the server. A virtually hosted web server identifies the correct document root to use from the IP address or hostname in the URI or the Host header. This way, two web sites hosted on the same web server can have completely distinct content, even if the request URIs are identical.

In Figure 5-9, the server hosts two sites: www.joes-hardware.com and www.marysantiques. com. The server can distinguish the web sites using the HTTP Host header, or from distinct IP addresses.

* When request A arrives, the server fetches the file for /docs/joe/index.html.

* When request B arrives, the server fetches the file for /docs/mary/index.html.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_9.PNG)

### User home directory docroots

Another common use of docroots gives people private web sites on a web server. A typical convention maps URIs whose paths begin with a slash and tilde (/~) followed by a username to a private document root for that user. The private docroot is often the folder called public_html inside that user’s home directory, but it can be configured differently (Figure 5-10).

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_10.PNG)

### Directory Listings

A web server can receive requests for directory URLs, where the path resolves to a directory, not a file. Most web servers can be configured to take a few different actions when a client requests a directory URL:

* Return an error.

* Return a special, default, “index file” instead of the directory.

* Scan the directory, and return an HTML page containing the contents.

Most web servers look for a file named index.html or index.htm inside a directory to represent that directory. If a user requests a URL for a directory and the directory contains a file named index.html (or index.htm), the server will return the contents of that file.

### Dynamic Content Resource Mapping

Web servers also can map URIs to dynamic resources—that is, to programs that generate content on demand (Figure 5-11). In fact, a whole class of web servers called application servers connect web servers to sophisticated backend applications. The web server needs to be able to tell when a resource is a dynamic resource, where the dynamic content generator program is located, and how to run the program. Most web servers provide basic mechanisms to identify and map dynamic resources.

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_11.PNG)

### Server-Side Includes (SSI)

Many web servers also provide support for server-side includes. If a resource is flagged as containing server-side includes, the server processes the resource contents before sending them to the client.

The contents are scanned for certain special patterns (often contained inside special HTML comments), which can be variable names or embedded scripts. The special patterns are replaced with the values of variables or the output of executable scripts. This is an easy way to create dynamic content.

### Access Controls

Web servers also can assign access controls to particular resources. When a request arrives for an access-controlled resource, the web server can control access based on the IP address of the client, or it can issue a password challenge to get access to the resource.

## Step 5: Building Responses

Once the web server has identified the resource, it performs the action described in the request method and returns the response message. The response message contains a response status code, response headers, and a response body if one was generated. HTTP response codes were detailed in “Status Codes” in Chapter 3.

### Response Entities

If the transaction generated a response body, the content is sent back with the response message. If there was a body, the response message usually contains:

* A Content-Type header, describing the MIME type of the response body

* A Content-Length header, describing the size of the response body

* The actual message body content

### MIME Typing

The web server is responsible for determining the MIME type of the response body. There are many ways to configure servers to associate MIME types with resources:

![Figure](ScreenshotsForNotes/Chapter5/Figure_5_12.PNG)

* *mime.types*

    * The web server can use the extension of the filename to indicate MIME type. The web server scans a file containing MIME types for each extension to compute the MIME type for each resource. This extension-based type association is the most common; it is illustrated in Figure 5-12.

* *Magic typing*

    * The Apache web server can scan the contents of each resource and patternmatch the content against a table of known patterns (called the magic file) to determine the MIME type for each file. This can be slow, but it is convenient, especially if the files are named without standard extensions.

* *Explicit typing*

    * Web servers can be configured to force particular files or directory contents to have a MIME type, regardless of the file extension or contents.

* *Type negotiation*

    * Some web servers can be configured to store a resource in multiple document formats. In this case, the web server can be configured to determine the “best” format to use (and the associated MIME type) by a negotiation process with the user. We’ll discuss this in Chapter 17.

Web servers also can be configured to associate particular files with MIME types.

### Redirection

Web servers sometimes return redirection responses instead of success messages. A web server can redirect the browser to go elsewhere to perform the request. A redirection response is indicated by a 3XX return code. The Location response header contains a URI for the new or preferred location of the content. Redirects are useful for:

* *Permanently moved resources*

    * A resource might have been moved to a new location, or otherwise renamed, giving it a new URL. The web server can tell the client that the resource has been renamed, and the client can update any bookmarks, etc. before fetching the resource from its new location. The status code 301 Moved Permanently is used for this kind of redirect.

* *Temporarily moved resources*

    * If a resource is temporarily moved or renamed, the server may want to redirect the client to the new location. But, because the renaming is temporary, the server wants the client to come back with the old URL in the future and not to update any bookmarks. The status codes 303 See Other and 307 Temporary Redirect are used for this kind of redirect.

* *URL augmentation*

    * Servers often use redirects to rewrite URLs, often to embed context. When the request arrives, the server generates a new URL containing embedded state information and redirects the user to this new URL.* The client follows the redirect, reissuing the request, but now including the full, state-augmented URL. This is a useful way of maintaining state across transactions. The status codes 303 See Other and 307 Temporary Redirect are used for this kind of redirect.

* *Load balancing*

    * If an overloaded server gets a request, the server can redirect the client to a less heavily loaded server. The status codes 303 See Other and 307 Temporary Redirect are used for this kind of redirect.

* *Server affinity*

    * Web servers may have local information for certain users; a server can redirect the client to a server that contains information about the client. The status codes 303 See Other and 307 Temporary Redirect are used for this kind of redirect.

* *Canonicalizing directory names*

    * When a client requests a URI for a directory name without a trailing slash, most web servers redirect the client to a URI with the slash added, so that relative links work correctly.

## Step 6: Sending Responses

Web servers face similar issues sending data across connections as they do receiving. The server may have many connections to many clients, some idle, some sending data to the server, and some carrying response data back to the clients.

The server needs to keep track of the connection state and handle persistent connections with special care. For nonpersistent connections, the server is expected to close its side of the connection when the entire message is sent.

For persistent connections, the connection may stay open, in which case the server needs to be extra cautious to compute the Content-Length header correctly, or the client will have no way of knowing when a response ends (see Chapter 4).

## Step 7: Logging

Finally, when a transaction is complete, the web server notes an entry into a log file, describing the transaction performed. Most web servers provide several configurable forms of logging. Refer to Chapter 21 for more details

# 6. Proxies

## Web Intermediaries

Web proxy servers are middlemen that fulfill transactions on the client’s behalf. Without a web proxy, HTTP clients talk directly to HTTP servers. With a web proxy, the client instead talks to the proxy, which itself communicates with the server on the client’s behalf. The client still completes the transaction, but through the good services of the proxy server.

HTTP proxy servers are both web servers and web clients. Because HTTP clients send request messages to proxies, the proxy server must properly handle the requests and the connections and return responses, just like a web server. At the same time, the proxy itself sends requests to servers, so it must also behave like a correct HTTP client, sending requests and receiving responses (see Figure 6-1). If you are creating your own HTTP proxy, you’ll need to carefully follow the rules for both HTTP clients and HTTP servers.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_1.PNG)

## Private and Shared Proxies

A proxy server can be dedicated to a single client or shared among many clients. Proxies dedicated to a single client are called private proxies. Proxies shared among numerous clients are called public proxies.

* ***Public proxies***

    * Most proxies are public, shared proxies. It’s more cost effective and easier to administer a centralized proxy. And some proxy applications, such as caching proxy servers, become more useful as more users are funneled into the same proxy server, because they can take advantage of common requests between users.

* ***Private proxies***

    * Dedicated private proxies are not as common, but they do have a place, especially when run directly on the client computer. Some browser assistant products, as well as some ISP services, run small proxies directly on the user’s PC in order to extend browser features, improve performance, or host advertising for free ISP services.

## Proxies Versus Gateways

Strictly speaking, proxies connect two or more applications that speak the same protocol, while gateways hook up two or more parties that speak different protocols. A gateway acts as a “protocol converter,” allowing a client to complete a transaction with a server, even when the client and server speak different protocols.

Figure 6-2 illustrates the difference between proxies and gateways:

* The intermediary device in Figure 6-2a is an HTTP proxy, because the proxy speaks HTTP to both the client and server.

* The intermediary device in Figure 6-2b is an HTTP/POP gateway, because it ties an HTTP frontend to a POP email backend. The gateway converts web transactions into the appropriate POP transactions, to allow the user to read email through HTTP. Web-based email programs such as Yahoo! Mail and MSN Hotmail are HTTP email gateways.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_2.PNG)

In practice, the difference between proxies and gateways is blurry. Because browsers and servers implement different versions of HTTP, proxies often do some amount of protocol conversion. And commercial proxy servers implement gateway functionality to support SSL security protocols, SOCKS firewalls, FTP access, and web-based applications. We’ll talk more about gateways in Chapter 8.

## Why Use Proxies?

Proxy servers can do all kinds of nifty and useful things. They can improve security, enhance performance, and save money. And because proxy servers can see and touch all the passing HTTP traffic, proxies can monitor and modify the traffic to implement many useful value-added web services. Here are examples of just a few of the ways proxies can be used:

* *Child filter* (Figure 6-3)

    * Elementary schools use filtering proxies to block access to adult content, while providing unhindered access to educational sites. As shown in Figure 6-3, the proxy might permit unrestricted access to educational content but forcibly deny access to sites that are inappropriate for children. Several companies and nonprofit organizations provide filtering software and maintain “blacklists” in order to identify and restrict access to objectionable content

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_3.PNG)

* *Document access controller* (Figure 6-4)

    * Proxy servers can be used to implement a uniform access-control strategy across a large set of web servers and web resources and to create an audit trail. This is useful in large corporate settings or other distributed bureaucracies. All the access controls can be configured on the centralized proxy server, without requiring the access controls to be updated frequently on numerous web servers, of different makes and models, administered by different organizations.† In Figure 6-4, the centralized access-control proxy:

* Permits client 1 to access news pages from server A without restriction

* Gives client 2 unrestricted access to Internet content

* Requires a password from client 3 before allowing access to server B

* *Security firewall* (Figure 6-5)

    * Network security engineers often use proxy servers to enhance security. Proxy servers restrict which application-level protocols flow in and out of an organization, at a single secure point in the network. They also can provide hooks to scrutinize that traffic (Figure 6-5), as used by virus-eliminating web and email proxies.



![Figure](ScreenshotsForNotes/Chapter6/Figure_6_4.PNG) ![Figure](ScreenshotsForNotes/Chapter6/Figure_6_5.PNG)

* *Web cache* (Figure 6-6)

    * Proxy caches maintain local copies of popular documents and serve them on demand, reducing slow and costly Internet communication. In Figure 6-6, clients 1 and 2access object A from a nearby web cache, while clients 3 and 4 access the document from the origin server.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_6.PNG)

* *Surrogate* (Figure 6-7)

    * Proxies can masquerade as web servers. These so-called surrogates or reverse proxies receive real web server requests, but, unlike web servers, they may initiate communication with other servers to locate the requested content on demand. Surrogates may be used to improve the performance of slow web servers for common content. In this configuration, the surrogates often are called server accelerators (Figure 6-7). Surrogates also can be used in conjunction with content-routing functionality to create distributed networks of on-demand replicated content.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_7.PNG)

* *Content router* (Figure 6-8)

    * Proxy servers can act as “content routers,” vectoring requests to particular web servers based on Internet traffic conditions and type of content. Content routers also can be used to implement various service-level offerings. For example, content routers can forward requests to nearby replica caches if the user or content provider has paid for higher performance (Figure 6-8), or route HTTP requests through filtering proxies if the user has signed up for a filtering service. Many interesting services can be constructed using adaptive contentrouting proxies.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_8.PNG)

* *Transcoder* (Figure 6-9)

    * Proxy servers can modify the body format of content before delivering it to clients. This transparent translation between data representations is called transcoding.* Transcoding proxies can convert GIF images into JPEG images as they fly by, to reduce size. Images also can be shrunk and reduced in color intensity to be viewable on television sets. Likewise, text files can be compressed, and small text summaries of web pages can be generated for Internet-enabled pagers and smart phones. It’s even possible for proxies to convert documents into foreign languages on the fly! Figure 6-9 shows a transcoding proxy that converts English text into Spanish text and also reformats HTML pages into simpler text that can displayed on the small screen of a mobile phone.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_9.PNG)

* *Anonymizer* (Figure 6-10)

    * Anonymizer proxies provide heightened privacy and anonymity, by actively removing identifying characteristics from HTTP messages (e.g., client IP address, From header, Referer header, cookies, URI session IDs).* In Figure 6-10, the anonymizing proxy makes the following changes to the user’s messages to increase privacy:

* The user’s computer and OS type is removed from the User-Agent header.

* The From header is removed to protect the user’s email address.

* The Referer header is removed to obscure other sites the user has visited.

* The Cookie headers are removed to eliminate profiling and identity data.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_10.PNG)

## Proxy Server Deployment

You can place proxies in all kinds of places, depending on their intended uses. Figure 6-11 sketches a few ways proxy servers can be deployed.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_11.PNG)

* *Egress proxy* (Figure 6-11a)

    * You can stick proxies at the exit points of local networks to control the traffic flow between the local network and the greater Internet. You might use egress proxies in a corporation to offer firewall protection against malicious hackers outside the enterprise or to reduce bandwidth charges and improve performance of Internet traffic. An elementary school might use a filtering egress proxy to prevent precocious students from browsing inappropriate content.

* *Access (ingress) proxy* (Figure 6-11b)

    * Proxies are often placed at ISP access points, processing the aggregate requests from the customers. ISPs use caching proxies to store copies of popular documents, to improve the download speed for their users (especially those with high-speed connections) and reduce Internet bandwidth costs.

* *Surrogates* (Figure 6-11c)

    * Proxies frequently are deployed as surrogates (also commonly called reverse proxies) at the edge of the network, in front of web servers, where they can field all of the requests directed at the web server and ask the web server for resources only when necessary. Surrogates can add security features to web servers or improve performance by placing fast web server caches in front of slower web servers. Surrogates typically assume the name and IP address of the web server directly, so all requests go to the proxy instead of the server.

* *Network exchange proxy* (Figure 6-11d)

    * With sufficient horsepower, proxies can be placed in the Internet peering exchange points between networks, to alleviate congestion at Internet junctions through caching and to monitor traffic flows.

## Proxy Hierarchies

Proxies can be cascaded in chains called proxy hierarchies. In a proxy hierarchy, messages are passed from proxy to proxy until they eventually reach the origin server (and then are passed back through the proxies to the client), as shown in Figure 6-12.

Proxy servers in a proxy hierarchy are assigned parent and child relationships. The next inbound proxy (closer to the server) is called the parent, and the next outbound proxy (closer to the client) is called the child. In Figure 6-12, proxy 1 is the childproxy of proxy 2. Likewise, proxy 2 is the child proxy of proxy 3, and proxy 3 is the parent proxy of proxy 2.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_12.PNG)

## Proxy hierarchy content routing

The proxy hierarchy in Figure 6-12is static—proxy 1 always forwards messages to proxy 2, and proxy 2 always forwards messages to proxy 3. However, hierarchies do not have to be static. A proxy server can forward messages to a varied and changing set of proxy servers and origin servers, based on many factors.

For example, in Figure 6-13, the access proxy routes to parent proxies or origin servers in different circumstances:

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_13.PNG)

* If the requested object belongs to a web server that has paid for content distribution, the proxy could route the request to a nearby cache server that would either return the cached object or fetch it if it wasn’t available.

* If the request was for a particular type of image, the access proxy might route the request to a dedicated compression proxy that would fetch the image and then compress it, so it would download faster across a slow modem to the client.

Here are a few other examples of dynamic parent selection:

* *Load balancing*

    * A child proxy might pick a parent proxy based on the current level of workload on the parents, to spread the load around.

* *Geographic proximity routing*

    * A child proxy might select a parent responsible for the origin server’s geographic region.

* *Protocol/type routing*

    * A child proxy might route to different parents and origin servers based on the URI. Certain types of URIs might cause the requests to be transported through special proxy servers, for special protocol handling.

* *Subscription-based routing*

    * If publishers have paid extra money for high-performance service, their URIs might be routed to large caches or compression engines to improve performance.

Dynamic parenting routing logic is implemented differently in different products, including configuration files, scripting languages, and dynamic executable plug-ins.

## How Proxies Get Traffic

Because clients normally talk directly to web servers, we need to explain how HTTP traffic finds its way to a proxy in the first place. There are four common ways to cause client traffic to get to a proxy:

* *Modify the client*

    * Many web clients, including Netscape and Microsoft browsers, support both manual and automated proxy configuration. If a client is configured to use a proxy server, the client sends HTTP requests directly and intentionally to the proxy, instead of to the origin server (Figure 6-14a).

* *Modify the network*

    * There are several techniques where the network infrastructure intercepts and steers web traffic into a proxy, without the client’s knowledge or participation. This interception typically relies on switching and routing devices that watch for HTTP traffic, intercept it, and shunt the traffic into a proxy, without the client’s knowledge (Figure 6-14b). This is called an intercepting proxy.*

* *Modify the DNS namespace*       * Surrogates, which are proxy servers placed in front of web servers, assume the name and IP address of the web server directly, so all requests go to them instead of to the server (Figure 6-14c). This can be arranged by manually editing the DNS naming tables or by using special dynamic DNS servers that compute the appropriate proxy or server to use on-demand. In some installations, the IP address and name of the real server is changed and the surrogate is given the former address and name.

* *Modify the web server*

    * Some web servers also can be configured to redirect client requests to a proxy by sending an HTTP redirection command (response code 305) back to the client. Upon receiving the redirect, the client transacts with the proxy (Figure 6-14d).

The next section explains how to configure clients to send traffic to proxies. Chapter 20 will explain how to configure the network, DNS, and servers to redirect traffic to proxy servers.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_14.PNG)

## Client Proxy Settings

All modern web browsers let you configure the use of proxies. In fact, many browsers provide multiple ways of configuring proxies, including:

* *Manual configuration*

    * You explicitly set a proxy to use.

* *Browser preconfiguration*

    * The browser vendor or distributor manually preconfigures the proxy setting of the browser (or any other web client) before delivering it to customers.

* *Proxy auto-configuration (PAC)*

    * You provide a URI to a JavaScript proxy auto-configuration (PAC) file; the client fetches the JavaScript file and runs it to decide if it should use a proxy and, if so, which proxy server to use.

* *WPAD proxy discovery*

    * Some browsers support the Web Proxy Autodiscovery Protocol (WPAD), which automatically detects a “configuration server” from which the browser can download an auto-configuration file.

## Client Proxy Configuration: Manual

Many web clients allow you to configure proxies manually. Both Netscape Navigator and Microsoft Internet Explorer have convenient support for proxy configuration.

## Client Proxy Configuration: PAC Files

Manual proxy configuration is simple but inflexible. You can specify only one proxy server for all content, and there is no support for failover. Manual proxy configuration also leads to administrative problems for large organizations. With a large base of configured browsers, it’s difficult or impossible to reconfigure every browser if you need to make changes.

Proxy auto-configuration (PAC) files are a more dynamic solution for proxy configuration, because they are small JavaScript programs that compute proxy settings on the fly. Each time a document is accessed, a JavaScript function selects the proper proxy server.

To use PAC files, configure your browser with the URI of the JavaScript PAC file (configuration is similar to manual configuration, but you provide a URI in an “automatic configuration” box). The browser will fetch the PAC file from this URI and use the JavaScript logic to compute the proper proxy server for each access. PAC files typically have a .pac suffix and the MIME type “application/x-ns-proxy-autoconfig.”

Each PAC file must define a function called FindProxyForURL(url,host) that computes the proper proxy server to use for accessing the URI. The return value of the function can be any of the values in Table 6-1.

![Figure](ScreenshotsForNotes/Chapter6/Table_6_1.PNG)

The PAC file in Example 6-1 mandates one proxy for HTTP transactions, another proxy for FTP transactions, and direct connections for all other kinds of transactions.

```JavaScript
function FindProxyForURL(url, host) {
    if (url.substring(0,5) == "http:") {
        return "PROXY http-proxy.mydomain.com:8080";
    } else if (url.substring(0,4) =="ftp:") {
        return "PROXY ftp-proxy.mydomain.com:8080";
    } else {
        return "DIRECT";
    }
}
```

## Client Proxy Configuration: WPAD

Another mechanism for browser configuration is the Web Proxy Autodiscovery Protocol (WPAD). WPAD is an algorithm that uses an escalating strategy of discovery mechanisms to find the appropriate PAC file for the browser automatically. A client that implements the WPAD protocol will:

* Use WPAD to find the PAC URI.
* Fetch the PAC file given the URI.
* Execute the PAC file to determine the proxy server.
* Use the proxy server for requests.

WPAD uses a series of resource-discovery techniques to determine the proper PAC file. Multiple discovery techniques are used, because not all organizations can use all techniques. WPAD attempts each technique, one by one, until it succeeds.

The current WPAD specification defines the following techniques, in order:

* Dynamic Host Discovery Protocol (DHCP)
* Service Location Protocol (SLP)
* DNS well-known hostnames
* DNS SRV records
* DNS service URIs in TXT records

## Proxy URIs Differ from Server URIs

Web server and web proxy messages have the same syntax, with one exception. The URI in an HTTP request message differs when a client sends the request to a server instead of a proxy.

When a client sends a request to a web server, the request line contains only a partial URI (without a scheme, host, or port), as shown in the following example:

```
GET /index.html HTTP/1.0
User-Agent: SuperBrowserv1.3
```

When a client sends a request to a proxy, however, the request line contains the full URI. For example:

```
GET http://www.marys-antiques.com/index.html HTTP/1.0
User-Agent: SuperBrowser v1.3
```

Why have two different request formats, one for proxies and one for servers? In the original HTTP design, clients talked directly to a single server. Virtual hosting did not exist, and no provision was made for proxies. Because a single server knows its own hostname and port, to avoid sending redundant information, clients sent just the partial URI, without the scheme and host (and port).

When proxies emerged, the partial URIs became a problem. Proxies needed to know the name of the destination server, so they could establish their own connections to the server. And proxy-based gateways needed the scheme of the URI to connect to FTP resources and other schemes. HTTP/1.0 solved the problem by requiring the full URI for proxy requests, but it retained partial URIs for server requests (there were too many servers already deployed to change all of them to support full URIs).

So we need to send partial URIs to servers, and full URIs to proxies. In the case of explicitly configured client proxy settings, the client knows what type of request to issue:

* When the client is not set to use a proxy, it sends the partial URI (Figure 6-15a).
* When the client is set to use a proxy, it sends the full URI (Figure 6-15b).

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_15.PNG)

## The Same Problem with Virtual Hosting

The proxy “missing scheme/host/port” problem is the same problem faced by virtually hosted web servers. Virtually hosted web servers share the same physical web server among many web sites. When a request comes in for the partial URI /index.html, the virtually hosted web server needs to know the hostname of the intended web site (see “Virtually hosted docroots” in Chapter 5 and “Virtual Hosting” in Chapter 18 for more information).

In spite of the problems being similar, they were solved in different ways:

* Explicit proxies solve the problem by requiring a full URI in the request message.
* Virtually hosted web servers require a Host header to carry the host and port information.

## Intercepting Proxies Get Partial URIs

As long as the clients properly implement HTTP, they will send full URIs in requests to explicitly configured proxies. That solves part of the problem, but there’s a catch: a client will not always know it’s talking to a proxy, because some proxies may be invisible to the client. Even if the client is not configured to use a proxy, the client’s traffic still may go through a surrogate or intercepting proxy. In both of these cases, the client will think it’s talking to a web server and won’t send the full URI:

* A surrogate, as described earlier, is a proxy server taking the place of the origin server, usually by assuming its hostname or IP address. It receives the web server request and may serve cached responses or proxy requests to the real server. A client cannot distinguish a surrogate from a web server, so it sends partial URIs (Figure 6-15c).
* An intercepting proxy is a proxy server in the network flow that hijacks traffic from the client to the server and either serves a cached response or proxies it. Because the intercepting proxy hijacks client-to-server traffic, it will receive partial URIs that are sent to web servers (Figure 6-15d). Intercepting proxies also might intercept client-to-proxy traffic in some circumstances, in which case the intercepting proxy might get full URIs and need to handle them. This doesn’t happen often, because explicit proxies normally communicate on a port different from that used by HTTP (usually 8080 instead of 80), and intercepting proxies usually intercept only port 80.

## Proxies can Handle Both Proxy and Server Requests

Because of the different ways that traffic can be redirected into proxy servers, general-purpose proxy servers should support both full URIs and partial URIs in request messages. The proxy should use the full URI if it is an explicit proxy request or use the partial URI and the virtual Host header if it is a web server request.

The rules for using full and partial URIs are:

* If a full URI is provided, the proxy should use it.

* If a partial URI is provided, and a Host header is present, the Host header should be used to determine the origin server name and port number.

* If a partial URI is provided, and there is no Host header, the origin server needs to be determined in some other way:

    * If the proxy is a surrogate, standing in for an origin server, the proxy can be configured with the real server’s address and port number.

    *  If the traffic was intercepted, and the interceptor makes the original IP address and port available, the proxy can use the IP address and port number from the interception technology (see Chapter 20).

    * If all else fails, the proxy doesn’t have enough information to determine the origin server and must return an error message (often suggesting that the user upgrade to a modern browser that supports Host headers). This shouldn’t be done casually. Users will receive cryptic error pages they never got before.

## In-Flight URI Modification

Proxy servers need to be very careful about changing the request URI as they forward messages. Slight changes in the URI, even if they seem benign, may create interoperability problems with downstream servers.

In particular, some proxies have been known to “canonicalize” URIs into a standard form before forwarding them to the next hop. Seemingly benign transformations, such as replacing default HTTP ports with an explicit “:80”, or correcting URIs by replacing illegal reserved characters with their properly escaped substitutions, can cause interoperation problems.

In general, proxy servers should strive to be as tolerant as possible. They should not aim to be “protocol policemen” looking to enforce strict protocol compliance, because this could involve significant disruption of previously functional services.

In particular, the HTTP specifications forbid general intercepting proxies from rewriting the absolute path parts of URIs when forwarding them. The only exception is that they can replace an empty path with “/”.

## URI Client Auto-Expansion and Hostname Resolution

Browsers resolve request URIs differently, depending on whether or not a proxy is present. Without a proxy, the browser takes the URI you type in and tries to find a corresponding IP address. If the hostname is found, the browser tries the corresponding IP addresses until it gets a successful connection.

But if the host isn’t found, many browsers attempt to provide some automatic “expansion” of hostnames, in case you typed in a “shorthand” abbreviation of the host (refer back to “Expandomatic URLs” in Chapter 2):

* Many browsers attempt adding a “www.” prefix and a “.com” suffix, in case you just entered the middle piece of a common web site name (e.g., to let people enter “yahoo” instead of “www.yahoo.com”).

* Some browsers even pass your unresolvable URI to a third-party site, which attempts to correct spelling mistakes and suggest URIs you may have intended.

* In addition, the DNS configuration on most systems allows you to enter just the prefix of the hostname, and the DNS automatically searches the domain. If you are in the domain “oreilly.com” and type in the hostname “host7,” the DNS automatically attempts to match “host7.oreilly.com”. It’s not a complete, valid hostname.

## URI Resolution Without a Proxy

Figure 6-16 shows an example of browser hostname auto-expansion without a proxy. In steps 2a–3c, the browser looks up variations of the hostname until a valid hostname is found.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_16.PNG)

Here’s what’s going on in this figure:

* In Step 1, the user types “oreilly” into the browser’s URI window. The browser uses “oreilly” as the hostname and assumes a default scheme of “http://”, a default port of “80”, and a default path of “/”.

* In Step 2a, the browser looks up host “oreilly.” This fails.

* In Step 3a, the browser auto-expands the hostname and asks the DNS to resolve “www.oreilly.com.” This is successful.

* The browser then successfully connects to www.oreilly.com.

## URI Resolution with an Explicit Proxy

When you use an explicit proxy the browser no longer performs any of these convenience expansions, because the user’s URI is passed directly to the proxy.

As shown in Figure 6-17, the browser does not auto-expand the partial hostname when there is an explicit proxy. As a result, when the user types “oreilly” into the browser’s location window, the proxy is sent “http://oreilly/” (the browser adds the default scheme and path but leaves the hostname as entered).

For this reason, some proxies attempt to mimic as much as possible of the browser’s convenience services as they can, including “www...com” auto-expansion and addition of local domain suffixes. But, for widely shared proxies, it may be impossible to know the proper domain suffix for individual users.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_17.PNG)

## URI Resolution with an Intercepting Proxy

Hostname resolution is a little different with an invisible intercepting proxy, because as far as the client is concerned, there is no proxy! The behavior proceeds much like the server case, with the browser auto-expanding hostnames until DNS success. But a significant difference occurs when the connection to the server is made, as Figure 6-18 illustrates.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_18.PNG)

Figure 6-18 demonstrates the following transaction:

* In Step 1, the user types “oreilly” into the browser’s URI location window.

* In Step 2a, the browser looks up the host “oreilly” via DNS, but the DNS server fails and responds that the host is unknown, as shown in Step 2b.

* In Step 3a, the browser does auto-expansion, converting “oreilly” into “www. oreilly.com.” In Step 3b, the browser looks up the host “www.oreilly.com” via DNS. This time, as shown in Step 3c, the DNS server is successful and returns IP addresses back to the browser.

* In Step 4a, the client already has successfully resolved the hostname and has a list of IP addresses. Normally, the client tries to connect to each IP address until it succeeds, because some of the IP addresses may be dead. But with an intercepting proxy, the first connection attempt is terminated by the proxy server, not the origin server. The client believes it is successfully talking to the web server, but the web server might not even be alive.

* When the proxy finally is ready to interact with the real origin server (Step 5b), the proxy may find that the IP address actually points to a down server. To provide the same level of fault tolerance provided by the browser, the proxy needs to try other IP addresses, either by reresolving the hostname in the Host header or by doing a reverse DNS lookup on the IP address. It is important that both intercepting and explicit proxy implementations support fault tolerance on DNS resolution to dead servers, because when browsers are configured to use an explicit proxy, they rely on the proxy for fault tolerance.

## Tracing Messages

Today, it’s not uncommon for web requests to go through a chain of two or more proxies on their way from the client to the server (Figure 6-19). For example, many corporations use caching proxy servers to access the Internet, for security and cost savings, and many large ISPs use proxy caches to improve performance and implement features. A significant percentage of web requests today go through proxies. At the same time, it’s becoming increasingly popular to replicate content on banks of surrogate caches scattered around the globe, for performance reasons.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_19.PNG)

Proxies are developed by different vendors. They have different features and bugs and are administrated by various organizations.

As proxies become more prevalent, you need to be able to trace the flow of messages across proxies and to detect any problems, just as it is important to trace the flow of IP packets across different switches and routers.

## The Via Header

The Via header field lists information about each intermediate node (proxy or gateway) through which a message passes. Each time a message goes through another node, the intermediate node must be added to the end of the Via list.

The following Via string tells us that the message traveled through two proxies. It indicates that the first proxy implemented the HTTP/1.1 protocol and was called proxy-62.irenes-isp.net, and that the second proxy implemented HTTP/1.0 and was called cache.joes-hardware.com:

```Via: 1.1 proxy-62.irenes-isp.net, 1.0 cache.joes-hardware.com```

The Via header field is used to track the forwarding of messages, diagnose message loops, and identify the protocol capabilities of all senders along the request/response chain (Figure 6-20).

Proxies also can use Via headers to detect routing loops in the network. A proxy should insert a unique string associated with itself in the Via header before sending out a request and should check for the presence of this string in incoming requests to detect routing loops in the network.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_20.PNG)

## Via Syntax

The Via header field contains a comma-separated list of waypoints. Each waypoint represents an individual proxy server or gateway hop and contains information about the protocol and address of that intermediate node. Here is an example of a Via header with two waypoints:

```Via = 1.1 cache.joes-hardware.com, 1.1 proxy.irenes-isp.net```

The formal syntax for a Via header is shown here:

![Figure](ScreenshotsForNotes/Chapter6/ViaSyntax.PNG)

Note that each Via waypoint contains up to four components: an optional protocol name (defaults to HTTP), a required protocol version, a required node name, and an optional descriptive comment:

* *Protocol name*

    * The protocol received by an intermediary. The protocol name is optional if the protocol is HTTP. Otherwise, the protocol name is prepended to the version, separated by a “/”. Non-HTTP protocols can occur when gateways connect HTTP requests for other protocols (HTTPS, FTP, etc.).

* *Protocol version*

    * The version of the message received. The format of the version depends on the protocol. For HTTP, the standard version numbers are used (“1.0”, “1.1”, etc.). The version is included in the Via field, so later applications will know the protocol capabilities of all previous intermediaries.

* *Node name*

    * The host and optional port number of the intermediary (if the port isn’t included, you can assume the default port for the protocol). In some cases an organization might not want to give out the real hostname, for privacy reasons, in which case it may be replaced by a pseudonym.

* *Node comment*

    * An optional comment that further describes the intermediary node. It’s common to include vendor and version information here, and some proxy servers also use the comment field to include diagnostic information about the events that occurred on that device. For example, caching proxy servers may include hit/miss information.

## Via request and response paths

Both request and response messages pass through proxies, so both request and response messages have Via headers.

Because requests and responses usually travel over the same TCP connection, response messages travel backward across the same path as the requests. If a request message goes through proxies A, B, and C, the corresponding response message travels through proxies C, B, then A. So, the Via header for responses is almost always the reverse of the Via header for responses (Figure 6-21).

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_21.PNG)

## Via and gateways

Some proxies provide gateway functionality to servers that speak non-HTTP protocols. The Via header records these protocol conversions, so HTTP applications can be aware of protocol capabilities and conversions along the proxy chain. Figure 6-22 shows an HTTP client requesting an FTP URI through an HTTP/FTP gateway.

The client sends an HTTP request for ftp://http-guide.com/pub/welcome.txt to the gateway proxy.irenes-isp.net. The proxy, acting as a protocol gateway, retrieves the desired object from the FTP server, using the FTP protocol. The proxy then sends the object back to the client in an HTTP response, with this Via header field:

```Via: FTP/1.0 proxy.irenes-isp.net (Traffic-Server/5.0.1-17882 [cMs f ])```

Notice the received protocol is FTP. The optional comment contains the brand and version number of the proxy server and some vendor diagnostic information. You can read all about gateways in Chapter 8.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_22.PNG)

## The Server and Via headers

The Server response header field describes the software used by the origin server. Here are a few examples:

```

Server: Apache/1.3.14 (Unix) PHP/4.0.4

Server: Netscape-Enterprise/4.1

Server: Microsoft-IIS/5.0

```

If a response message is being forwarded through a proxy, make sure the proxy does not modify the Server header. The Server header is meant for the origin server. Instead, the proxy should add a Via entry.

## Privacy and security implications of Via

There are some cases when we want don’t want exact hostnames in the Via string. In general, unless this behavior is explicitly enabled, when a proxy server is part of a network firewall it should not forward the names and ports of hosts behind the firewall, because knowledge of network architecture behind a firewall might be of use to a malicious party. Malicious people can use the names of computers and version numbers to learn about the network architecture behind a security perimeter. This information might be helpful in security attacks. In addition, the names of computers might be clues to private projects within an organization.

If Via node-name forwarding is not enabled, proxies that are part of a security perimeter should replace the hostname with an appropriate pseudonym for that host. Generally, though, proxies should try to retain a Via waypoint entry for each proxy server, even if the real name is obscured.

For organizations that have very strong privacy requirements for obscuring the design and topology of internal network architectures, a proxy may combine an ordered sequence of Via waypoint entries (with identical received-protocol values) into a single, joined entry. For example:

```Via: 1.0 foo, 1.1 devirus.company.com, 1.1 access-logger.company.com```

could be collapsed to:

```Via: 1.0 foo, 1.1 concealed-stuff```

Don’t combine multiple entries unless they all are under the same organizational control and the hosts already have been replaced by pseudonyms. Also, don’t combine entries that have different received-protocol values.

## The TRACE method

Proxy servers can change messages as the messages are forwarded. Headers are added, modified, and removed, and bodies can be converted to different formats. As proxies become more sophisticated, and more vendors deploy proxy products, interoperability problems increase. To easily diagnose proxy networks, we need a way to conveniently watch how messages change as they are forwarded, hop by hop, through the HTTP proxy network.

HTTP/1.1’s TRACE method lets you trace a request message through a chain of proxies, observing what proxies the message passes through and how each proxy modifies the request message. TRACE is very useful for debugging proxy flows.*

When the TRACE request reaches the destination server,† the entire request message is reflected back to the sender, bundled up in the body of an HTTP response (see Figure 6-23). When the TRACE response arrives, the client can examine the exact message the server received and the list of proxies through which it passed (in the Via header). The TRACE response has Content-Type message/http and a 200 OK status.

## Max-Forwards

Normally, TRACE messages travel all the way to the destination server, regardless of the number of intervening proxies. You can use the Max-Forwards header to limit the number of proxy hops for TRACE and OPTIONS requests, which is useful for testing a chain of proxies forwarding messages in an infinite loop or for checking the effects of particular proxy servers in the middle of a chain. Max-Forwards also limits the forwarding of OPTIONS messages (see “Proxy Interoperation”).

The Max-Forwards request header field contains a single integer indicating the remaining number of times this request message may be forwarded (Figure 6-24). If the Max-Forwards value is zero (Max-Forwards: 0), the receiver must reflect the TRACE message back toward the client without forwarding it further, even if the receiver is not the origin server.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_23.PNG)

If the received Max-Forwards value is greater than zero, the forwarded message must contain an updated Max-Forwards field with a value decremented by one. All proxies and gateways should support Max-Forwards. You can use Max-Forwards to view the request at any hop in a proxy chain.

## Proxy Authentication

Proxies can serve as access-control devices. HTTP defines a mechanism called proxy authentication that blocks requests for content until the user provides valid accesspermission credentials to the proxy:

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_24.PNG)

* When a request for restricted content arrives at a proxy server, the proxy server can return a 407 Proxy Authorization Required status code demanding access credentials, accompanied by a Proxy-Authenticate header field that describes how to provide those credentials (Figure 6-25b).

* When the client receives the 407 response, it attempts to gather the required credentials, either from a local database or by prompting the user.

* Once the credentials are obtained, the client resends the request, providing the required credentials in a Proxy-Authorization header field.

* If the credentials are valid, the proxy passes the original request along the chain (Figure 6-25c); otherwise, another 407 reply is sent.

Proxy authentication generally does not work well when there are multiple proxies in a chain, each participating in authentication. People have proposed enhancements to HTTP to associate authentication credentials with particular waypoints in a proxy chain, but those enhancements have not been widely implemented.

## Proxy Interoperation

Clients, servers, and proxies are built by multiple vendors, to different versions of the HTTP specification. They support various features and have different bugs. Proxy servers need to intermediate between client-side and server-side devices, which may implement different protocols and have troublesome quirks.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_25.PNG)

## Handling Unsupported Headers and Methods

The proxy server may not understand all the header fields that pass through it. Some headers may be newer than the proxy itself; others may be customized header fields unique to a particular application. Proxies must forward unrecognized header fields and must maintain the relative order of header fields with the same name.* Similarly, if a proxy is unfamiliar with a method, it should try to forward the message to the next hop, if possible.

Proxies that cannot tunnel unsupported methods may not be viable in most networks today, because Hotmail access through Microsoft Outlook makes extensive use of HTTP extension methods.

## OPTIONS: Discovering Optional Feature Support

The HTTP OPTIONS method lets a client (or proxy) discover the supported functionality (for example, supported methods) of a web server or of a particular resource on a web server (Figure 6-26). Clients can use OPTIONS to determine a server’s capabilities before interacting with the server, making it easier to interoperate with proxies and servers of different feature levels.

![Figure](ScreenshotsForNotes/Chapter6/Figure_6_26.PNG)

If the URI of the OPTIONS request is an asterisk (*), the request pertains to the entire server’s supported functionality. For example:

```OPTIONS * HTTP/1.1```

If the URI is a real resource, the OPTIONS request inquires about the features available to that particular resource:

```OPTIONS http://www.joes-hardware.com/index.html HTTP/1.1```

On success, the OPTIONS method returns a 200 OK response that includes various header fields that describe optional features that are supported on the server or available to the resource. The only header field that HTTP/1.1 specifies in the response is the Allow header, which describes what methods are supported by the server (or particular resource on the server).* OPTIONS allows an optional response body with more information, but this is undefined.

## The Allow Header

The Allow entity header field lists the set of methods supported by the resource identified by the request URI, or the entire server if the request URI is *. For example:

```Allow: GET, HEAD, PUT``` 

The Allow header can be used as a request header to recommend the methods to be supported by the new resource. The server is not required to support these methods and should include an Allow header in the matching response, listing the actual supported methods.

A proxy can’t modify the Allow header field even if it does not understand all the methods specified, because the client might have other paths to talk to the origin server.



