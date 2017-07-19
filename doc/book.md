# NodeJs Restful Web API

## 第一章 关于REST

### 什么是 Rest

Rest 是 Representational State Transfer 的缩写——表征状态转移。是Roy Fielding博士在2000年他的博士论文中提出来的一种软件架构风格。它是一种针对网络应用的设计和开发方式，可以降低开发的复杂性，提高系统的可伸缩性。 

表征状态转移。是一组架构约束条件和原则。满足这些约束条件和原则的应用程序或设计就是RESTful。需要注意的是，REST是设计风格而不是标准。REST通常基于使用HTTP，URI，和XML（标准通用标记语言下的一个子集）以及HTML（标准通用标记语言下的一个应用）这些现有的广泛流行的协议和标准。 
REST 定义了一组体系架构原则，您可以根据这些原则设计以系统资源为中心的 Web 服务，包括使用不同语言编写的客户端如何通过 HTTP 处理和传输资源状态。 如果考虑使用它的 Web 服务的数量，REST 近年来已经成为最主要的 Web 服务设计模式。 事实上，REST 对 Web 的影响非常大，由于其使用相当方便，已经普遍地取代了基于 SOAP 和 WSDL 的接口设计。 

Nowadays, topics such as cloud computing and mobile device service feeds, as well as other data sources driven by cutting-edge, scalable, stateless, and modern technologies such as RESTful web services, leave the impression that REST was invented recently. Well, to be honest, it definitely was not! In fact, REST has been here since the end of the 20th century.

【如今，诸如云计算和移动设备服务源之类的主题以及其他数据源由前端，可扩展，无状态和现代技术（如RESTful Web服务）驱动，给人留下了最近发明REST的印象。 那么说实话，绝对不是！ 事实上，自20世纪末以来，REST一直在这里。】

This chapter will walk you through REST's fundamental principles, and it will explain how
REST couples with the HTTP protocol. You will look into the five key principles that need
to be considered while turning an HTTP application into a RESTful-service-enabled
application. You will also look at the differences in describing RESTful and classic SOAP-
based web services. Finally, you will learn how to utilize already existing infrastructure for
your benefit.

【本章将介绍REST的基本原则，并介绍如何将REST与Http协议相结合。你会看到由Http应用转向REST提服务所考虑遵循的5个关键原则，你还将看到RESTful与典型的以SOUAP为基础的web服务的差异性。最后，你会学习怎样利用已经存在的基础资源为你所用】

In this chapter, we will cover the following topics:

REST fundamentals

REST with HTTP

Essential differences in the description and discovery of RESTful servicescomhpared to classical SOAP-based services

Taking advantage of existing infrastructure

【本章，我们将介绍以下主题：

REST 基础、REST 与HTTP、 RESTful服务的描述和发现与传统的基于SOAP的服务的基本差异、了解利用现有基础设施的优点

】

REST fundamentals

It actually happened back in 1999, when a request for comments was submitted to the Internet Engineering Task Force (IETF: http://www.ietf.org/) via RFC 2616:“Hypertext Transfer Protocol-HTTP/1.1.” One of its authors, Roy Fielding, later defined a set of principles built around the HTTP and URI standards. This gave birth to REST as we know it today.

【REST 基础

实际上是在1999年，当通过RFC 2616向互联网工程任务组（IETF：http：//www.ietf.org/）提交了意见征求意见时，其实际上是“超文本传输协议-HTTP / 1.1”。 其作者Roy Fielding后来定义了围绕HTTP和URI标准构建的一套原则。 我们今天知道这产生了REST。

这些定义在Fielding的论文“表征状态转移（REST）”的第5章，“建筑风格”和基于网络的软件架构的“设计”中给出
。 论文仍可在http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_a rch_style.htm获得。】

Let's look at the key principles around the HTTP and URI standards, sticking to which will
make your HTTP application a RESTful-service-enabled application:


Everything is a resource

Each resource is identifiable by a unique identifier (URI)
Use the standard HTTP methods

Resources can have multiple representations
Communicate statelessly

我们来看看关于HTTP和URI标准的关键原则，坚持使你的HTTP应用成为启用RESTful的应用程序：

一切都是资源、所有资源都可以通过唯一标识符（URI）来标识

使用标准的HTTP方法

资源能多个表现形式			

沟通无国界


Principle 1 – everything is a resource

To understand this principle, one must conceive the idea of representing data by a specificformat and not by a physical file. Each piece of data available on the Internet has a formatthat could be described by a content type. For example, JPEG images; MPEG videos; HTML,XML, and text documents; and binary data are all resources with the following contenttypes: image/jpeg, video/mpeg, text/html, text/xml, and application/octet-stream.		

原则1-万物皆资源

为了理解这个原则，人们必须设想一种通过特定格式而不是物理文件来表示数据的想法。 互联网上可用的每个数据都可以通过内容类型来描述。 例如，JPEG图像; MPEG视频; HTML，XML和文本文档; 二进制数据都是具有以下内容类型的资源：image / jpeg，video / mpeg，text / html，text / xml和application / octet-stream。		

Principle 2 – each resource is identifiable by aunique identifier

Since the Internet contains so many different resources, they all should be accessible viaURIs and should be identified uniquely. Furthermore, the URIs can be in a human-readableformat, despite the fact that their consumers are more likely to be software programs ratherthan ordinary humans.

Human-readable URIs keep data self-descriptive and ease further development against it.This helps you to reduce the risk of logical errors in your programs to a minimum.

Here are a few sample examples of such URIs:

```
        http://www.mydatastore.com/images/vacation/2014/summer
        http://www.mydatastore.com/videos/vacation/2014/winter
        http://www.mydatastore.com/data/documents/balance?format=xml
        http://www.mydatastore.com/data/archives/2014
```

These human-readable URIs expose different types of resources in a straightforward manner. In the example, it is quite clear that the media types of these resources are asfollows:

Images
Videos
XML documents
Some kinds of binary archive documents

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

原则3-使用标准的HTTP方法

本地HTTP协议（RFC 2616）定义了八个请求方式：