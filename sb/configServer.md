# 12. Configuring the Spring Boot Server

![](img/2020-04-02-03-01-49.png)

![](img/2020-04-02-03-02-23.png)

![](img/2020-04-02-03-02-44.png)

![](img/2020-04-02-03-03-05.png)

![](img/2020-04-02-03-03-22.png)

![](img/2020-04-02-03-04-00.png)

![](img/2020-04-02-03-04-49.png)

![](img/2020-04-02-03-05-20.png)
---

![](img/2020-04-02-03-07-46.png)

- update `resources/application.properties`

```json
#
# Define my crazy properties
#
coach.name = Mickey mouse
team.name = The Mouse Club


#
# Change Spring Boot embedded server port
#
server.port = 7070


#
# Set the context path of the application
#
# All requests should be prefixed with /mycoolapp
#
server.servlet.context-path=/mycoolapp
```

- enter http://localhost:7070/mycoolapp/workout

![](img/2020-04-02-03-17-58.png)

![](img/2020-04-02-03-18-52.png)



















