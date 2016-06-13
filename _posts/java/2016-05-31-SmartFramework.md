---
layout: post
title: Smart Framework
category: Java
tags: java javaEE smartFramework
keywords:
description:
---

## simple web application  

```
├─src
│  ├─main
│  │  ├─java
│  │  │      _HelloServlet.java
│  │  └─webapp
│  │      └─WEB-INF
│  │          │  _web.xml
│  │          │  
│  │          └─jsp
│  │                 _hello.jsp
```  

>> Maven : Servlet, JSP, JSTL  

## HttpServlet  

```
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setAttribute("test", "noTest");
        req.getRequestDispatcher("/WEB-INF/jsp/hello.jsp").forward( req, resp);
    }
}
```  

>> 继承自HttpServlet  
>> override doGet  
>> HttpServletRequest传递参数  
>> 使用WebServlet注解 配置请求路径 对外发布  





