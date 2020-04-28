# 5. Thymeleaf CRUD DB Update Employees code

- copy `35-project` to `36-project`

![](img/2020-04-27-23-51-00.png)

- intellij open `36-project`

- add `update` button for `list-employee.html`

![](img/2020-04-27-23-55-01.png)

![](img/2020-04-28-00-04-30.png)

- update `list-employee.html`

```html
<!DOCTYPE HTML>
<html lang="en" xmlns:th="http://www.thymeleaf.org">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Employee Directory</title>
</head>

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
                <th>Action</th>
            </tr>
        </thead>

        <tbody>
            <tr th:each="tempEmployee : ${employees}">
                <td th:text="${tempEmployee.firstName}">
                <td th:text="${tempEmployee.lastName}">
                <td th:text="${tempEmployee.firstName}">

                <!-- Add update button/link -->
                <td>
                    <a th:href="@{/employees/showFormForUpdate(employeeId=${tempEmployee.id})}"
                        class="btn btn-info btn-sm">
                        Update
                    </a>
                </td>
            </tr>
        </tbody>
    </table>
</div>

</body>

</html>
```

![](img/2020-04-28-00-15-47.png)

![](img/2020-04-28-00-35-11.png)

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

    @GetMapping("/showFormForUpdate")
    public String showFormForUpdate(@RequestParam("employeeId") int theId,
                 Model theModel){
        //get the employee from the service
        Employee theEmployee = employeeService.findById(theId);

        //set employee as a model attribute to pre-populate the form
        theModel.addAttribute("employee", theEmployee);

        //send over to our form
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

- update employee-form.html

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

            <!-- Add hidden form field to handle update -->
            <input type="hidden" th:field="*{id}" />


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

- run app

![](img/2020-04-28-00-37-37.png)


- click `update`

![](img/2020-04-28-00-38-20.png)

![](img/2020-04-28-00-38-54.png)
![](img/2020-04-28-00-39-04.png)










