# 3. Thymeleaf CRUD DB Add Employees code

- copy `34-project` to `35-project`

![](img/2020-04-27-22-39-14.png)

![](img/2020-04-27-22-43-38.png)

![](img/2020-04-27-22-43-56.png)

![](img/2020-04-27-22-44-54.png)

![](img/2020-04-27-22-45-09.png)

![](img/2020-04-27-22-45-46.png)

![](img/2020-04-27-22-46-14.png)

![](img/2020-04-27-22-46-53.png)

![](img/2020-04-27-22-46-59.png)

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

        return "employees/list-employees";
    }
}
```

- run ThymeleafdemoApplication 

![](img/2020-04-27-22-50-05.png)

![](img/2020-04-27-22-50-31.png)

![](img/2020-04-27-22-50-55.png)

- update `list-employees.html`

```html
<body>

<div class="container">
    <h3>Employee Directory</h3>
    <hr>

    <!-- Add a button   -->
    <a th:href="@{/employees/showFormForAdd}"
        class="btn btn-primary btn-sm mb-3">
        Add Employee
    </a>

    <table class="table table-bordered table-striped">
        <thead class="thead-dark">
            <tr>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Email</th>
            </tr>
        </thead>

        <tbody>
            <tr th:each="tempEmployee : ${employees}">
                <td th:text="${tempEmployee.firstName}">
                <td th:text="${tempEmployee.lastName}">
                <td th:text="${tempEmployee.firstName}">
            </tr>
        </tbody>
    </table>
</div>

</body>

</html>
```

![](img/2020-04-27-22-54-07.png)

![](img/2020-04-27-22-54-50.png)

![](img/2020-04-27-23-04-02.png)

![](img/2020-04-27-23-04-47.png)

![](img/2020-04-27-23-05-02.png)

- update EmployeeController.java

```java
package com.luv2code.springboot.thymeleafdemo.controller;

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

        return "employees/list-employees";
    }

    @GetMapping("/showFormForAdd")
    public String showFormForAdd(Model theModel) {
        //create model attribute to bind form data
        Employee theEmployee = new Employee();

        theModel.addAttribute("employee", theEmployee);

        return "employees/employee-form";
    }
}

```

![](img/2020-04-27-23-05-37.png)

- copy from `list-employees.html`, paste to `employee-form.html`

![](img/2020-04-27-23-11-27.png)

![](img/2020-04-27-23-14-23.png)

- Add a navigation link at botton of page

- update `employee-form.html`

```html
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Save Employee</title>
</head>

<body>

    <div class="container">
        <h3>Employee Directory</h3>
        <hr>
        <p class="h4 mb-4">Save Employee</p>
        <form action="#" th:action="@{/employees/save}"
                        th:object="${employee}" method="POST">
            <input type="text" th:field="*{firstName}"
                   class="form-control mb-4 col-4" placeholder="First Name">

            <input type="text" th:field="*{lastName}"
                   class="form-control mb-4 col-4" placeholder="Last Name">

            <input type="text" th:field="*{email}"
                   class="form-control mb-4 col-4" placeholder="Email">

            <button type="submit" class="btn btn-info col-2">Save</button>
        </form>

        <hr>
        <a th:href="@{/employees/list}">Back to Employees List</a>
        
    </div>

</body>

</html>
```

- test app

- click `Add Employee` button

![](img/2020-04-27-23-17-47.png)

- successfully!

![](img/2020-04-27-23-22-25.png)

- update `employeeController.java`

```java
package com.luv2code.springboot.thymeleafdemo.controller;

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

        return "employees/list-employees";
    }

    @GetMapping("/showFormForAdd")
    public String showFormForAdd(Model theModel) {
        //create model attribute to bind form data
        Employee theEmployee = new Employee();

        theModel.addAttribute("employee", theEmployee);

        return "employees/employee-form";
    }

    @PostMapping("/save")
    public String saveEmployee(@ModelAttribute("employee") Employee theEmployee) {
        //save the employee
        employeeService.save(theEmployee);

        //use a redirect to prevent duplicate submissions
        return "redirect:/employees/list";
    }
}

```

- rerun app

![](img/2020-04-27-23-24-44.png)

- click save

![](img/2020-04-27-23-24-57.png)

- success!

![](img/2020-04-27-23-25-38.png)

![](img/2020-04-27-23-26-04.png)

- update 

![](img/2020-04-27-23-26-59.png)

![](img/2020-04-27-23-27-43.png)

![](img/2020-04-27-23-28-37.png)

![](img/2020-04-27-23-29-40.png)

- update `EmployeeServiceImplementation` and `EmployeeRepository`

![](img/2020-04-27-23-33-26.png)
![](img/2020-04-27-23-34-31.png)

- rerun app

![](img/2020-04-27-23-35-27.png)

- now sorting by last name with acending order

![](img/2020-04-27-23-36-31.png)
![](img/2020-04-27-23-36-41.png)














