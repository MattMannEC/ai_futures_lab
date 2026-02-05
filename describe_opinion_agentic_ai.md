# Controversial Opinion on Agentic AI

> **"Most LLM-based agentic systems today could be implemented more simply as deterministic workflows."**

I'm not anti-agentic—but I believe we're over-applying autonomy where it isn't needed.

---

## The Core Argument

### 🎯 Reliability First
When the workflow is known in advance, **predictable, repeatable behavior** often matters more than autonomy. Reliability should be the default priority.

### ⚠️ Premature Architecture Decisions
Too often, the decision to build an autonomous agentic system is made *before* a proper business requirements analysis identifies the best solution. The result?

- Deterministic workflows get encoded into system prompts
- Systems become **more resource-intensive**
- Reliability **decreases**, despite having no genuine autonomy requirement

### 🔧 Right-Sized Intelligence
When some autonomy is needed, an LLM can often be replaced with a **smaller, bespoke intelligent component** designed specifically for the task. These components may have a higher upfront setup cost, but they typically offer much lower long-term cost and improved reliability.

## Plan of Action
### Phase 1: Corpus Analysis (Testing H1)

**Objective:** Quantify how much "agentic" code is actually deterministic logic.

**Method:**
1. Collect 50+ real-world agent implementations (GitHub repos, published case studies, open-source projects)
2. Two independent reviewers classify each instruction in system prompts:
   - **Type A:** Deterministic rule ("If the user asks about pricing, respond with X")
   - **Type B:** Constraint/guardrail ("Never discuss competitors")
   - **Type C:** Genuine reasoning delegation ("Assess the user's intent and respond appropriately")
3. Calculate the **Determinism Ratio**: `(Type A instructions) / (Total instructions)`

**Success criterion:** If >60% of instructions across the corpus are Type A, H1 is supported.

**Controls:**
- Inter-rater reliability (Cohen's kappa >0.7)
- Stratified sampling across domains (customer service, data processing, coding, etc.)

---

### Phase 2: Comparative Implementation (Testing H2)

**Objective:** Compare performance of agent vs. deterministic implementations on identical tasks.

**Method:**

1. **Select 5 representative tasks** with known, documentable workflows:
   - Document classification and routing
   - Form validation and data extraction
   - FAQ response with escalation logic
   - Multi-step data transformation
   - Approval workflow with conditional routing

2. **Build three implementations for each task:**
   - **Agent:** LLM with system prompt encoding the workflow
   - **Deterministic:** Traditional decision tree / state machine
   - **Hybrid:** Deterministic core with LLM fallback for ambiguous cases

3. **Create standardized test datasets:**
   - 100 "happy path" cases (clear, expected inputs)
   - 50 "edge cases" (valid but unusual inputs)
   - 50 "adversarial cases" (attempts to deviate from workflow)
   - Ground truth labels established by human expert consensus

4. **Measure:**

| Metric | Definition |
|--------|------------|
| **Accuracy** | % of outputs matching ground truth |
| **Consistency** | Same input → same output (run 10x, measure variance) |
| **Latency** | p50 and p99 response times |
| **Cost** | $ per 1,000 executions |
| **Robustness** | Accuracy on adversarial cases |
| **Maintainability** | Time to implement a logic change (measured via developer study) |

**Success criterion for H2:** Deterministic implementation achieves:
- ≥95% accuracy of agent on happy path
- Higher consistency (lower variance)
- Lower cost and latency
- Higher robustness to adversarial inputs
