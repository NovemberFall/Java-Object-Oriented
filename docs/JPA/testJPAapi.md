# 3. Testing REST API DAO

![](img/2020-04-03-14-16-36.png)

- update EmployeeDAOJpaImpl

```java
package com.luv2code.springboot.cruddemo.dao;

import com.luv2code.springboot.cruddemo.entity.Employee;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

import javax.persistence.EntityManager;
import javax.persistence.Query;
import java.util.List;

@Repository
public class EmployeeDAOJpaImpl implements EmployeeDAO{
    private EntityManager entityManager;

    @Autowired
    public EmployeeDAOJpaImpl(EntityManager entityManager) {
        this.entityManager = entityManager;
    }

    @Override
    public List<Employee> findAll() {
        //create a query
        Query theQuery = entityManager.createQuery("from Employee");

        //execute query
        List<Employee> employees = theQuery.getResultList();

        //return the results
        return employees;
    }

    @Override
    public Employee findById(int theId) {
        //get employee
        Employee theEmployee = entityManager.find(Employee.class, theId);
        //return employee
        return theEmployee;
    }

    @Override
    public void save(Employee theEmployee) {
        //save or update the employee
        Employee dbEmployee = entityManager.merge(theEmployee);

        //update with id from db ... so we can get generate id for save/insert
        theEmployee.setId(dbEmployee.getId());
    }

    @Override
    public void deleteById(int theId) {
        //delete object with primary key
        Query theQuery = entityManager.createQuery(
                "delete from Employee where id=:employeeId");
        theQuery.setParameter("employeeId", theId);
        theQuery.executeUpdate();
    }
}
```

- test post method:

![](img/2020-04-03-15-49-01.png)

![](img/2020-04-03-15-49-37.png)

- test update `Put` method

![](img/2020-04-03-15-51-08.png)

![](img/2020-04-03-15-51-20.png)

- test delete method

![](img/2020-04-03-15-51-59.png)

![](img/2020-04-03-15-52-11.png)




