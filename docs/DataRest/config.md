# 3. Configuration Pagination Sort

![](img/2020-04-05-23-55-34.png)

![](img/2020-04-05-23-56-02.png)

![](img/2020-04-05-23-56-24.png)

![](img/2020-04-05-23-56-42.png)

![](img/2020-04-05-23-57-02.png)

![](img/2020-04-05-23-57-17.png)

![](img/2020-04-05-23-58-00.png)

![](img/2020-04-05-23-59-27.png)

```java
package com.luv2code.springboot.cruddemo.dao;

import com.luv2code.springboot.cruddemo.entity.Employee;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.rest.core.annotation.RepositoryRestResource;

@RepositoryRestResource(path="members")
public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
    //that's it ... no need to write any code LOL!
}
```

- insert `@RepositoryRestResource(path="members")` to `EmployeeRepsitory`

- rerun app

- since we change path(employees to memebers), it will generate 404 error

![](img/2020-04-06-00-02-29.png)

![](img/2020-04-06-00-04-04.png)

- let's change it back, just comment this line 

```java
//@RepositoryRestResource(path="members")
public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
    //that's it ... no need to write any code LOL!
}
```

![](img/2020-04-06-00-06-22.png)

- update application.properties

```json
#
# Spring Data REST properties
#
spring.data.rest.base-path=/magic-api
spring.data.rest.default-page-size=3
```

![](img/2020-04-06-00-07-57.png)

![](img/2020-04-06-00-08-12.png)

- now click next page

![](img/2020-04-06-00-09-23.png)

![](img/2020-04-06-00-10-26.png)

- let's change page size = 20

---

### Let's sort by last name

![](img/2020-04-06-00-13-52.png)

### Let's sort by last name, descending

![](img/2020-04-06-00-15-19.png)





