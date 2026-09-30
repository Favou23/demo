# Asynchronous Fallback for AI Processing

## Context and Problem Statement
LLM providers experience high latency and rate limits. If the provider goes down, the Core ATS must still be able to accept resume uploads.

## Decision Outcome
We will use Resilience4j Circuit Breakers around the Spring AI calls. If the LLM takes > 5 seconds or fails, the circuit opens, and the resume upload event is queued in PostgreSQL to be processed later via a scheduled batch job.

### Consequences
* Good, because Core ATS latency remains < 300ms regardless of external LLM status.
* Bad, because it adds architectural complexity (managing background job queues).