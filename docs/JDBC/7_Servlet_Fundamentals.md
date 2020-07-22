### `What are Servlets?`

![](img/2019-08-26-12-18-03.png)
---

![](img/2019-08-26-12-19-08.png)
---
![](img/2019-08-26-12-20-52.png)
---
![](img/2019-08-26-12-23-57.png)
---


- create a new Web project `servletdemo`

![](img/2019-08-26-16-52-06.png)
---

- `src` -> `New` -> `create new servlet`
![](img/2019-08-26-17-43-38.png)
---

- Servlet Configuration on `web.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    
    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>com.luv2code.servletdemo.HelloWorldServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/HelloWorldServlet</url-pattern>
    </servlet-mapping>
</web-app>
```
- run the server
![](img/2019-08-27-01-24-06.png)
---

- The 2nd way for Servlet Configuration in `HelloWorldServlet.java`
```java
@WebServlet(name = "HelloWorldServlet", urlPatterns = {"/hello"})
public class HelloWorldServlet extends HttpServlet {
```
- input `http://localhost:8080/servletdemo_war_exploded/hello`
![](img/2019-08-27-01-30-24.png)
- we also get the same result
---


### `Comparing Servlets and JSP - What's the difference`

![](img/2019-08-27-01-41-24.png)
---

- Which One?
![](img/2019-08-27-01-44-00.png)
---
![](img/2019-08-27-01-48-22.png)
---

### `Reading HTML Form Data with Servlets`

- HTTP Request/ Response
![](img/2019-08-27-02-16-27.png)
---

:star: Step1: Building HTML Form
![](img/2019-08-27-02-20-42.png)
---

- Form `GET` method calls Servlet `doGet()` method
![](img/2019-08-27-02-21-54.png)
---

:star: Step2: Reading Form Data with Servlet
![](img/2019-08-27-02-23-54.png)
---
![](img/2019-08-27-02-24-19.png)
---

### `Reading HTML Form Data with Servlets` code example:

- create `student.form.html` in web
```html
<!DOCTYPE html>
<html lang="en">
<body>
<form action="StudentServlet" method="GET">
    First name: <input type="text" name="firstName"/>
    <br><br>
    Last name: <input type="text" name="lastName"/>
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
</html>
```
- create `StudentServlet` in package `com.luv2code.servletdemo`
```java

@WebServlet(name = "StudentServlet")
public class StudentServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //step1: set content type
        response.setContentType("text/html");
        
        //step2: get the printWriter
        PrintWriter out = response.getWriter();
        
        //step3: generate the HTML content
        out.println("<html><body>");
        out.println("The student is confirmed: "
                + request.getParameter("firstName") + " "
                + request.getParameter("lastName"));
        out.println("</body></html>");
    }
}
```
:star: Note: we still need configure the environment
- altering the `web.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"> 
<!--    <servlet>-->
<!--        <servlet-name>HelloWorldServlet</servlet-name>-->
<!--        <servlet-class>com.luv2code.servletdemo.HelloWorldServlet</servlet-class>-->
<!--    </servlet>-->
<!--    -->
<!--    <servlet-mapping>-->
<!--        <servlet-name>HelloWorldServlet</servlet-name>-->
<!--        <url-pattern>/HelloWorldServlet</url-pattern>-->
<!--    </servlet-mapping>-->
        <servlet>
            <servlet-name>StudentServlet</servlet-name>
            <servlet-class>com.luv2code.servletdemo.StudentServlet</servlet-class>
        </servlet>
        <servlet-mapping>
            <servlet-name>StudentServlet</servlet-name>
            <url-pattern>/StudentServlet</url-pattern>
        </servlet-mapping>
</web-app>
```

- run the .html on the Tomcat server
![](img/2019-08-27-04-44-14.png)
---
![](img/2019-08-27-04-44-29.png)



### `HTML Forms - Difference between GET and POST`

![](img/2019-08-27-04-46-51.png)
---

- Form GET method calls Servlet doGet() method
![](img/2019-08-27-04-49-34.png)
---
- Form POST method calls Servlet doPost() method
![](img/2019-08-27-04-50-23.png)
---
- Sending Data with GET method
![](img/2019-08-27-04-50-55.png)
---
-  Sending Data with POST method
![](img/2019-08-27-04-51-33.png)
---

- which one?
![](img/2019-08-27-04-52-06.png)
---
![](img/2019-08-27-04-52-41.png)

---

### `Reading Servlet Parameters`

- Servlet Configuration Parameters
![](img/2019-08-27-04-57-43.png)
---

-  Deployment Descriptor: web.xml
![](img/2019-08-27-04-58-09.png)
---

-  Reading Configuration Parameters
![](img/2019-08-27-04-58-55.png)
---

- code example
- first, configure our `web.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"> 
    <context-param>
        <param-name>max-shopping-cart-size</param-name>
        <param-value>99</param-value>
    </context-param>
    
     <context-param>
        <param-name>project-team-name</param-name>
        <param-value>The Coding Gurus</param-value>
    </context-param>  
</web-app>
```
---
- create `TestParamServlet` in package `com.luv2code.servletdemo`
```java
package com.luv2code.servletdemo;

@WebServlet(name = "TestParamServlet", urlPatterns = {"/testParam"})
public class TestParamServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //step 1: set content type
        response.setContentType("text/html");
        
        //step 2: get printWriter
        PrintWriter out = response.getWriter();
        
        //step 3: read configuration params
        ServletContext context = getServletContext();
        String maxCartSize = context.getInitParameter("max-shopping-cart-size");
        String teamName = context.getInitParameter("project-team-name");
        
        //step 4: generate HTML content
        out.println("<html><body>");
        
        out.println("Max cart: " + maxCartSize);
        out.println("<br><br>");
        out.println("Team name: " + teamName);

        out.println("</body></html>");
    }
}
```
![](img/2019-08-27-05-18-37.png)
---
