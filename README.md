# AI Lab 05 — Real Model Evaluation with n8n

## Overview

This project demonstrates how to evaluate an AI-powered customer-message classifier using real OpenAI API responses, n8n automation, and structured performance metrics.

The goal is to measure classification accuracy while distinguishing model performance, evaluation coverage, and simulated API failure handling.

## Technologies

- n8n — workflow orchestration
- OpenAI GPT-4.1-mini — customer-message classification
- JavaScript — response parsing, validation, and evaluation
- JSON — structured model responses
- Markdown — automated evaluation reports

## Classification Task

The model classifies customer messages into four categories:

- **Billing:** Payments, invoices, refunds, and charges
- **Sales:** Pricing, purchases, plans, and licensing
- **Support:** Technical problems and troubleshooting
- **Other:** Messages outside the previous categories

The evaluation uses 15 manually labeled customer messages.

The model receives the customer message without the expected category.

## Evaluation Results

Two real-model executions produced the following results:

| Metric | Execution 1 | Execution 2 |
|---|---:|---:|
| Test cases | 15 | 15 |
| Correct predictions | 14 | 15 |
| Incorrect predictions | 1 | 0 |
| Classification accuracy | 93.33% | 100% |

The second execution's responses were pinned in n8n and reused to verify the evaluation and reporting pipeline without additional API requests.

### Final Report

- Classification accuracy: **100%**
- Evaluation coverage: **100%**
- Missing predictions: **0**
- Simulated API failures: **0**
- Unexplained missing predictions: **0**

These results describe a small, controlled experiment and do not establish production accuracy or reliability.

## Workflow Design

The n8n workflow:

1. Generates 15 labeled test cases.
2. Sends each customer message to GPT-4.1-mini.
3. Parses the model's JSON classification.
4. Compares predictions against expected categories.
5. Calculates accuracy and category-level precision, recall, and F1 scores.
6. Generates a confusion matrix.
7. Measures evaluation coverage.
8. Combines evaluation results with a simulated zero-failure summary.
9. Exports a Markdown evaluation report.

## API Failure Handling

The zero-failure branch is deliberately simulated.

Although real OpenAI API calls generated the classification predictions, this lab does not test genuine API outages, retries, or failure recovery.

Actual API reliability and latency require separate testing.

## Repository Files

- `AI_Lab_05_Real_Model_Evaluation_Public.json` — sanitized, importable n8n workflow.
- `AI_Lab_05_Real_Model_Evaluation_2026-11-12.md` — evaluation report generated from pinned real-model responses.
- `README.md` — project documentation.

## How to Reproduce

1. Import the public workflow JSON into n8n.
2. Configure your own OpenAI API credentials.
3. Review the GPT-4.1-mini model configuration and prompts.
4. Execute the workflow manually.
5. Inspect the classification metrics and exported Markdown report.

Running the OpenAI node makes billable API requests. The public workflow does not contain credentials or pinned model responses.

## Limitations

- Only 15 manually labeled test cases were evaluated.
- The dataset is not representative of real production traffic.
- Model outputs can vary between executions.
- Actual API errors and recovery mechanisms were not tested.
- Production deployment would require larger datasets, monitoring, error handling, and regression testing.

## Key Learning Outcomes

This project demonstrates practical experience with:

- LLM API integration
- Prompt engineering
- Structured response parsing
- AI evaluation metrics
- Workflow orchestration
- Evaluation coverage and reporting
- Reproducible testing

**Project status:** Completed educational evaluation with real GPT-4.1-mini predictions and simulated zero-failure handling.
