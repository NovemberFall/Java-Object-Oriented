# 10. Running SpringBoot from command line

![](img/2020-04-02-01-44-02.png)

![](img/2020-04-02-01-45-01.png)

![](img/2020-04-02-01-45-22.png)

![](img/2020-04-02-01-46-04.png)

![](img/2020-04-02-01-47-00.png)

![](img/2020-04-02-01-47-22.png)

![](img/2020-04-02-01-47-41.png)

![](img/2020-04-02-01-48-07.png)

---

### Let's delete actuator and security from pom.xml

- exit the IDE

![](img/2020-04-02-02-13-11.png)

![](img/2020-04-02-02-13-54.png)

![](img/2020-04-02-02-14-53.png)

![](img/2020-04-02-02-16-05.png)

- run `./mvnw package`

![](img/2020-04-02-02-17-08.png)

- we see `BUILD SUCCESS`

![](img/2020-04-02-02-17-36.png)

![](img/2020-04-02-02-18-32.png)

- `cd target`

![](img/2020-04-02-02-19-23.png)

![](img/2020-04-02-02-20-16.png)

- so our springboot app run successfully

![](img/2020-04-02-02-21-18.png)

![](img/2020-04-02-02-21-42.png)

![](img/2020-04-02-02-22-25.png)
---


## Run app using spring boot maven plugin

![](img/2020-04-02-02-23-51.png)

![](img/2020-04-02-02-24-35.png)

- enter localhost:8080 again

![](img/2020-04-02-02-25-20.png)

- working again!

- this point, we run springboot app from command line, no need for IDE, and 
  also no need to have any of the servers installed because our springboot app
  is self contained.



















