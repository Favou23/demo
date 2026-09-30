# Decision Log


### Prompt Log

> what is an api boundry map

> WHAT OF IN A CASE WHERE vector stoes are used ? also just to make this cleares as possibe, apart fromdefining the urls or endpoints to boundaries, what exactly makes thouse url isolated or sets the boundaries or limits it can go, is it solely the kind of data it can exchange? and also how is this implemennted i code can you give an example so this can be clearer also what are the cases where the endpoints are not isolated and what are their example cases

### AI-Output Verification

The output explained that an API boundary is not created by the URL alone. It is also defined by service/process isolation, data ownership, and the contract between the services.

### Human Review Evidence

I checked the explanation against the example architecture and confirmed that the main application should not directly access the vector store's internal database or implementation when a separate service boundary is being used.



### Prompt Log

> what are SLOs in SWE

> what is the software industry stadard latency speed for CRUD operations in a software system ?

### AI-Output Verification

The output explained SLOs as measurable reliability and performance targets and introduced latency percentiles such as P50, P95, and P99 instead of relying only on average latency.

### Human Review Evidence

I researched and checked the latency guidance and confirmed that there is no single universal CRUD latency standard. The final targets were therefore treated as engineering SLOs for the system rather than fixed industry rules.



### Prompt Log

> how do i integrate resilience4java into a project for fault tolerance

> expaiin the cocept of tomcat http thread for me

> which ai inference layer is best compatible with spring boot beteen langchain4j and spring ai

### AI-Output Verification

The output explained the use of Resilience4j patterns such as circuit breakers, retries, time limiters, and bulkheads. It also explained how long-running AI requests can occupy Tomcat worker threads and lead to thread starvation.

### Human Review Evidence

I checked the Resilience4j approach against the Tomcat thread model and confirmed that long-running external AI calls should be controlled with timeouts and resilience mechanisms so they do not unnecessarily consume HTTP worker threads. I also reviewed the Spring AI and LangChain4j comparison before selecting the AI integration approach.