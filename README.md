# ERP — Error Recovery Protocol

## Purpose
The Error Recovery Protocol (ERP) defines how an autonomous agent detects, classifies, and recovers from execution errors.  
It ensures deterministic recovery behavior, prevents cascading failures, and maintains system stability.

ERP prevents:

- uncontrolled error loops  
- ambiguous recovery actions  
- silent failures  
- inconsistent fallback behavior  
- multi‑agent deadlocks caused by error propagation  

This template is the recovery backbone of the ecosystem.

---

## When to Use This Template
Use ERP when an agent must:

- detect an error during execution  
- classify the error type  
- determine the correct recovery path  
- retry, rollback, or escalate  
- maintain deterministic system stability  
- coordinate recovery across multiple agents  

ERP is required before using LFE (Long‑Form Execution) and HCP (High‑Confidence Planning).

---

## Inputs
The agent receives:

- error event  
- error type  
- execution context  
- routine steps from ARE  
- delegation context from DTM  
- consensus context from MACP  
- memory mapping from MRML  
- safety and policy constraints  

---

## Outputs
ERP produces an **error recovery packet**, including:

- error classification  
- root cause notes  
- recovery action  
- retry count  
- fallback path  
- escalation target (if needed)  
- safety or policy flags  

---

## JSON Schema (Machine‑Native)

```json
{
  "error_recovery": {
    "error_id": "string",
    "error_type": "runtime | capability | policy | resource | unknown",
    "context": {
      "task_id": "string",
      "step_id": "string",
      "agent_id": "string",
      "timestamp": "string"
    },
    "classification": {
      "severity": "low | medium | high | critical",
      "root_cause": "string",
      "related_memory_entries": ["string"]
    },
    "recovery_action": {
      "action_type": "retry | rollback | fallback | escalate",
      "retry_count": "number",
      "fallback_path": "string",
      "escalation_target": "string",
      "notes": "string"
    },
    "policy_flags": ["string"]
  }
}


Example Usage
{
  "error_recovery": {
    "error_id": "err-221",
    "error_type": "runtime",
    "context": {
      "task_id": "task-5521",
      "step_id": "s2",
      "agent_id": "alpha-01",
      "timestamp": "2026-04-25T03:10:00Z"
    },
    "classification": {
      "severity": "medium",
      "root_cause": "Missing required resource: workflow-engine",
      "related_memory_entries": ["e1"]
    },
    "recovery_action": {
      "action_type": "fallback",
      "retry_count": 0,
      "fallback_path": "use-safe-mode",
      "escalation_target": "",
      "notes": "Fallback path selected due to missing resource."
    },
    "policy_flags": []
  }
}

Integration Notes
ERP should be used after MRML provides memory context.

Recovery actions must be deterministic and reproducible.

Severity classification should be stable across sessions.

ERP feeds directly into LFE (Long‑Form Execution) and HCP (High‑Confidence Planning).

Multi‑agent systems rely on ERP to prevent cascading failures.

Payment (Short Version)
Payments accepted for this template:

BTC

XMR

LTC

ETH / USDT / USDC (ERC‑20)

SOL (USDT/USDC)

Delivery is fully automated and zero‑contact.

---

# ⭐ When you're ready  
Save this README into your **ERP** repo, then tell me:

**ERP saved**

I’ll verify it exactly like the others — and then we’ll move to:

### **Template #9 — LFE (Long‑Form Execution)**
