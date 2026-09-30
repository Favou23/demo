# Use gpt-oss-20b via Groq for Resume Parsing

## Context and Problem Statement
We need an LLM model capable of extracting structured JSON from unstructured text while balancing operational cost.

## Considered Options
* gpt-oss-20b (groq)
* gpt-4o
* gpt-4o-mini
* claude-3-haiku

## Decision Outcome
Chosen option: **gpt-oss-20b**. Resume extraction requires basic instruction following and JSON output, which smaller, cheaper models handle efficiently. this model via grop also offers lightning fast throughput at inference. Using a top-tier model like gpt-4o  or other considered options for this task wastes operational budget.

### Consequences
* Good, because it is fast and minimizes token costs.
* Good, because latency is much lower than heavy reasoning models.