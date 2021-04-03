## adding Data to Spring Model

![](img/2021-04-03-16-40-55.png)

![](img/2021-04-03-16-41-32.png)

#### Code Example

- We want to create a new method to process form data
- Read the form data: student’s name
- Convert the name to upper case
- Add the uppercase version to the model



![](img/2021-04-03-16-43-08.png)

![](img/2021-04-03-16-45-32.png)

![](img/2021-04-03-16-45-43.png)

![](img/2021-04-03-16-47-52.png)

![](img/2021-04-03-16-48-19.png)

---

![](img/2021-04-03-16-55-14.png)

- for `helloworld-form.jsp`, the param is `studentName`


- for controller, we have:

```java
	//new a controller method to read form data and
	//add data to the model
	@RequestMapping("/processFormVersionTwo")
	public String letsShoutDude(HttpServletRequest request, Model model) {
		
		//read the request parameter from the HTML form
		String theName = request.getParameter("studentName");
		
		//convert the data to all caps
		theName = theName.toUpperCase();
		
		//create the message
		String result = "Yo!" + theName;
		
		//add message to the model
		model.addAttribute("message", result);
		
		return "helloworld";
	}
}
```

![](img/2021-04-03-16-58-08.png)

![](img/2021-04-03-16-59-07.png)

![](img/2021-04-03-16-59-19.png)























