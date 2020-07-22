### `JSP Expression`

![](img/2019-08-25-03-27-13.png)
![](img/2019-08-25-03-28-02.png)

- here is an example
![](img/2019-08-25-03-30-02.png)


```java
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
  <head>
    <title>$Title$</title>
  </head>
  <body>
  <h3>Hello World of Java!</h3>
  The time on the server is <%= new java.util.Date() %>
  <br>
  Converting a string to uppercase: <%= new String("Hello World").toUpperCase() %>
  <br><br>
  25 multiplied by 4 equals <%= 25 * 4 %>
  <br><br>
  Is 75 less than 69? <%= 75 < 69 %>
  </body>
</html>
```
![](img/2019-08-25-04-53-04.png)


### `JSP Scriptlets` (脚本小程序)
- now create a new `scriptlet.jsp`

```java
<body>
    <h3>Hello World of Java</h3>
    <%
    for(int i=1; i<=5; i++){
        out.println("<br/> I really enjoy JSP code: " + i);
    }    
    %>
</body>
```
![](img/2019-08-25-05-06-40.png)



### `JSP Declarations`
- add a new file `declaration.jsp`

- Declare a method in the JSP page
- Call the method in the same JSP page
```java
<body>
<%!
    String makeItLower(String data) {
        return data.toLowerCase();
    }
%>
Lower case "Hello World": <%= makeItLower("Hello World")%>
</body>
```
![](img/2019-08-25-05-16-05.png)

### `Calling a java class from JSP`
- Minimize the `scriptlets` and `declarations` in a JSP

1. Create Java class
2. Call Java class from JSP

:star: create a package named `com.luv2code.jsp`
- create a class named `FunUtils.java` in package `com.luv2code.jsp` 
```java
package com.luv2code.jsp;
public class FunUtils {
    public static String makeItLower(String data) {
        return data.toLowerCase();
    }
}
```
- create a class named `fun-test.jsp` in `web` folder
![](img/2019-08-25-05-30-58.png)
```jsp
<%@ page import="com.luv2code.jsp.*" %>
<html>
<body>
Let's have some fun: <%=FunUtils.makeItLower("FUN FUN FUN")%>
</body>
</html>
```
![](img/2019-08-25-05-36-03.png)


### `Built-In Server Objects`
- List of commonly used JSP objects
![](img/2019-08-25-05-40-28.png)
---
![](img/2019-08-25-05-42-15.png)


- create a `builtin-test.jsp`
```jsp
<body>
<h3>JSP Built-In Objects</h3>
Request user agent: <%=request.getHeader("User-Agent")%>
<br><br>
Request language: <%=request.getLocale()%>
</body>
```
![](img/2019-08-25-05-50-21.png)




### `Including Files in JSP`

:star: how to use JSP for including other files 
![](img/2019-08-25-05-57-26.png)

- create a `my-header.html` in `web` folder
```html
<h1 align="center">JSP Tutorial</h1>
```

- create a `my-footer.jsp` in `web` folder
```jsp
<p align="center">
    Last updated: <%=new java.util.Date()%>
</p>
```

- create a `homepage.jsp` in `web` folder
```html
<html>
<body>
<jsp:include page="my-header.html"/>
Blah blah blah ... <br><br>
Blah blah blah ... <br><br>
Blah blah blah ... <br><br>
<jsp:include page="my-footer.jsp"/>

</body>
</html>
```
![](img/2019-08-25-06-10-15.png)
- so far so good!
- Great!

