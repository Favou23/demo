# Use Spring AI for LLM Integration

## Context and Problem Statement
We need an abstraction layer to connect to LLM providers so we do not hardcode vendor-specific software development kits into our backend.

## Considered Options
* Spring AI
* LangChain4j

## Decision Outcome
Chosen option: **Spring AI**. It integrates natively with Spring Boot's dependency injection and auto-configuration, reducing boilerplate code for our specific tech stack.

### Consequences
* Good, because it provides seamless model abstraction.
* Bad, because it is newer than LangChain4j and have a smaller community ecosystem.