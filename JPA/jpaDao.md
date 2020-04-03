# 2. Create JPA DAO

- run `employee.sql` again on workbench

![](img/2020-04-03-13-05-25.png)

- copy older project `cruddemo` to `22-jpa-cruddemo`

- create a new class `EmployeeDAOjpaImpl` implements `EmployeeDAO`

![](img/2020-04-03-13-07-51.png)

![](img/2020-04-03-13-10-44.png)

```java
@Repository
public class EmployeeDAOjpaImpl implements EmployeeDAO{
    private EntityManager entityManager;

    @Autowired
    public EmployeeDAOjpaImpl(EntityManager entityManager) {
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
        return null;
    }

    @Override
    public void save(Employee theEmployee) {

    }

    @Override
    public void deleteById(int theId) {

    }
}

```

- run app, but there is an error, since sprigboot doesn't know 
  which DAO implementation to use...

![](img/2020-04-03-13-19-02.png)
![](img/2020-04-03-13-17-55.png)

- so, we need to set a implementation to be qualifier or primary

![](img/2020-04-03-13-20-40.png)


- run again

![](img/2020-04-03-14-14-15.png)

- cool!

- test on postman

![](img/2020-04-03-14-15-00.png)

