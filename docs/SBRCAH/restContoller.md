# 9. REST Controller to find and add

![](img/2020-04-02-17-44-23.png)

![](img/2020-04-02-17-44-39.png)

![](img/2020-04-02-17-44-54.png)

![](img/2020-04-02-17-45-10.png)

![](img/2020-04-02-17-45-22.png)

![](img/2020-04-02-17-45-49.png)

![](img/2020-04-02-17-47-13.png)

![](img/2020-04-02-17-47-43.png)
---

- update controller

```java
@RestController
@RequestMapping("/api")
public class EmployeeRestController {

    private EmployeeService employeeService;

    //quick and dirty: inject employee dao
    @Autowired
    public EmployeeRestController(EmployeeService employeeService) {
        this.employeeService = employeeService;
    }

    //expose "/employees" and return list of employee
    @GetMapping("/employees")
    public List<Employee> findAll() {
        return employeeService.findAll();
    }

    //add mapping for GET /employees/{employeeId}
    @GetMapping("/employees/{employeeId}")
    public Employee getEmployee(@PathVariable int employeeId){

        Employee theEmployee = employeeService.findById(employeeId);
        if(theEmployee == null){
            throw new RuntimeException("Employee id not found - " + employeeId);
        }
        return theEmployee;
    }
}
```

- now let's test GET method by id

![](img/2020-04-02-18-00-36.png)

- OPEN Postman

![](img/2020-04-02-18-03-59.png)

- get all

![](img/2020-04-02-18-04-46.png)

---

- Post method:

```java

    //add mapping for POST / employees - add new employee
    @PostMapping("/employees")
    public Employee addEmployee(@RequestBody Employee theEmployee){
        //also jst in case they pass an id in JSON ... set id to 0
        //this is to force a save of new item ... instead of update
        theEmployee.setId(0);
        employeeService.save(theEmployee);
        return theEmployee;
    }

```

![](img/2020-04-02-18-12-59.png)

- chage to JSON

![](img/2020-04-02-18-14-36.png)

![](img/2020-04-02-18-14-54.png)

- success

![](img/2020-04-02-18-48-05.png)

























