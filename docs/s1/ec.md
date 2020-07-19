# 1. Environment Configuration

## download tomcat

![](img/1.png)

- unzip the apache-tomcat-8.5.42.tar.gz

- drag apache-tomcat-8.5.42 into jsf-for-beginners

![](img/2.png)

---

- cd to the folder

- `startup.sh`  is what I'll use to actually start the Tomcat server.

![](img/3.png)

![](img/4.png)

---

- enter `bin/startup.sh` ,then our server's installed and we also started the server.

- Tomcat started.

![](img/5.png)

- typing http://localhost:8080/

![](img/6.png)

---

- Now it's time to learn shut down

- `ls bin`

![](img/7.png)

- we found the `shutdown.sh`

- on terminal print `bin/shutdown.sh`; then stop server.

- we also can run the tomcat server from intellij 

![](img/8.png)



---

# IntelliJ IDEA – Run / debug web application on Tomcat

- Plugins -> search 

- Make sure Tomcat and TomEE Integration is checked.

![](img/9.png)

- create a new java Enterprise 'spring-demo-one'

![](img/11.png)

![](img/10.png)

![](img/12.png)


- the project should import the downloaded libraries:

![](img/13.png)
