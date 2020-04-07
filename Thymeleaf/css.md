# 3. Apply CSS style

![](img/2020-04-06-19-42-03.png)

![](img/2020-04-06-19-42-30.png)

![](img/2020-04-06-19-42-58.png)

![](img/2020-04-06-19-43-26.png)

![](img/2020-04-06-19-43-57.png)

![](img/2020-04-06-19-44-23.png)

![](img/2020-04-06-19-44-49.png)

![](img/2020-04-06-19-45-08.png)

![](img/2020-04-06-19-45-25.png)

- copy project 30, paste on 31

- create a new folder `css`

![](img/2020-04-06-19-50-59.png)

![](img/2020-04-06-20-00-51.png)

```css
.funny{
    font-style: italic;
    color: green;
}
```

- Reference CSS in Thymeleaf templates

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Thymeleaf Demo</title>

    <!-- reference CSS file   -->
    <link rel="stylesheet"
          th:href="@{/css/demo.css}" />
</head>
<body>
    <p th:text="'Time on the server is ' + ${theDate}" class="funny"/>
</body>
</html>
```

![](img/2020-04-06-19-54-50.png)

- run again

![](img/2020-04-06-20-04-49.png)











