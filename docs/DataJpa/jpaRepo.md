# 2. Creating Spring DATA JPA Repo

- rebuild our database

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

- copy 22 folder, paste it, and chanage name to 23

- import project 23 for intellij

- delete 3 files from folder `dao`

![](img/2020-04-05-21-06-24.png)

![](img/2020-04-05-21-07-05.png)

- extends JpaRepository

![](img/2020-04-05-21-09-24.png)

- no need to write any codes

![](img/2020-04-05-21-10-19.png)

![](img/2020-04-05-21-11-03.png)

![](img/2020-04-05-21-11-51.png)

![](img/2020-04-05-21-12-30.png)

![](img/2020-04-05-21-16-15.png)
---

- update EmployeeServiceImplementation

```java
package com.luv2code.springboot.cruddemo.service;
import com.luv2code.springboot.cruddemo.dao.EmployeeRepository;
import com.luv2code.springboot.cruddemo.entity.Employee;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.Optional;

@Service
public class EmployeeServiceImplementation implements EmployeeService {

    private EmployeeRepository employeeRepository;

    @Autowired
    public EmployeeServiceImplementation(EmployeeRepository theEmployeeRepository) {
        this.employeeRepository = theEmployeeRepository;
    }

    @Override
    public List<Employee> findAll() {
        return employeeRepository.findAll();
    }

    @Override
    public Employee findById(int theId) {
        Optional<Employee> result = this.employeeRepository.findById(theId);
        Employee theEmployee = null;
        if (result.isPresent()) {
            theEmployee = result.get();
        }else{
            //we didn't find the employee
            throw new RuntimeException("Didn't find employee id - " + theId);
        }
        return theEmployee;
    }

    @Override
    public void save(Employee theEmployee) {
        employeeRepository.save(theEmployee);
    }

    @Override
    public void deleteById(int theId) {
        employeeRepository.deleteById(theId);
    }
}
```

## Testing the REST API with Spring DATA JPA Repository

![](img/2020-04-05-21-33-16.png)

![](img/2020-04-05-21-33-47.png)

![](img/2020-04-05-21-36-25.png)

![](img/2020-04-05-21-37-25.png)

![](img/2020-04-05-21-38-50.png)

![](img/2020-04-05-21-39-11.png)

- update

![](img/2020-04-05-21-40-05.png)

![](img/2020-04-05-21-40-20.png)

- delete

![](img/2020-04-05-21-40-55.png)

![](img/2020-04-05-21-41-07.png)

- Recall :

![](img/2020-04-05-21-42-31.png)

- Spring Data JPA Magic!

