# NodeJs Restful Web API

## 第一章 关于REST

### 什么是 Rest

Rest 是 Representational State Transfer 的缩写——表征状态转移。是Roy Fielding博士在2000年他的博士论文中提出来的一种软件架构风格。它是一种针对网络应用的设计和开发方式，可以降低开发的复杂性，提高系统的可伸缩性。 

表征状态转移。是一组架构约束条件和原则。满足这些约束条件和原则的应用程序或设计就是RESTful。需要注意的是，REST是设计风格而不是标准。REST通常基于使用HTTP，URI，和XML（标准通用标记语言下的一个子集）以及HTML（标准通用标记语言下的一个应用）这些现有的广泛流行的协议和标准。 
REST 定义了一组体系架构原则，您可以根据这些原则设计以系统资源为中心的 Web 服务，包括使用不同语言编写的客户端如何通过 HTTP 处理和传输资源状态。 如果考虑使用它的 Web 服务的数量，REST 近年来已经成为最主要的 Web 服务设计模式。 事实上，REST 对 Web 的影响非常大，由于其使用相当方便，已经普遍地取代了基于 SOAP 和 WSDL 的接口设计。 

*Nowadays, topics such as cloud computing and mobile device service feeds, as well as other data sources driven by cutting-edge, scalable, stateless, and modern technologies such as RESTful web services, leave the impression that REST was invented recently. Well, to be honest, it definitely was not! In fact, REST has been here since the end of the 20th century.*

如今，诸如云计算和移动设备服务源之类的主题以及其他数据源由前端，可扩展，无状态和现代技术（如RESTful Web服务）驱动，给人留下了最近发明REST的印象。 那么说实话，绝对不是！ 事实上，自20世纪末以来，REST一直在这里。

*This chapter will walk you through REST's fundamental principles, and it will explain how REST couples with the HTTP protocol. You will look into the five key principles that need to be considered while turning an HTTP application into a RESTful-service-enabled application. You will also look at the differences in describing RESTful and classic SOAP-based web services. Finally, you will learn how to utilize already existing infrastructure for your benefit.*

本章将介绍REST的基本原则，并介绍如何将REST与Http协议相结合。你会看到由Http应用转向REST提服务所考虑遵循的5个关键原则，你还将看到RESTful与典型的以SOUAP为基础的web服务的差异性。最后，你会学习怎样利用已经存在的基础资源为你所用

*In this chapter, we will cover the following topics:*

*REST fundamentals*
*REST with HTTP*
*Essential differences in the description and discovery of RESTful servicescomhpared to classical SOAP-based services*
*Taking advantage of existing infrastructure*

本章，我们将介绍以下主题：

REST 基础、REST 与HTTP、 RESTful服务的描述和发现与传统的基于SOAP的服务的基本差异、了解利用现有基础设施的优点

*REST fundamentals*

*It actually happened back in 1999, when a request for comments was submitted to the Internet Engineering Task Force (IETF: http://www.ietf.org/) via RFC 2616:“Hypertext Transfer Protocol-HTTP/1.1.” One of its authors, Roy Fielding, later defined a set of principles built around the HTTP and URI standards. This gave birth to REST as we know it today.*

REST 基础
实际上是在1999年，当通过RFC 2616向互联网工程任务组（IETF：http：//www.ietf.org/）提交了意见征求意见时，其实际上是“超文本传输协议-HTTP / 1.1”。 其作者Roy Fielding后来定义了围绕HTTP和URI标准构建的一套原则。 我们今天知道这产生了REST。
这些定义在Fielding的论文“表征状态转移（REST）”的第5章，“建筑风格”和基于网络的软件架构的“设计”中给出。 
*(论文仍可在http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_a rch_style.htm获得。)*

*Let's look at the key principles around the HTTP and URI standards, sticking to which will make your HTTP application a RESTful-service-enabled application:*

*Everything is a resource*
*Each resource is identifiable by a unique identifier (URI)*
*Use the standard HTTP methods*
*Resources can have multiple representations*
*Communicate statelessly*

我们来看看关于HTTP和URI标准的关键原则，坚持使你的HTTP应用成为启用RESTful的应用程序：

*一切都是资源、所有资源都可以通过唯一标识符（URI）来标识*
*使用标准的HTTP方法*
*资源能多个表现形式*			
*沟通无国界*

*Principle 1 – everything is a resource*

*To understand this principle, one must conceive the idea of representing data by a specificformat and not by a physical file. Each piece of data available on the Internet has a formatthat could be described by a content type. For example, JPEG images; MPEG videos; HTML,XML, and text documents; and binary data are all resources with the following contenttypes: image/jpeg, video/mpeg, text/html, text/xml, and application/octet-stream.*

原则1-万物皆资源

为了理解这个原则，人们必须设想一种通过特定格式而不是物理文件来表示数据的想法。 互联网上可用的每个数据都可以通过内容类型来描述。 例如，JPEG图像; MPEG视频; HTML，XML和文本文档; 二进制数据都是具有以下内容类型的资源：image / jpeg，video / mpeg，text / html，text / xml和application / octet-stream。		

*Principle 2 – each resource is identifiable by aunique identifier*

*Since the Internet contains so many different resources, they all should be accessible viaURIs and should be identified uniquely. Furthermore, the URIs can be in a human-readableformat, despite the fact that their consumers are more likely to be software programs ratherthan ordinary humans.*

*Human-readable URIs keep data self-descriptive and ease further development against it.This helps you to reduce the risk of logical errors in your programs to a minimum.*

*Here are a few sample examples of such URIs:*

```
        http://www.mydatastore.com/images/vacation/2014/summer
        http://www.mydatastore.com/videos/vacation/2014/winter
        http://www.mydatastore.com/data/documents/balance?format=xml
        http://www.mydatastore.com/data/archives/2014
```

*These human-readable URIs expose different types of resources in a straightforward manner. In the example, it is quite clear that the media types of these resources are asfollows:*

*Images*
*Videos*
*XML documents*
*Some kinds of binary archive documents*

原则2-所有资源都可以通过唯一标识符（URI）来标识

由于互联网包含如此多的不同资源，所有这些资源都可以通过浏览器访问，应该被唯一标识。 此外，URI可以是人类可读格式，尽管事实上，他们的消费者更可能是普通人的软件程序。

保持URIs的可读性，使开发更容易，降低风险错误。

这有几个例子

```
http://www.mydatastore.com/images/vacation/2014/summer
http://www.mydatastore.com/videos/vacation/2014/winter
http://www.mydatastore.com/data/documents/balance?format=xml
http://www.mydatastore.com/data/archives/2014
```

这些可读性的链接比较直观的展示了资源的不同。在这个例子中，十分清晰展示了下列几种媒体资源

```
Images
Videos
XML documents
一些二进制存档文件
```

Principle 3 – use the standard HTTP methods

The native HTTP protocol (RFC 2616) defines eight actions, also known as HTTP verbs:

```
GET
POST
PUT
DELETE
HEAD
OPTIONS
TRACE
CONNECT
```

The first four of them feel just natural in the context of resources, especially when defining actions for resource data manipulation. Let's make a parallel with relative SQL databases where the native language for data manipulation is CRUD (short for Create, Read, Update, and Delete) originating from the different types of SQL statements: INSERT, SELECT, UPDATE, and DELETE, respectively. In the same manner, if you apply the REST principles correctly, the HTTP verbs should be used as shown here:

| HTTP verb | Action                                   | Response status code                     |
| --------- | ---------------------------------------- | ---------------------------------------- |
| GET       | Requests an existing resource            | "200 OK" if the resource exists, “404 Not Found” if it does not exist, and “500 Internal Server Error” for other errors |
| PUT       | Updates a resource or creates it as an identifier provided from the client | "201 CREATED" if a new resource is created,"200 OK" if updated,adn "500 Internal Server Error" for other errors |
| POST      | Creates a resource with an identifier generated at server side or updates a resource with an existing identifier provided from the client | “201 CREATED” if a new resource is created,”200 OK” if the resource has been updated successfully, “404 Not Found” if the resource to be updated does not exist, and “500 Internal Server Error” for other errors |
| DELETE    | Deletes a resource                       | “200 OK“or “204 No Content” if the resource has been deleted successfully, “404 Not Found” if the resource to be deleted does not exist, and “500 Internal Server Error” for other errors |

Note that a resource can be created by either of POST or PUT HTTP verbs. When a resource has to be created under a specific URI with an identifier provided by the client, then PUT is the appropriate action:
PUT /data/documents/balance/22082014 HTTP/1.1 Content-Type: text/xml Host: www.mydatastore.com
<?xml version="1.0" encoding="utf-8"?>
<balance date="22082014">
<Item>Sample item</Item>
<price currency="EUR">100</price>
</balance>

HTTP/1.1 201 Created Content-Type: text/xml Location: /data/documents/balance/22082014 

However, in your application, you may want to leave it up to the server REST application to decide where to place the newly created resource, and thus create it under an appropriate but still unknown or non-existing location. For instance, in our example, we might want the server to create the date part of the URI based on the current date. In such cases, it is perfectly fine to use the POST verb to the main resource URI and let the server respond with the location of the newly created resource:
POST /data/documents/balance HTTP/1.1 Content-Type: text/xml Host: www.mydatastore.com
<?xml version="1.0" encoding="utf-8"?>
<balance date="22082014">
<Item>Sample item</Item>
<price currency="EUR">100</price>
</balance>
HTTP/1.1 201 Created Content-Type: text/xml Location: /data/documents/balance



原则3-使用标准的HTTP方法

本地HTTP协议（RFC 2616）定义了八种请求方式：

```
GET
POST
PUT
DELETE
HEAD
OPTIONS
TRACE
```

前四个人在资源的背景下感到自然，特别是在定义资源数据操作的动作时。 让我们与相关的SQL数据库并行，数据操作的本机语言分别来自不同类型的SQL语句CRUD（创建，读取，更新和删除的简写）：INSERT，SELECT，UPDATE和DELETE。 以相同的方式，如果您正确应用REST原则，则应使用HTTP动词，如下所示：

前四个请求在定义资源数据操作时显得很自然，让我们与相关的SQL数据库并行。数据库的本地语言CRUD（Create，Read，Update，Delete的简写）来自不同类型的SQL语句：INSERT，SELECT，UPDATE，与DELETE。如果你正确遵循REST原则，应该使用下面的请求方式：

| HTTP verb | Action                                 | Response status code                     |
| --------- | -------------------------------------- | ---------------------------------------- |
| GET       | 请求一个存在的资源                              | "200 OK" 如果资源存在,“404 Not Found” 如果不存在, “500服务器错误“ 其他原因 |
| PUT       | 通过客户端传递过来的标识符更新或创建资源                   | "201 CREATED"创建成功,"200 OK"更新成功。 "500 服务器错误"其他原因 |
| POST      | 创建具有在服务器端生成的标识符的资源，或使用从客户端提供的现有标识符更新资源 | “201 CREATED”创建成功,”200 OK”更新成功, “404 Not Found”要更新的资源不存在 “500 Internal Server Error” 其他原因 |
| DELETE    | 删除一个资源                                 | “200 OK“or “204 No Content”成功删除 “404 Not Found”资源不存在，已经被删除, and “500 Internal Server Error”其他错误 |

注意这里可以通过PUT和POST请求来创建资源。在创建资源时，当客户端提供了具有特定标识符的URL的情况下，用PUT请求比较合适。

<?xml version="1.0" encoding="utf-8"?>
<balance date="22082014">
<Item>Sample item</Item>
<price currency="EUR">100</price>
</balance>
但是，在您的应用程序中，您可能希望将其留给服务器REST应用程序来决定放置新创建的资源的位置，从而在适当但尚未知或不存在的位置创建它。

例如，在我们的示例中，我们可能希望服务器根据当前日期创建URI的日期部分。 在这种情况下，使用POST动词到主资源URI是完全正确的，让服务器响应新创建的资源的位置：

POST /data/documents/balance HTTP/1.1 Content-Type: text/xml Host: www.mydatastore.com
<?xml version="1.0" encoding="utf-8"?>
<balance date="22082014">
<Item>Sample item</Item>
<price currency="EUR">100</price>
</balance>
HTTP/1.1 201 Created Content-Type: text/xml Location: /data/documents/balance


原则4-资源可以有多个表示

资源的一个关键特征是它可以以与存储资源不同的形式表示。 因此，可以以不同的表示来请求或张贴。 只要支持指定的格式，启用REST的端点就可以使用它。 在前面的例子中，我们发布了一个余额的XML表示，但如果服务器支持JSON格式，以下请求也将是有效的：

POST /data/documents/balance HTTP/1.1 
Content-Type: application/json 
Host: www.mydatastore.com
{
 "balance": {    
​			"date": ""22082014"", 
​			"Item": "Sample item",
​			"price": {      
​					"-currency": "EUR",
​					"#text": "100"
​					} 
​			} 
} 
HTTP/1.1 201 Created 
Content-Type: application/json
 Location: /data/documents/balance

原则5-可沟通 无状态

始终将通过HTTP请求的资源操作视为原子操作。所有修改资源的HTTP请求都应该在隔离后再执行，请求执行完成后，资源将处于最终状态，这意味着不支持部分资源更新。 您应该始终发送资源的完整状态。

回到平衡示例，更新给定余额的price字段将意味着发布一个包含所有余额数据的完整JSON文档，包括更新的price字段。 只发送更新的价格字段不是无状态的，因为它意味着应用程序知道资源具有价格字段，即它知道其状态。

您的RESTful应用程序的另一个要求是无状态; 事实上，一旦部署在生产环境中，传入请求可能由负载均衡器提供服务，确保可扩展性和高可用性。 一旦通过负载平衡器暴露出来，保持在服务器端的应用程序状态的想法就会受到影响。 这并不意味着您不能保持应用程序的状态。 这只是意味着你应该以RESTful的方式保持它。 例如，在URI内保留一部分状态。

RESTful API的无状态将呼叫者隔离在服务器端的变化。 因此，不要求呼叫者在连续请求中与同一台服务器进行通信。 这允许在服务器基础架构内轻松应用更改，例如添加或删除节点。

请记住，您的责任是保持您的RESTful API无状态，正如API的消费者所期望的那样。

现在你知道REST大约15岁，一个明智的问题是：“为什么最近才变得如此受欢迎？”我的答案是，我们作为开发人员通常拒绝简单直接的方法，大部分时候，更愿意花更多的时间把已经复杂的解决方案变成更为复杂的解决方案。

以古典SOAP Web服务为例。 它们的各种WS- *规范是如此之多，有时甚至被宽松地定义，为了使来自不同供应商的不同解决方案可互操作，已经引入了单独的规范WS-Basic简档。它定义了额外的互操作性规则，以确保所有WS - *基于SOAP的Web服务中的规范可以一起工作。