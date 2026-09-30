# Service Level Objectives (SLOs)

- **Core API Latency**
  - Target: 99% of standard CRUD requests should complete in under 300ms.
  - If missed: Make sure AI processing does not block Tomcat HTTP threads.

- **AI API Latency**
  - Target: 95% of AI parsing requests should complete in under 5 seconds.
  - If missed: Trip the circuit breaker and move the request to an async queue for background processing.

- **AI Availability**
  - Target: 99.9% of LLM calls should avoid errors.
  - If missed: Fail over to a secondary LLM provider.(llm model router)