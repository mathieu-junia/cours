---
marp: true
theme: gaia
markdown.marp.enableHtml: true
paginate: true
footer: ISEN
---

<style>

section {
  background-color: #fefefe;
  color: #333;
}

img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
blockquote {
  background: #ffedcc;
  border-left: 10px solid #d1bf9d;
  margin: 1.5em 10px;
  padding: 0.5em 10px;
}
blockquote:before{
  content: unset;
}
blockquote:after{
  content: unset;
}
</style>

<!-- _class: lead -->


# REST APIs

---

# What is a REST API ?

At its core, a REST API (**Re**presentational **S**tate **T**ransfer **A**pplication **P**rogramming **I**nterface) is a set of rules and guidelines for building web services that allow different software applications to communicate and exchange data over the internet.

---

# What is a REST API ?

Roy Fielding first presented it in 2000 in his PhD dissertation. Since then it has become one of the most widely used approaches for building web-based APIs (Application Programming Interfaces).

REST is not a protocol or a standard, it is an architectural style. During the development phase, API developers can implement REST in a variety of ways.

Like the other architectural styles, REST also has its guiding principles and constraints. These principles must be satisfied if a service interface has to be referred to as RESTful.

---

# Think of it like this

  * **It's a bridge**: REST APIs act as bridges between different software systems. Imagine you have two separate applications, like a mobile app and a database. The REST API allows these two applications to "talk" to each other and share information.
  * **It follows specific rules**: These rules, or architectural constraints, guide how the API should behave. This ensures consistency, making it easier for developers to understand and use.
  * **It uses HTTP**: REST APIs primarily rely on the Hypertext Transfer Protocol (HTTP), the same protocol used for browsing websites. This makes them widely compatible and easy to implement.

---

# Key Characteristics of a REST API

 * **Client-Server Architecture**: It's a two-way communication system where a client (like a mobile app) requests data from a server (where the data resides).
 * **Statelessness**: Each request from the client must contain all the necessary information for the server to understand and process it. The server doesn't retain any information about previous requests from the same client.

---

# Key Characteristics of a REST API

 * **Cacheability**: Responses from the server can be cached (temporarily stored) to improve performance and reduce server load.
 * **Uniform Interface**: REST APIs use standard methods (like GET, POST, PUT, DELETE) and data formats (like JSON) to ensure consistent communication.

---

# Why are REST APIs so popular?

* **Simplicity**: They are relatively easy to understand and implement compared to other API styles.
* **Flexibility**: They can be used with various programming languages and platforms.
* **Scalability**: They can easily handle a large number of requests, making them suitable for high-traffic applications.
* **Efficiency**: They often provide faster response times due to their stateless nature and caching capabilities.

---

# Popular frameworks

* **JS**: Express.js, NestJS
* **Go**: Gin, Echo
* **Rust**: Actix Web, Rocket, Axum
* **Python**: FastAPI, Django, Flask

---

# The 6 contraints of a REST API

1. Uniform Interface

The uniform interface constraint defines the interface between clients and servers. It simplifies and decouples the architecture, which enables each part to evolve independently. The four guiding principles of the uniform interface are:

---

# The 6 contraints of a REST API

**Resource-Based**

Individual resources are identified in requests using URIs as resource identifiers. The resources themselves are conceptually separate from the representations that are returned to the client. For example, the server does not send its database, but rather, some HTML, XML or JSON that represents some database records expressed, depending on the details of the request and the server implementation.

---

# The 6 contraints of a REST API

**Manipulation of Resources Through Representations**

When a client holds a representation of a resource, including any metadata attached, it has enough information to modify or delete the resource on the server, provided it has permission to do so.

**Self-descriptive Messages**

Each message includes enough information to describe how to process the message. For example, which parser to invoke may be specified by an Internet media type (previously known as a MIME type). Responses also explicitly indicate their cache-ability.

---

# The 6 contraints of a REST API

**Stateless**

As REST is an acronym for REpresentational State Transfer, statelessness is key. Essentially, what this means is that **the necessary state to handle the request is contained within the request itself**, whether as part of the URI, query-string parameters, body, or headers. The URI uniquely identifies the resource and the body contains the state (or state change) of that resource. Then after the server does its processing, the appropriate state, or the piece(s) of state that matter, are communicated back to the client via headers, status and response body.

---

# The 6 contraints of a REST API

**Cacheable**

As on the World Wide Web, clients can cache responses. Responses must therefore, implicitly or explicitly, define themselves as cacheable, or not, to prevent clients reusing stale or inappropriate data in response to further requests. Well-managed caching partially or completely eliminates some client–server interactions, further improving scalability and performance.

---

# The 6 contraints of a REST API

**Client-Server**

The uniform interface separates clients from servers. This separation of concerns means that, for example, clients are not concerned with data storage, which remains internal to each server, so that the portability of client code is improved. Servers are not concerned with the user interface or user state, so that servers can be simpler and more scalable. Servers and clients may also be replaced and developed independently, as long as the interface is not altered.

---

# The 6 contraints of a REST API

**Layered System**

A client cannot ordinarily tell whether it is connected directly to the end server, or to an intermediary along the way. Intermediary servers may improve system scalability by enabling load-balancing and by providing shared caches. Layers may also enforce security policies.

---

# HTTP Methods

| Method | Description                                                                                           |
| ------ | ----------------------------------------------------------------------------------------------------- |
| GET    | Read a specific resource (by an identifier) or a collection of resources.                             |
| POST   | Create a new resource. Also a catch-all verb for operations that don’t fit into the other categories. |
| DELETE | Remove/delete a specific resource by an identifier.                                                   |

---

# HTTP Methods

| Method | Description                                                                                                                                                                  |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PUT    | Replace a specific resource (by an identifier) or a collection of resources. Can also be used to create a specific resource if the resource identifier is known before-hand. |
| PATCH  | Update a specific resource (by an identifier) or a collection of resources. This can be thought of in some ways as a ‘partial update’ vs the replace that PUT performs.      |

---

# Resource Names

* Use identifiers in your URLs instead of in the query-string. Using URL query-string parameters is for filtering, but not for resource names.
    * Good: /users/12345
    * Poor: /api?type=user&id=23
* Leverage the hierarchical nature of the URL to imply structure.
* Resource names should be nouns.

---

# Resource Names

* Use plurals.
    * Recommended: /customers/33245/orders/8769/lineitems/1
    * Not: /customer/33245/order/8769/lineitem/1
* Use lower-case in URL segments, separating words with underscores (’_’) or hyphens (’-’). Some servers ignore case so it’s best to be clear.
* Keep URLs as short as possible, with as few segments as makes sense.

---

# HTTP Response Codes

Response status codes are part of the HTTP specification.

| Status Code | Description                                                                                                                                                                                |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 200 OK      | General success status code. This is the most common code. Used to indicate success.                                                                                                       |
| 201 CREATED | Successful creation occurred (via either POST or PUT). Set the Location header to contain a link to the newly-created resource (on POST). Response body content may or may not be present. |

---


# HTTP Response Codes

Response status codes are part of the HTTP specification.

| Status Code      | Description                                                                                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 401 UNAUTHORIZED | Error code response for missing or invalid authentication token.                                                                                            |
| 404 NOT FOUND    | Used when the requested resource is not found, whether it doesn’t exist or if there was a 401 or 403 that, for security reasons, the service wants to mask. |

---

# Idempotence

---

# Idempotence



From a RESTful service standpoint, for an operation to be idempotent, clients can make that same call repeatedly while producing the same result. In other words, **making multiple identical requests has the same effect as making a single request**.

The PUT and DELETE methods are defined to be idempotent.