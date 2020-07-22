# JSP_Servlets

### `Note: before run the servlet, connect to the database firstly`


:star: installing Tomact on Mac
- see my github SpringBoot folder's `environmentConfiguration.md`

![](img/2019-08-25-01-10-08.png)
![](img/2019-08-25-01-32-40.png)
- we see `startup.sh`
![](img/2019-08-25-01-33-46.png)
- we see `Tomcat started`

### Now, in my browser I can simply type `localhost:8080`
![](img/2019-08-25-01-35-31.png)

- shutdown Tomact Server

:star: What is a JSP file?
- An HTML page with some Java code sprinkled in ...
- Include dynamic content from Java code

:star: Where is the JSP processed?
- JSP is processed on the server
- Results of Java code included in HTML returned to browser
![](img/2019-08-25-02-06-00.png)

:star: Where to place JSP file?
- The JSP file goes in your WebContent folder
- Must have `.jsp` extension
![](img/2019-08-25-02-07-37.png)



:star: Connecting Eclipse(or Intellij Idea) and Tomact

- create a new `Java Enterprise` with `Java EE` -> Application Server: `Tomcat 8.5.42` -> `Web Application(4.0)`
![](img/2019-08-25-01-47-17.png)

- named this project `jspdemo`
![](img/2019-08-25-01-49-16.png)

- `Run` -> `Edit Configuration`
![](img/2019-08-25-01-51-35.png)

- `Templates` -> `Tomact Server` -> `+`
![](img/2019-08-25-01-56-21.png)

- create a File name: `hellowrld.jsp`
![](img/2019-08-25-02-24-25.png)
![](img/2019-08-25-02-27-25.png)

- run 
![](img/2019-08-25-03-18-59.png)
- this the result we expected


