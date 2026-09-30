# Implement Regular-expression(regex)-Based PII distillation at AI Boundary

## Context and Problem Statement
Resumes contain Restricted Personally Idetifyable Informations (emails, phone numbers). We cannot legally or ethically send this data to a third-party LLM provider.

## Decision Outcome
We will implement a pre-processing scrubbing service at the AI Bounded Context entry point. Before any text is passed to Spring AI, Regex patterns will replace emails and phone numbers with `[REDACTED]`.

### Consequences
* Good, because it ensures compliance with our Data Classification
* Bad, because complex PII (like home addresses) might evade simple Regex 