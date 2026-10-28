# Project evidence

## Automated tests

Command: `python tests/test_agent.py all` — **120/120 points**.

- [Tasks 2–5 passing](test-pass-evidence1.png)
- [Parallel KB retrieval](test-pass-evidence-2.png)
- [Task 6 and final 120/120 score](test-pass-evidence-3.png)

## AgentCore deployment

- [Active runtime, HTTP/Public configuration, guardrail version 2](agentcore-runtime-evidence.png)

## Knowledge Bases

| Knowledge Base | Configuration | Completed sync |
| --- | --- | --- |
| Returns | [KB, Titan v2, S3 Vectors index](returns-kb-evidence.png) | [Sync complete](returns-sync-evidence.png) |
| Shipping | [KB, Titan v2, S3 Vectors index](shipping-kb-evidence.png) | [Sync complete](shipping-sync-evidence.png) |
| Warranty | [KB, Titan v2, S3 Vectors index](warranty-kb-evidence.png) | [Sync complete](warranty-policy-sync-evidence.png) |

## Configuration

- [config.py output](config.py-evidence.png)
- [Active runtime with guardrail version 2](agentcore-runtime-evidence.png)

## Live scenarios

- Return: [Step 01](step1.png), [Step 02](step2.png), [Step 03](step3.png), [response and trace](step3-2.png)
- Policy: [Step 04](step4.png), [retrieval 1](step4-2.png), [retrieval 2](step4-3.png), [Step 05](step5.png), [response and trace](step5-2.png)
- Calculation: [Step 06 and $134.96 response](step6-calculation-refund.png)

## X-Ray

- [Full Trace Map: orchestrator, workers, and three Knowledge Bases](full-x-ray-tracemap.png)
- [Policy request spans](x-ray-trace-evidence.png)
- [Policy request trace graph](x-ray-map-evidence.png)