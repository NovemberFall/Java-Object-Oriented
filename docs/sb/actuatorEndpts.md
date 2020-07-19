# 8. Accessing Actuator endpoints

- copy 02-dev-tools-demo , and paste change name to 03-actuator-demo

- import 03-actuator-demo for intellij

- deploy actuator endpoints

- pom.xml

```xml
		<!-- ADD SUPPORT FOR AUTOMATIC RELOADING -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
		</dependency>

		<!-- ADD SUPPORT FOR SPRING BOOT ACTUATOR -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>
	</dependencies>

```

![](img/2020-04-02-00-41-45.png)

![](img/2020-04-02-00-41-25.png)

---

- test info endpoints

![](img/2020-04-02-00-43-49.png)

- we can add some info into `resources/application.properties`

```json
info.app.name = My Super Cool App
info.app.description = A crazy fun app, yoohoo!
info.app.version = 1.0.0
```

![](img/2020-04-02-00-53-39.png)

![](img/2020-04-02-00-58-01.png)

![](img/2020-04-02-00-58-32.png)

---

## I have installed json formatter for google chrome...

- update `resources/application.properties`

```json
info.app.name = My Super Cool App
info.app.description = A crazy fun app, yoohoo!
info.app.version = 1.0.0

# Use wildcard "*" to expose all endpoints
# Can also expose individual endpoints with a comma-delimited list
#
management.endpoints.web.exposure.include=*
```

- http://localhost:8080/actuator/beans

![](img/2020-04-02-01-03-08.png)

- http://localhost:8080/actuator/threaddump

![](img/2020-04-02-01-05-58.png)

- http://localhost:8080/actuator/mappings

![](img/2020-04-02-01-06-51.png)

---



