# Overall Architecture Style Analysis


## Identified key architectural characteristics

Key characteristics are quality attributes that describe our system, there are many characteristics but not all of them can be satisfied perfectly. By identifying key characteristics of our system we can focus on these requirements when making important decisions.

| Characteristic | Reason                                                                                                                                                                                                              |
| -------------  |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Cost           | Since this project is completely sponsored by non-profit agency our hard requirement is lower costs                                                                                                                 |
| Elasticity     | In our system we expect high changes in workloads due to different events so we need system that can easily adapt to changing workloads                                                                             |
| Performance    | System uses client's current location to match them with police officers and since locations can change rapidly we need to have great performance so clients don't experience any latencies                         |
| Scalability    | System expect large amount of users and connections - more than a billion client interactions yearly, so our architecture has to be scalable in order to easily adapt to large interaction increases                |

## Architecture comparison

![Architecture characteristics](diagrams/pictures/architecture-characteristics.png)

[original comparison matrix from [DeveloperToArchitect.com](https://www.developertoarchitect.com/downloads/worksheets.html)]

By comparing two architectures we can see that most suitable architecture would be space based, but it lacks cost efficiency which is our hard requirement and 
one of, if not the most important, characteristic. Second best would be event driven or microservices architecture which have same issues with costs. Keeping 
that in mind we decided to mitigate that by using service based architecture. It provides us with great cost while maintaining good scalability and performance, 
our only issue remains with elasticity, but we will use some of the characteristics of space based architecture to mitigate it.

## ADR

[ADR Use service based architecture](./ADRs/ADR-001.md)
