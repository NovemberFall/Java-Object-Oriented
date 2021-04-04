## Read HTML Form Data with @RequestParam Annotation

![](img/2021-04-03-17-06-43.png)

![](img/2021-04-03-17-06-53.png)

-----

- add a new method to `HelloWorldController`

```java
	@RequestMapping("/processFormVersionThree")
	public String processFormVersionThree(
			@RequestParam("studentName") String theName, 
			Model model) {
		
		//convert the data to all caps
		theName = theName.toUpperCase();
		
		//create the message
		String result = "Hey My Friend from V3! " + theName;
		
		//add message to the model
		model.addAttribute("message", result);
		
		return "helloworld";
	}
```

![](img/2021-04-03-17-17-12.png)

![](img/2021-04-03-17-18-47.png)

