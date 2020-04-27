# 5. Thymeleaf-add Bootstrap CSS

![](img/2020-04-27-16-32-36.png)

![](img/2020-04-27-16-33-45.png)

![](img/2020-04-27-16-34-16.png)

![](img/2020-04-27-16-34-31.png)

![](img/2020-04-27-16-34-52.png)

---

- COPY 32-project, paste 33-project

![](img/2020-04-27-16-36-43.png)

- intellij open `33-project`

- open `33-project`

![](img/2020-04-27-16-38-27.png)

- import Bootstrap css

- input `getbootstrap` on google chrome

![](img/2020-04-27-16-39-55.png)

- click `get start`

![](img/2020-04-27-16-41-00.png)

- paste on our `list-employees.html`

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
```

## Step 3: Apply Bootstrap CSS styles

- update `list-employees.html`

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

- now let's testing Bootstrap CSS

- rerun `ThymeleafdemoApplication`

- OK, done!

![](img/2020-04-27-16-46-22.png)











