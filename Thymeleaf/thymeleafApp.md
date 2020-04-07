# 2. Create Thymeleaf App

- https://start.spring.io/

![](img/2020-04-06-19-01-05.png)

- generate this project

- unzip thymeleafdemo

- paste `thymeleafdemo` in `dev-spring-boot`

- import this project

- change name to `30-thymeleafdemo-helloworld`

- add a new package `controller`

![](img/2020-04-06-19-20-28.png)

- add a new class

![](img/2020-04-06-19-21-17.png)

```java
package com.luv2code.springboot.thymeleafdemo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class DemoController {
    //create a mapping for "/hello"
    @GetMapping("/hello")
    public String sayHello(Model theModel) {
        theModel.addAttribute("theDate", new java.util.Date());
        return "HelloWorld";
    }
}

```

![](img/2020-04-06-19-24-15.png)

![](img/2020-04-06-19-25-58.png)

- add a new html in templates

![](img/2020-04-06-19-27-04.png)

- helloworld.html

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Thymeleaf Demo</title>
</head>
<body>
    <p th:text="'Time on the server is ' + ${theDate}" />
</body>
</html>
```

![](img/2020-04-06-19-32-20.png)

![](img/2020-04-06-19-37-58.png)

![](img/2020-04-06-19-38-59.png)


