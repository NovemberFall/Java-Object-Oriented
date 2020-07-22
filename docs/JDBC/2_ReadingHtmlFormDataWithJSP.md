### `HTML Form Overview`

:star: Built-In Server Objects
- Review HTML Forms
![](img/2019-08-25-06-15-57.png)
---
![](img/2019-08-25-06-17-29.png)

- Building HTML Forms
![](img/2019-08-25-06-18-50.png)
---
- Reading Form Data with JSP
![](img/2019-08-25-06-20-31.png)
---
![](img/2019-08-25-06-21-53.png)

- create a `student-form.html` in `web` folder
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Student Registration Form</title>
</head>
<body>
<form action="student-response.jsp">
    First name:<input type="text" name="firstName"/>
    <br><br>
    Last name:<input type="text" name="lastName"/>
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
</html>
```
- create a `student-response.jsp` in `web`
```jsp
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Student Registration Form</title>
</head>
<body>
<form action="student-response.jsp">
    First name:<input type="text" name="firstName"/>
    <br><br>
    Last name:<input type="text" name="lastName"/>
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
</html>
```
![](img/2019-08-25-06-41-22.png)
- after click `Submit`
![](img/2019-08-25-06-42-35.png)


### `Drop-Down Lists`
- Drop-Down List in Action
![](img/2019-08-25-06-57-20.png)

---

- Drop-Down List - HTML `<select>` tag
![](img/2019-08-25-06-57-41.png)
---
![](img/2019-08-25-06-58-57.png)

---
1. Create HTML Form
2. Create JSP confirmation page

- copy `student-form.html`'s content, paste in a new `student-dropdown-from.html`

---

```html
<body>
<form action="student-dropdown-response.jsp">
    First name:<input type="text" name="firstName"/>
    <br><br>
    Last name:<input type="text" name="lastName"/>
    <br><br>
    <select name="country">
        <option>Brazil</option>
        <option>France</option>
        <option>Germany</option>
        <option>India</option>
        <option>Turkey</option>
        <option>United Kingdom</option>
        <option>United States of America</option>
    </select>
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
```

- copy `student-response.jsp`'s content, paste in a new `student-dropdown-response.jsp`

```jsp
<html>
<head>
    <title>Student Confirmation Title</title>
</head>
<body>
    The student is confirmed: ${param.firstName} ${param.lastName}
    <br><br>

    The student's country: ${param.country}
</body>
</html>
```
![](img/2019-08-25-07-16-41.png)
![](img/2019-08-25-07-17-04.png)

- Ok , Cool !


### `Radio Button`
- Radio Button Demo
- HTML for Radio Button
![](img/2019-08-25-07-19-47.png)
![](img/2019-08-25-07-20-09.png)

1. Create HTML Form
2. Create JSP confirmation page

- copy `student-form.html`'s content, paste in a new `student-radio-from.html`
```html
<body>
<form action="student-radio-response.jsp">
    First name:<input type="text" name="firstName"/>
    <br><br>
    Last name:<input type="text" name="lastName"/>
    <br><br>
    Favorite Programming Language: <br>
    <input type="radio" name="favoriteLanguage" value="Java"/> Java
    <input type="radio" name="favoriteLanguage" value="C++"/> C++
    <input type="radio" name="favoriteLanguage" value="JavaScript"/> JavaScript
    <input type="radio" name="favoriteLanguage" value="PHP"/> PHP
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
```

- copy `student-response.jsp`'s content, paste in a new `student-radio-response.jsp`
```jsp
<html>
<head>
    <title>Student Confirmation Title</title>
</head>
<body>
    The student is confirmed: ${param.firstName} ${param.lastName}

    <br><br>
    The student's favorite programming language: ${param.favoriteLanguage} 
</body>
</html>
```

![](img/2019-08-25-07-28-11.png)
![](img/2019-08-25-07-28-23.png)



### `Checkboxes-Overview`
- Check Box Demo
- HTML for CHeck Box
![](img/2019-08-25-07-33-20.png)
![](img/2019-08-25-07-33-39.png)
![](img/2019-08-25-07-34-05.png)

1. Create HTML Form
2. Create JSP confirmation page

- copy `student-form.html`'s content, paste in a new `student-checkbox-from.html`
```html
<body>
<form action="student-checkbox-response.jsp">
    First name:<input type="text" name="firstName"/>
    <br><br>
    Last name:<input type="text" name="lastName"/>
    <br><br>
    <input type="checkbox" name="favoriteLanguage" value="Java"> Java
    <input type="checkbox" name="favoriteLanguage" value="C++"/> C++
    <input type="checkbox" name="favoriteLanguage" value="JavaScript"/> JavaScript
    <input type="checkbox" name="favoriteLanguage" value="PHP"/> PHP
    <br><br>
    <input type="submit" value="Submit"/>
</form>
</body>
</html>
```

- copy `student-response.jsp`'s content, paste in a new `student-checkbox-response.jsp`
```jsp
<body>
    The student is confirmed: ${param.firstName} ${param.lastName}
    <br><br>
    Favorite Programming Language: <br>
<%--  dispaly list of "favoriteLanguage"  --%>
    <ul>
        <%
            String[] langs = request.getParameterValues("favoriteLanguage");
            for (String tempLang : langs) {
                out.print("<li>" + tempLang + "</li>");
            }
        %>
    </ul>
</body>
</html>
```
![](img/2019-08-25-07-44-28.png)
![](img/2019-08-25-07-46-58.png)

:star: `How to handle when user doesn't select a checkbox?`
```java
        <%
            String[] langs = request.getParameterValues("favoriteLanguage");
        
            if (langs != null) {
                for (String tempLang : langs) {
                    out.println("<li>" + tempLang + "</li>");
                }
            }
        %>
```



