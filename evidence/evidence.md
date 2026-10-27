# Project 3 — Multi-Agent RAG Ecommerce System

## Submission details

| Field | Value |
| --- | --- |
| GitHub account | fastbreakkkk |
| Repository | https://github.com/fastbreakkkk/multi-agent-rag-ecommerce-cd14764-project |
| AWS region | us-east-1 |

## 1. Project overview

This submission covers the NovaMart customer-support system: an OrchestratorAgent routes requests to InventoryAgent, RefundAgent, PolicyAgent, and CommunicationAgent. PolicyAgent coordinates three retriever sub-agents for returns, shipping, and warranty policies. The system uses DynamoDB workflow state, Bedrock Knowledge Bases with S3 Vectors, and an AgentCore Runtime deployment.

## 2. Automated test results

Command executed:

```bash
python tests/test_agent.py all
```

| Task | Area | Observed score | Result |
| --- | --- | --- | --- |
| Task 2 | Agent creation, tools, models, parallel retrieval | [SCORE]/40 | [PASS/FAIL] |
| Task 3 | Guardrails and AgentCore Runtime configuration | [SCORE]/20 | [PASS/FAIL] |
| Task 4 | AgentCore summary memory | [SCORE]/15 | [PASS/FAIL] |
| Task 5 | Knowledge Bases and retrieval | [SCORE]/25 | [PASS/FAIL] |
| Task 6 | CloudWatch and X-Ray configuration | [SCORE]/20 | [PASS/FAIL] |
| **Total** | **Full suite** | **[SCORE]/120** | **[PASS/FAIL]** |

Zero-point checks also passed: [YES/NO].

Failed checks or outstanding errors: [DESCRIBE, OR ENTER NONE].

### Required screenshot: full-suite results

![Automated test results and final score](evidence/01-tests-summary.png)

Additional test-result screenshots, if needed to show all PASS lines clearly: [ADD RELATIVE FILE LINKS, OR ENTER NONE].

Full terminal output: [OPTIONAL: LINK TO THE SAVED TEST LOG].

## 3. Required end-to-end scenarios

Command executed:

```bash
python src/agent_orchestrator.py test
```

### Scenario A — Return an order

- **Customer:** CUST-001
- **Request:** I want to return my wireless headphones from order ORD-27176.
- **Expected route:** Initialise session → Inventory → Refund → Communication.
- **Observed route:** [ENTER THE ACTUAL AGENTS/TOOLS CALLED].
- **Observed final answer:** [PASTE THE CUSTOMER-FACING RESPONSE].
- **Validation:** [CONFIRM WHETHER THE DECISION MATCHED THE ORDER DATE AND CUSTOMER TIER; INCLUDE THE ACTUAL RETURN REFERENCE IF ONE WAS CREATED].
- **Result:** [PASS/FAIL].

### Scenario B — Retrieve policy information

- **Customer:** CUST-002
- **Request:** What is the return policy for premium customers?
- **Expected route:** Initialise session → Policy → three parallel retriever sub-agents → Communication.
- **Observed route:** [ENTER THE ACTUAL AGENTS/TOOLS CALLED].
- **Retrieval evidence:** [DESCRIBE THE OUTPUT SHOWING RETURNS, SHIPPING, AND WARRANTY RETRIEVERS RUNNING IN PARALLEL].
- **Observed final answer:** [PASTE THE CUSTOMER-FACING RESPONSE].
- **Validation:** [CONFIRM WHETHER THE RESPONSE IS GROUNDED IN THE RETRIEVED POLICY AND IDENTIFIES THE PREMIUM 60-DAY RETURN WINDOW].
- **Result:** [PASS/FAIL].

### Scenario C — Calculate a discounted price

- **Customer:** CUST-003
- **Request:** How much would 5 items at $29.99 be with a 10% discount?
- **Expected route:** Initialise session → arithmetic → Communication, without Inventory, Policy, or Refund calls.
- **Expected amount:** $134.96 after rounding the full calculation.
- **Observed route:** [ENTER THE ACTUAL AGENTS/TOOLS CALLED].
- **Observed final answer:** [PASTE THE CUSTOMER-FACING RESPONSE].
- **Validation:** [CONFIRM THE AMOUNT, THAT NO UNNECESSARY WORKERS WERE CALLED, AND THAT THE GUARDRAIL ALLOWED THE CALCULATION].
- **Result:** [PASS/FAIL].

Optional scenario screenshots or saved terminal output: [ADD RELATIVE FILE LINKS, OR ENTER NONE].

## 4. Deployed-runtime verification

Command executed:

```bash
python src/agent_orchestrator.py invoke 'What is the return policy for premium customers?' CUST-002
```

- **Runtime status at verification:** [OBSERVED STATUS].
- **Observed response:** [PASTE THE DEPLOYED RUNTIME RESPONSE].
- **Result:** [PASS/FAIL].
- **Optional screenshot/log:** [RELATIVE FILE LINK, OR NONE].

## 5. Observability evidence

Live requests used to generate traces:

```bash
python src/agent_orchestrator.py test
```

| Field | Observed value |
| --- | --- |
| Trace generation date/time | [DATE, TIME, AND TIME ZONE] |
| Console region | us-east-1 |
| Map time range | [TIME RANGE THAT INCLUDES THE REQUESTS] |
| Example trace ID | [TRACE ID FROM THE LIVE RUN] |
| Orchestrator node | [OBSERVED NODE NAME] |
| Connected worker nodes | [OBSERVED WORKER NODES] |
| Connected Knowledge Base nodes | [OBSERVED KNOWLEDGE BASE NODES] |

### Required screenshot: X-Ray Service/Trace Map

![X-Ray map showing the orchestrator, workers, and Knowledge Base calls](evidence/02-xray-service-map.png)

The screenshot was captured from CloudWatch → X-Ray traces → Trace Map (called Service map in the project README).

Observed call-chain summary: [DESCRIBE THE VISIBLE ORCHESTRATOR → WORKER → KNOWLEDGE BASE CONNECTIONS].
