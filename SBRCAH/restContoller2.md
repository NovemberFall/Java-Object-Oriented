# 10. REST Controller Update and Delete

![](img/2020-04-02-23-21-44.png)

![](img/2020-04-02-23-22-03.png)

![](img/2020-04-02-23-22-21.png)

![](img/2020-04-02-23-22-34.png)

![](img/2020-04-02-23-24-28.png)

- update EmployeeRestController

```java
    //add mapping for PUT / employees - update existing employee
    @PutMapping("/employees")
    public Employee updateEmployee(@RequestBody Employee theEmployee){
        employeeService.save(theEmployee);
        return theEmployee;
    }
```

![](img/2020-04-02-23-30-16.png)

![](img/2020-04-02-23-31-27.png)

![](img/2020-04-02-23-32-22.png)

---

![](img/2020-04-02-23-35-26.png)

- update EmployeeRestController

```java
    //add mapping for DELETE /employees/{employeeId} - delete employee
    @DeleteMapping("/employees/{employeeId}")
    public String deleteEmployee(@PathVariable int employeeId){
        Employee tempEmployee = employeeService.findById(employeeId);

        //throw exception if null
        if(tempEmployee == null){
            throw new RuntimeException("Employee id not found - " + employeeId);
        }
        employeeService.deleteById(employeeId);
        return "Delete employee id - " + employeeId;
    }
```

![](img/2020-04-02-23-42-09.png)

![](img/2020-04-02-23-42-31.png)

![](img/2020-04-03-00-00-50.png)

![](img/2020-04-03-00-02-23.png)

- let's delete id=5

![](img/2020-04-03-00-03-09.png)

![](img/2020-04-03-00-03-22.png)

