# Java Servlet notes

These notes are taken from servlet specification 3.1 document. 
- [Servlet 3.1 specification](http://download.oracle.com/otndocs/jcp/servlet-3_1-fr-eval-spec/index.html)
- [Java EE 7 reference API](https://docs.oracle.com/javaee/7/api/)
- [Tomcat Architecture 7.0](http://tomcat.apache.org/tomcat-7.0-doc/architecture/)
- [Tomcat request flow UML](http://tomcat.apache.org/tomcat-7.0-doc/architecture/requestProcess/request-process.png)
- [JAX-RS](http://download.oracle.com/otndocs/jcp/jaxrs-2_0-fr-eval-spec/index.html) JAX-RS is a specification for writing restful web services or RESTful resources. Read the specification for the goals and differences. It is part of JAVA EE and package javax.ws.rs provides the API.

## Overview
 
Servlet is a Java Web Component, that specifies on how to communicate in a client server architecture. The most common servlet is HttpServet that uses HTTP protocol to communicate. Servlet class arr compiled into platform independent byte code and are managed by servlet containers. Servlet can contain Java code that embed HTML or JSP where Java code is embedded in HTML. The latter is used more commonly.

Servlets are managed by servlet engines. Servlet engines are also known as web servers. Tomcat is the most popular servlet engine. Servlel container manages the servlet lifecycle.

#### What is Servlet interface?
A servlet is a JavaTM technology-based Web component, managed by a container,
that generates dynamic content. Like other Java technology-based components,
servlets are platform-independent Java classes that are compiled to platform-neutral
byte code that can be loaded dynamically into and run by a Java technology-enabled
Web server. Containers, sometimes called servlet engines, are Web server extensions
that provide servlet functionality. Servlets interact with Web clients via a request/
response paradigm implemented by the servlet container. 

Apache Tomcat version 7.0 implements the Servlet 3.0 and JavaServer Pages 2.2 specifications from the Java Community Process, and includes many additional features that make it a useful platform for developing and deploying web applications and web services.

#### What is Servlet Container?
The servlet container is a part of a Web server or application server that provides the
network services over which requests and responses are sent, decodes MIME-based
requests, and formats MIME-based responses. A servlet container also contains and
manages servlets through their lifecycle.

A servlet container can be built into a host Web server, or installed as an addon
component to a Web Server via that server’s native extension API. Servlet containers
can also be built into or possibly installed into Web-enabled application
servers.

All servlet containers must support HTTP as a protocol for requests and
responses, but additional request/response-based protocols such as HTTPS (HTTP
over SSL) may be supported. The required versions of the HTTP specification that
a container must implement are HTTP/1.0 and HTTP/1.1. 

#### An Example
The following is a typical sequence of events:
- A client (e.g., a Web browser) accesses a Web server and makes an HTTP request.
- The request is received by the Web server and handed off to the servlet container.
The servlet container can be running in the same process as the host Web server,
in a different process on the same host, or on a different host from the Web server
for which it processes requests.
- The servlet container determines which servlet to invoke based on the
configuration of its servlets, and calls it with objects representing the request and
response.
- The servlet uses the request object to find out who the remote user is, what HTTP
POST parameters may have been sent as part of this request, and other relevant
data. The servlet performs whatever logic it was programmed with, and generates
data to send back to the client. It sends this data back to the client via the
response object.
- Once the servlet has finished processing the request, the servlet container ensures
that the response is properly flushed, and returns control back to the host Web
server.

## The Servlet Interface
The Servlet interface is the central abstraction of the Java Servlet API. All servlets
implement this interface either directly, or more commonly, by extending a class that
implements the interface. The two classes in the Java Servlet API that implement the
Servlet interface are GenericServlet and HttpServlet. For most purposes,
Developers will extend HttpServlet to implement their servlets.

Read the HttpServlet implementation from tomcat repository.

#### Servlet Life Cycle
A servlet is managed through a well defined life cycle that defines how it is loaded
and instantiated, is initialized, handles requests from clients, and is taken out of
service. This life cycle is expressed in the API by the init, service, and destroy
methods of the javax.servlet.Servlet interface that all servlets must implement
directly or indirectly through the GenericServlet or HttpServlet abstract classes.

##### Loading
Servets are loaded dynamically by the servlet container. When the servlet engine starts, servlet container locates all the servlets and using java loader loads all the servlets. After the loading is completed, it is initialized.

##### Initialization
Servlets ojects are loaded into servlet container. Once the loading is completed, init method is called to initialize expensive properties and to load one-time activities. ServletConfig is used for this purpose. ServletConfig object is one per servlet class. This object also provides access to name-value parameters and also to ServletContext object for the run time environment.

##### Destroy
Upon exceptions in initialization, destroy method is called to destry the servlet. Also, when container chooses to stop the web server, destroy method is called to release all expensive resources.

## The Request

.. TODO complete the document.
