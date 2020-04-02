# 2. Create a Project with SpringBoot initializr

![](img/2020-04-01-16-50-08.png)
![](img/2020-04-01-16-50-43.png)

## input `https://start.spring.io/`

![](img/2020-04-01-16-55-27.png)

- note: add `Spring Web`

- click `GENERATE` button to create a web project

- then we can download the `mycoolapp.zip`

- unzip this .zip file

![](img/2020-04-01-17-00-01.png)

---

## create a folder named `dev-spring-boot`, paste mycoolapp into this folder

- import mave project

![](img/2020-04-01-19-25-06.png)

![](img/2020-04-01-19-25-29.png)

- click next

![](img/2020-04-01-19-25-55.png)

![](img/2020-04-01-19-26-56.png)

## if we use Eclipse, we need to fix it, but for intellij don't need

- it's different from jsp + servlet

- springboot just need to run application

![](img/2020-04-01-20-07-57.png)

- open `localhost:8080`

![](img/2020-04-01-20-09-45.png)

- here is ugly error

---

## Developing a REST API Controller with Spring Boot

- create a new package 

![](img/2020-04-01-20-15-29.png)

- create a new class `FunRestController` inside this folder

- building REST controller we start with the annotation

- improve the FunRestController.java

```java
package com.luv2code.springboot.demo.mycoolapp.rest;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.time.LocalDateTime;

@RestController
public class FunRestController {

    // expose "/" that return "Hello World"

    @GetMapping("/")
    public String sayHello(){
        return "Hello World! Time on server is " + LocalDateTime.now(); //Current time stamp
    }
}
```

- back to `MycoolappApplication`

- run again

![](img/2020-04-01-20-38-02.png)


- springboot solution made it easier to get started with spring development

- so use that spring initializer to help us set up our project really quickly

- we don't need to do any xml configuration and any java configuration

