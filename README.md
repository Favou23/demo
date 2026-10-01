


# AI-Native HR Applicant Tracking System (ATS) Backend

## Project Overview

This repository contains the foundational architecture and initial Spring Boot scaffolding for an AI-Native HR Applicant Tracking System (ATS). It is developed as the Week 1 Advanced capstone deliverable for the flexisaf AI navive backend internship.

The system integrates Large Language Models (LLMs) to automatically parse unstructured candidate resumes into structured JSON data, significantly accelerating the recruitment pipeline. Crucially, the architecture establishes strict service boundaries and data classification rules to ensure candidate Personally Identifiable Information (PII) is scrubbed and never exposed to third-party AI providers.

## Architecture Pack Deliverables

This repository fulfills all technical strategy and architectural requirements for the week:

### 1. System & Data-Flow Diagrams

Visual representations of the bounded contexts, infrastructure, and data flow between the client, the Spring Boot modular monolith, the PostgreSQL database, and the external LLM provider.

* **View Architecture Diagrams (draw.io):** [https://drive.google.com/file/d/1YM9a4nwHHKB4I_QgDqPJI3y2qzWD3Aoa/view?usp=sharing (architectural decesion link )
https://drive.google.com/file/d/1VFWBnH_0UI2PZlWtH-CRAMUaPCSx5SWi/view?usp=sharing (DATA CLASSIFICATION)
]

### 2. API & Service-Boundary Map

* **Location:** `/docs/api-boundary-map.md`
* Defines the strict isolation between the Core ATS context (managing PostgreSQL transactions) and the AI Processing context (managing LLM network calls).

### 3. Data Classification & SLOs

* **Data Classification Matrix:** Located in `/docs/data-classification.md`. Details the redaction rules for Restricted PII prior to AI processing.
* **SLO Targets:** Located in `/docs/slo-targets.md`. Outlines latency caps, availability targets, and circuit-breaker fallback mechanisms.

### 4. Architecture Decision Records (ADRs)

Five formal MADR-compliant records documenting the core technical trade-offs, located in `/docs/adrs/`:

* `0001-database-selection.md`
* `0002-ai-framework-selection.md`
* `0003-data-classification-strategy.md`
* `0004-slo-and-failure-modes.md`
* `0005-llm-model-strategy.md`

## AI Practice Requirement & Decision Log

The architectural decisions, bounded contexts, and system design were developed using a human-in-the-loop AI collaboration model. The AI acted as a sounding board for evaluating framework trade-offs and verifying enterprise design patterns.

* **Complete AI Prompt & Verification Log:** [View the Gemini Chat Session](https://share.gemini.google/N3TSb8RVB2Ln)

**Process Documentation:**
Throughout the design phase, raw AI outputs were critically evaluated against the specific constraints of the flexisaf AI navive backend internship.

* **Verification:** AI-suggested endpoint structures were manually refactored to ensure strict package-level and database-level isolation between the Core ATS logic and the AI integration layer.
* **Human Review Evidence:** Generic LLM recommendations (such as returning static fallback text during an outage) were rejected in favor of designing a robust, asynchronous queueing mechanism in PostgreSQL to preserve data integrity. All final architecture choices documented in the ADRs are human-approved and tailored specifically to the ATS domain.

## Tech Stack

* **Backend Framework:** Java / Spring Boot
* **Database:** PostgreSQL (Spring Data JPA)
* **AI Integration:** Spring AI
* **Resilience:** Resilience4j (Circuit Breakers)
* **Build Tool:** Maven

## Getting Started

1. Clone the repository and checkout the `week-25` tag.
2. Ensure PostgreSQL is running locally on port `5432` with a database named `ats_core`.
3. Configure your LLM API key in `src/main/resources/application.properties`:
`spring.ai.openai.api-key=YOUR_API_KEY`
4. Build and run the application via `mvn spring-boot:run`.