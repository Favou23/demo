# Use PostgreSQL for Core Database

## Context and Problem Statement
We need a persistent data store for candidate records, job postings, and structured resume data.

## Considered Options
* PostgreSQL
* MongoDB

## Decision Outcome
Chosen option: **PostgreSQL**. The ATS domain requires strict relational integrity between candidates, job applications, and structured AI outputs. PostgreSQL also supports `pgvector` if we need to add embedding searches later.

### Consequences
* Good, because it enforces strict data integrity for the Core ATS boundary.
* Bad, because it requires managing explicit schema migrations (Flyway/Liquibase).