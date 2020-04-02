# 11. Injecting Custom App properties

![](img/2020-04-02-02-30-55.png)

![](img/2020-04-02-02-31-22.png)

![](img/2020-04-02-02-31-36.png)

![](img/2020-04-02-02-36-35.png)

![](img/2020-04-02-02-37-11.png)

- update `resources/application.properties`

```json
#
# Define my crazy properties
#
coach.name = Mickey mouse
tem.name = The Mouse Club
```

![](img/2020-04-02-02-46-14.png)

- update FunRestController

```java
@RestController
public class FunRestController {

    // inject properties for: coach.name and team.name

    @Value("${coach.name}")
    private String coachName;

    @Value("${team.name}")
    private String teamName;

    // expose new endpoint for "teamInfo"
    @GetMapping("/teamInfo")
    public String getTeamInfo(){
        return "Coach: " + coachName + ", Team name: " + teamName;
    }


    // expose "/" that return "Hello World"
    @GetMapping("/")
    public String sayHello(){
        return "Hello World! Time on server is " + LocalDateTime.now(); //Current time stamp
    }

    //expose a new endpoint for "workout"
    @GetMapping("/workout")
    public String getDailyWorkout(){
        return "Run a hard 5k...!";
    }

    //expose a new endpoint for "fortune"
    @GetMapping("/fortune")
    public String getDailyFortune(){
        return "Today is Sunny day!";
    }
}
```


























