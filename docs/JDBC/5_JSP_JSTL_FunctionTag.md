### `JSP Standard Tag Library (JSTL) - Function Tags`

![](img/2019-08-26-09-23-27.png)
---

-  JSTL Functions - Prefix “fn”
![](img/2019-08-26-09-23-48.png)
---

-  JSTL Functions Reference
:star: Every page that uses the Function tags must include this reference

` <%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>`

- Code example:
![](img/2019-08-26-09-25-00.png)
---

- create `function-test.jsp`
```java
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>
<html>
<body>
<c:set var="data" value="luv2code" />
Length of the string <b>${data}</b>: ${fn:length(data)}

<br><br>
Uppercase version of the string <b>${data}</b>: ${fn:toLowerCase(data)}

<br><br>
Does the sting <b>${data}</b> start with <b>luv</b>?: ${fn:startsWith(data, "luv")}
</body>
</html>

```
![](img/2019-08-26-09-35-52.png)


### `JSTL Function Tags - Split and Join`

- Split function
![](img/2019-08-26-09-37-22.png)
---

- code example
![](img/2019-08-26-09-37-48.png)
---

- Join function
![](img/2019-08-26-09-38-08.png)
---

- code example
![](img/2019-08-26-09-38-46.png)
---

- create `split-join-test.jsp`
```java
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>
<html>
<body>

<c:set var="data" value="Singapore, Tokyo, Mubai, London"/>
<h3>Split Demo</h3>

<c:set var="citiesArray" value="${fn:split(data, ',')}"/>

<c:forEach var="tempCity" items="${citiesArray}"> 
    ${tempCity} <br>
</c:forEach>

<h3>Join Demo</h3>
<c:set var="fun" value="${fn:join(citiesArray,'*')}"/> 
Result of joining: ${fun}
</body>
</html>
```
![](img/2019-08-26-09-46-27.png)




