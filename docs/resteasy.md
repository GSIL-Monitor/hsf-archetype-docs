# RESTEasy

> hsf模板工程使用RESTEasy实现RESTful风格API。

## 关于 RESTful API

Representational State Transfer，翻译是”表现层状态转化”。
面向资源是REST最明显的特征，对于同一个资源的一组不同的操作。资源是服务器上一个可命名的抽象概念，资源是以名词为核心来组织的，首先关注的是名词。REST要求，必须通过统一的接口来对资源执行各种操作。对于每个资源只能执行一组有限的操作。（7个HTTP方法：GET/POST/PUT/DELETE/PATCH/HEAD/OPTIONS）

符合REST设计标准的API，即RESTful API。REST架构设计，遵循的各项标准和准则，就是HTTP协议的表现，换句话说，HTTP协议就是属于REST架构的设计模式。

## 关于 RESTEasy

RESTEasy 是 JBoss 的一个开源项目，提供各种框架构建 RESTful Web Services 和 RESTful Java 应用程序。它是 JAX-RS 规范的一个完整实现并通过 JCP 认证。RESTEasy 还提供一个 RESTEasy JAX-RS 客户端调用框架，能够很方便与 EJB、Seam、Guice、Spring 和 Spring MVC 集成使用，支持在客户端与服务器端自动实现 GZIP 解压缩。


## RESTEasy 常用注解

@GET，@POST，@PUT，@DELETE注解分别对应HTTP请求的查询，新增，修改，删除方法。

更多注解如：@FormParam、@PathParam、@QueryParam、@HeaderParam、@CookieParam、@MatrixParam、@Context可参考：
https://www.cnblogs.com/chen-lhx/p/5599806.html 和这里
https://blog.csdn.net/github_35758702/article/details/52614282

一个例子：

```java
@Path("/library")
public class Library {

   @GET
   @Path("/books")
   public String getBooks() {...}

   @GET
   @Path("/book/{isbn}")
   public String getBook(@PathParam("isbn") String id) {
      // search my database and get a string representation and return it
   }

   @PUT
   @Path("/book/{isbn}")
   public void addBook(@PathParam("isbn") String id, @QueryParam("name") String name) {...}

   @DELETE
   @Path("/book/{id}")
   public void removeBook(@PathParam("id") String id {...}

}
```

说明：

- 类或方法是存在 @Path 注解或者 HTTP 方法的注解。

- 如果方法上没有 HTTP 方法的注解，则称为 JAXRSResourceLocators。

- @Path 注解支持正则表达式映射。

RESTEasy更多特性和使用方法请参考 [官方文档](http://docs.jboss.org/resteasy/docs/3.5.1.Final/userguide/html_single/index.html)。
