# 1. Thymeleaf CRUD DB Get Employees

![](img/2020-04-27-16-51-44.png)

![](img/2020-04-27-16-51-58.png)

![](img/2020-04-27-16-52-15.png)

![](img/2020-04-27-16-52-35.png)

![](img/2020-04-27-16-52-50.png)

![](img/2020-04-27-16-53-09.png)

---

### copy 33-project, paste to 34-project `34-thymeleafdemo-employees-list-db`

- intellij reopen 34-project

- Update pom.xml for database support

- add a dependecny in `pom.xml`

![](img/2020-04-27-16-57-47.png)

```html
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
```

- add entry for mysql

![](img/2020-04-27-16-59-37.png)

```html
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>

		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
		</dependency>
```

- update project

![](img/2020-04-27-17-01-21.png)

- now copy from our previous project `23-project`'s codes

![](img/2020-04-27-17-03-37.png)

![](img/2020-04-27-17-04-53.png)

- delete old Employee(delete the "model" package)

![](img/2020-04-27-17-05-36.png)

![](img/2020-04-27-17-07-05.png)

- create a new package for 34-project

![](img/2020-04-27-17-08-27.png)

- COPY `Employee.java` from 23-project, paste into 34-project

![](img/2020-04-27-17-10-10.png)

- but we need to add a new constructor `id` param for new `Employee.java`

```java
    public Employee(int id, String firstName, String lastName, String email) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
        this.email = email;
    }
```

---

## Get Employee Part 2:

![](img/2020-04-27-17-18-51.png)

![](img/2020-04-27-17-20-17.png)

- copy `dao` from `23-project`

![](img/2020-04-27-17-20-51.png)

![](img/2020-04-27-17-22-04.png)

![](img/2020-04-27-17-22-29.png)

![](img/2020-04-27-17-23-28.png)

![](img/2020-04-27-17-22-59.png)

- copy `service` from `23-project` paste into `33-project`

- don't forget to fix error, since `23-project` import from `23`, we need to change to import from `34-project`

- now testing it, run `ThymeleafdemoApplication` agian

![](img/2020-04-27-17-32-20.png)

- STILL WORKING

---

## now refresh my database

```sql
CREATE DATABASE  IF NOT EXISTS `employee_directory`;
USE `employee_directory`;

--
-- Table structure for table `employee`
--

DROP TABLE IF EXISTS `employee`;

CREATE TABLE `employee` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(45) DEFAULT NULL,
  `last_name` varchar(45) DEFAULT NULL,
  `email` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;

--
-- Data for table `employee`
--

INSERT INTO `employee` VALUES 
	(1,'Leslie','Andrews','leslie@gmail.com'),
	(2,'Emma','Baumgarten','emma@gmail.com'),
	(3,'Avani','Gupta','avani@gmail.com'),
	(4,'Yuri','Petrov','yuri@gmail.com'),
	(5,'Juan','Vega','juan@gmail.com');

```

![](img/2020-04-27-17-35-16.png)

- Let's remove the in-memory employee code

- update EmployeeController 

```java
package com.luv2code.springboot.thymeleafdemo.controller;


import com.luv2code.springboot.thymeleafdemo.entity.Employee;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

import javax.annotation.PostConstruct;
import java.util.ArrayList;
import java.util.List;

@Controller
@RequestMapping("/employees")
public class EmployeeController {
    

    //add mapping for "/list"
    @GetMapping("/list")
    public String listEmployees(Model theModel) {
        //add to the spring model
        theModel.addAttribute("employees", theEmployees);

        return "list-employees";
    }
}

```

![](img/2020-04-27-18-26-56.png)
![](img/2020-04-27-18-28-48.png)

- update `EmployeeController`

```java
package com.luv2code.springboot.thymeleafdemo.controller;


import com.luv2code.springboot.thymeleafdemo.entity.Employee;
import com.luv2code.springboot.thymeleafdemo.service.EmployeeService;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

import java.util.List;

@Controller
@RequestMapping("/employees")
public class EmployeeController {

    private EmployeeService employeeService;

    public EmployeeController(EmployeeService theEmployeeService){
        employeeService = theEmployeeService;
    }

    //add mapping for "/list"
    @GetMapping("/list")
    public String listEmployees(Model theModel) {
        //get employees from db
        List<Employee> theEmployees = employeeService.findAll();

        //add to the spring model
        theModel.addAttribute("employees", theEmployees);

        return "list-employees";
    }
}

```

- rerun the app

![](img/2020-04-27-18-30-49.png)

- now read data from database

---

- Add index.html to redirect to `employees/list`

![](img/2020-04-27-18-40-05.png)

- index.html

```html
<meta http-equiv="refresh"
      content="0; URL='employees/list' ">
```

- now, run `http://localhost:8080/`

![](img/2020-04-27-18-40-45.png)

- Success!!! No more 404 Redirects to `employees/list`















