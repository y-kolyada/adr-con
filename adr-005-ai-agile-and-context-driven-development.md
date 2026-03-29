# ADR-005: Use AI-Agile Delivery with Documentation as Operational Context

## ✅ Status: Accepted

**AI Studio / AI Model:**

- AI Engineer
- Gemini Apps / Gemini 3 Fast
- VS Code / GPT-5.4
- Antigravity / Claude Opus 4.6 Thinking
- AI Engineer

**Documentation:**

- [adr-005-ai-agile-and-context-driven-development.md](./adr-005-ai-agile-and-context-driven-development.md)

---

**TOC:**

- [ADR-005: Use AI-Agile Delivery with Documentation as Operational Context](#adr-005-use-ai-agile-delivery-with-documentation-as-operational-context)
  - [✅ Status: Accepted](#-status-accepted)
  - [1. Context](#1-context)
  - [2. Decision](#2-decision)
  - [3. Rationale](#3-rationale)
    - [Why working context matters in AI-assisted delivery](#why-working-context-matters-in-ai-assisted-delivery)
    - [Why proportionality matters](#why-proportionality-matters)
    - [Why documentation is an accelerator, not a brake](#why-documentation-is-an-accelerator-not-a-brake)
    - [Why this is still Agile](#why-this-is-still-agile)
    - [Documentation as extended mind](#documentation-as-extended-mind)
  - [4. Consequences](#4-consequences)
    - [Positive](#positive)
    - [Negative](#negative)
    - [Neutral but important](#neutral-but-important)
  - [5. Rejected Alternative](#5-rejected-alternative)
    - [Alternative: treat documentation as a passive byproduct and rely mainly on transient chat context](#alternative-treat-documentation-as-a-passive-byproduct-and-rely-mainly-on-transient-chat-context)
    - [Alternative: minimize documentation to honor the Agile Manifesto literally](#alternative-minimize-documentation-to-honor-the-agile-manifesto-literally)
  - [6. Review Trigger](#6-review-trigger)
  - [7. Git Commit](#7-git-commit)

---

## 1. Context

The Agile Manifesto (2001) was written in a world where "documentation" meant hundreds of pages of specifications that took months to write, were outdated by the time they were delivered, and were difficult for people to read. Its second principle — "Working software over comprehensive documentation" — was a reaction to that overhead.

Modern AI-assisted development changes the equation fundamentally. AI Models generate code in seconds, but they cannot deliver a working product without clear boundaries, structured scope, and preserved intent. Without documentation, the AI model drifts into hallucination, unbounded refactoring, or architectural inconsistency as the project grows.

Right now, it's hard to say whether a feature (or product) was born from documentation (context) or whether documentation was born from development. And this is a key pain point in modern AI-assisted development.

It's an interconnected and interdependent process. Documentation is part of a successful AI-assisted delivery model.

As part of delivery model, the repository may contain:

- **Implementation plans** with explicit scope, step structure, verification checklists, and success criteria
- **Per-step delivery records** documenting what each step changed, checked, and committed
- **ADRs** preserving architectural intent across agents, studios, and model switches
- **Live indexes** (`000-project-documentation.md`, `000-project-commit-history.md`) maintaining navigation and audit continuity

The volume of documentation may appear to violate the Agile principle of preferring working software over comprehensive documentation. In practice, it does the opposite: the documentation is the mechanism that makes working software reliably deliverable in an AI-assisted workflow.

Three observations from the repository's development history make the need for this ADR concrete:

1. **Context degradation is the main failure mode.** As the project grows, AI Models lose track of established patterns, architectural boundaries, and verified behavior unless the context is explicitly preserved and structured Transient chat context is not a reliable long-term operating memory for multi-step work. Switching between AI Models or AI Studios becomes much safer when intent is preserved in repository documents rather than trapped in one conversation.

2. **Documentation and development are interdependent.** It is hard to say whether a feature was born from documentation or documentation was born from development. The implementation plan shapes the code, and the code shapes the step records. They are an interconnected process.

3. **The `AI Engineer` is the conductor, not the coder.** The human designs meaning, verifies results at every step, manages the process in real time or even re-plans — rather than waiting for a miracle at the end of one big run. Documentation is the score that the `AI Orchestra` follows. AI tools produce code quickly but depend heavily on clear boundaries, current architecture, and durable execution context. Human review remains necessary, but the human role shifts further toward directing, validating, and correcting an accelerated implementation loop.

> **AI Orchestra:** AI Agents powered by AI Models + AI Engineers powered by AI Agents

Over time, the repository will contain validated implementation plans, per-step records, verification loops, and architectural notes can improve delivery quality and portability across AI tools.

At the same time, not every task deserves the same documentation weight.

If AI-assisted delivery interprets "documentation" as a requirement to write a heavy design stack for every small change, the process becomes too expensive and stops being agile in practice.

What needs to be made explicit is the **AI process rule** behind the existing practice:

- documentation for AI-assisted delivery is operational context, not passive archive
- that context must stay proportional to the complexity, ambiguity, verifiability (by the AI Engineer), and boundary risk of the work

---

## 2. Decision

The evolution can be stated as:

| Old Agile (2001) | AI-Agile (2026) |
| :--- | :--- |
| Working product is more important than comprehensive documentation | Working context is the key to delivering a working and verified product |
| Documentation is a brake | Documentation is an accelerator and navigator for AI Agents and AI Engineers |

This approach is described as **AI-Agile (A2)** / **AI-Augmented Agile (A3)** or **Context-Driven Development (CDD)**: an evolution of the Agile Manifesto's second principle adapted to AI-speed code generation.

**AI-Agile means:**

1. keep working software as the primary delivery goal
2. documentation is not a byproduct of development — it is a co-product that makes AI-generated code reliably correct
3. structured documentation (implementation plans, step records, ADRs, live indexes) is part of the **AI development toolkit**, as important as the AI Studios, compilers, or AI Models used by AI Agents
4. each implementation step produces both code and a durable delivery record, forming a mini-iteration with verification and a git commit
5. treat maintained documentation as operational context that allows the `AI Engineer` to quickly understand and re-plan the implementation at the current step
6. documentation preserves `AI Engineer` intent across AI Model switches, studio switches, and context-window boundaries
7. preserve enough repository-local context that work can be resumed, reviewed by the `AI Engineer` and another AI Model, or handed between AI Models and AI Studios without depending on one transient chat thread
8. the `AI Engineer` orchestrates the AI through documented scope, boundaries, and verification criteria rather than relying on unstructured conversation

**Operational rules:**

1. require that the amount of documentation stay proportional to the size and risk of the work
2. for small and local changes, use the minimum documentation needed to keep the change understandable and auditable
3. for substantial multi-step work, use a maintained implementation plan and focused per-step records as defined by ADR-003 and ADR-004
4. for architecture-heavy, cross-boundary, or ambiguity-prone work, escalate to stronger design artifacts such as defined by ADR-101 (ADR, SRS, HLD, ICD, or LLD) only when those documents materially reduce execution risk
5. do not create heavyweight design artifacts by default when the simpler workflow is sufficient
6. keep verification inside the same delivery loop as code and documentation so AI output is checked incrementally rather than trusted as a single large run
7. record repository boundaries, architectural direction, and downstream impacts when those details are necessary to keep AI-generated work constrained and portable
8. treat the human `AI ​​engineer` as the responsible conductor of the workflow: choosing scope, reviewing output, and correcting direction continuously

This ADR therefore interprets the Agile documentation principle in AI-assisted work as follows:

- avoid documentation that exists only for formality
- preserve documentation that materially improves execution quality, context continuity, portability, re-planning and verification

---

## 3. Rationale

This ADR defines the delivery-governance principles for AI-assisted development.

### Why working context matters in AI-assisted delivery

1. AI tools are fast, but context-sensitive.

    Without an accurate repository boundary, architecture direction, or step scope, an AI Model is more likely to hallucinate, over-refactor, or solve the wrong problem cleanly.

2. Durable intent is now part of the implementation system.

    In this workflow, the implementation plan and step documents are not retrospective reports. They are part of the mechanism that keeps work coherent across multiple iterations.

3. Portability is a real engineering property.

    If the repository preserves enough execution context, work can move between sessions, reviewers, AI Models, and AI Studios with less loss of intent. That reduces process fragility.

4. `AI ​​engineer` oversight becomes more effective when the work is sliced.

    AI-assisted delivery is safer when the `AI ​​engineer` validates each step, verification result, and downstream implication instead of reviewing only a final large output.

### Why proportionality matters

`AI-Agile` is not a license for maximum documentation.

The repository needs a proportionality rule because two opposite failure modes are possible:

1. Too little documentation leaves the AI without stable context and pushes important intent into ephemeral chat history.
2. Too much mandatory documentation for ordinary work turns agility into bureaucratic drag, and it is difficult for an `AI Engineer` to verify the generated implementation plan and the results obtained.

The correct balance is to scale documentation to the real uncertainty of the task.

**That means:**

1. Simple local work can stay light, but there must remain an audit trail and verification.
2. Multi-step approach to implementation or migration projects benefits from maintained implementation records.
3. Cross-boundary design work may justify ADR, SRS, HLD, ICD, or LLD artifacts when the extra precision prevents rework or ambiguity.

### Why documentation is an accelerator, not a brake

1. **AI models need structured boundaries.**

   Implementation plan sections like `Repository Boundary`, `OOP Class Architecture`, and `Implementation Scope` or `Migration Scope` are the "rails" that prevent the model from hallucinating or devolving into refactoring for the sake of refactoring. Without them, every new conversation starts from zero.

2. **Context accumulation enables forward progress.**

   Each step document builds on the previous context. The AI model can pick up where the last step left off because the scope, decisions, and verification results are explicitly captured. This eliminates the "amnesia" problem that plagues long AI-assisted projects.

3. **Proportional effort at AI speed.**

   A human developer would take days to write the documentation this repository produces per step. An AI agent generates it in minutes. The ratio of documentation effort to development effort remains proportional — and at AI speed, the documentation cost is negligible compared to the value it provides.

### Why this is still Agile

1. **Sprints within steps.** Each implementation step is a mini-iteration: scope → implementation → verification → commit. This is Agile iterativity at a granular level.

2. **Responding to changes.** If a step reveals that the architecture is not working, the plan is adjusted and the AI immediately picks up on the changes. The documentation enables agility rather than preventing it.

3. **Continuous delivery.** Documentation is not accumulated for its own sake. It is immediately consumed as context for the next step's code generation. There is no gap between documenting and shipping.

4. **People and interactions.** The interaction between human and AI occurs through these documents. Without structured documentation, the Human-in-the-Loop process control turns into chaos.

### Documentation as extended mind

1. **Extended mind.** For the AI model, the implementation plan is not a bureaucratic report but a structured contextual window — an **extended mind** that compensates for the model's limited context window and lack of project memory.

2. **Portability problem.** This also solves the **portability problem**: traditional Agile often stores context in developers' heads. This approach allows a **"brain transplant"** — switching from one AI model to another, or from one AI Studio to another — simply by transferring the current plan and step history. Development becomes resilient to tool changes.

---

## 4. Consequences

### Positive

- AI-assisted deployment becomes reliable across long projects because context is explicitly preserved
- the repository gets an explicit rule for why implementation plans and step documents help AI-assisted delivery
- documentation is treated as a quality and portability tool rather than as ceremony
- teams can switch between AI tools more safely because intent is preserved in repository artifacts
- AI Model switches, AI Studio switches, AI Engineer switches are possible without losing project state
- the repository serves as its own training material for any AI Agent or AI Engineer that joins later
- the human AI Engineer maintains real-time oversight through structured verification at every step
- the repository now has an explicit proportionality rule for when to stay lightweight and when to escalate
- the approach remains proportional because AI generates documentation at the same speed it generates code
- release planning, auditing, and onboarding become straightforward because the documentation is already there
- the process remains compatible with Agile because documentation is justified by delivery value, not by formality alone

### Negative

- contributors must understand that documentation is part of the delivery workflow, not a separate administrative task
- contributors must exercise judgment instead of blindly following either a minimal-doc or maximal-doc instinct
- teams accustomed to minimal-documentation Agile may initially perceive this as overhead until they experience the context benefits
- documentation quality still depends on human review — poorly verified step records can propagate incorrect context
- the approach requires discipline: skipping documentation for "small" steps creates context gaps that compound over time
- the workflow still carries overhead for substantial work, especially when plans, step records, and indexes all need maintenance
- poor proportionality decisions can still create either documentation debt or unnecessary process weight

### Neutral but important

- this ADR does **not** require the full design-document stack for every change
- this ADR does **not** mandate a specific documentation volume or template for every project
- this ADR clarifies how to apply AI-assisted delivery discipline in an AI-assisted repository
- this ADR establishes the principle that in AI-assisted delivery, documentation serves as operational context, and therefore its value should be evaluated differently than in purely human-written development
- the existing ADRs like ADR-003 (implementation plan governance), ADR-004 (step documentation governance), ADR-005 (software design document types) — already define the specific documentation structures, but this ADR provides the philosophical and methodological foundation that explains **why** those structures exist
- the role and performance of AI Models and AI Agents is growing significantly, but the responsibility for any operational and financial consequences lies with the AI Engineer and the company.

---

## 5. Rejected Alternative

### Alternative: treat documentation as a passive byproduct and rely mainly on transient chat context

This alternative was rejected because it is too fragile for sustained AI-assisted delivery.

If most intent remains only in chat context or in one model's short-term memory, several risks increase:

- later steps become harder to resume correctly
- switching AI tools becomes less reliable
- architectural constraints are easier to lose
- verification and downstream implications are more likely to drift away from the recorded implementation history

The repository should also reject the opposite extreme of mandatory heavyweight documentation for every task.

The right option is not "more documents at any cost", but a proportionate operational context with the possibility of its verification.

### Alternative: minimize documentation to honor the Agile Manifesto literally

This alternative applies the 2001 Agile principle without adaptation: keep documentation minimal and rely on working software as the primary measure of progress.

This was rejected because it does not account for the AI-assisted development context:

- AI models cannot maintain project context across conversations without explicit documentation
- without structured boundaries, AI agents drift into inconsistent architecture as the project grows
- context degradation becomes the primary failure mode in long-running AI-assisted projects
- switching AI models or AI Studios becomes effectively impossible without documented state
- the human AI Engineer loses the ability to verify and steer at each step, regressing to "hope for a miracle at the end of a big run"

The literal reading of "working software over comprehensive documentation" was designed for a world where humans wrote both the documentation and the code. In a world where AI writes code in seconds, human time is spent designing meaning — and documentation is that materialized meaning.

---

## 6. Review Trigger

Revisit this ADR if one or more of these conditions become true:

1. the repository's AI-assisted workflow no longer depends materially on maintained repository context
2. the documentation overhead repeatedly exceeds the delivery value for the kinds of work this repository performs
3. contributors and AI Agents cannot apply the proportionality rule consistently and keep oscillating between under-documentation and over-documentation
4. AI Models gain reliable long-term project memory that eliminates the need for explicit context documents
5. future tooling provides a more durable, auditable, and portable execution context than the current repository-document model
6. the repository adopts a fundamentally different AI-assisted workflow that replaces step-based context accumulation
7. documentation maintenance begins to measurably slow delivery rather than accelerating it
8. the ratio of documentation effort to development effort becomes disproportionate even at AI speed
9. contributors consistently disagree about whether the documentation burden is justified by the context benefits
10. ADR-003, ADR-004, and ADR101 evolve in a way that changes how implementation plans and step documents support AI-assisted work

If those conditions appear, refine the repository's AI-Agile rule. Do not quietly collapse back to undocumented chaotic chat-only execution for work.

---

## 7. Git Commit

```bash
# AI Engineer, Gemini Apps / Gemini 3 Fast, VS Code / GPT-5.4 Medium
git add -f docs/adr/README.md
git add -f docs/adr/adr-005-ai-agile-and-context-driven-development.md
git commit -m "docs(architecture: ADR): define Context-Driven Development (CDD) and AI-Augmented Agile (A3) via AI Engineer, Gemini 3 Pro, and VSC PT-5.4 Medium

- add ADR-005 for treating documentation as operational context in AI-assisted delivery
- define proportional documentation rules for small, multi-step, and architecture-heavy work
- connect the new governance rule to the existing implementation-plan and step-document ADRs
- update ./README.md
"

# Antigravity / Claude Opus 4.6 Thinking
git add -f docs/adr/adr-005-ai-agile-and-context-driven-development.md
git commit -m "(architecture: ADR): add ADR-005 for AI-Agile and Context-Driven Development

- document the principle that structured documentation serves as operational context in AI-assisted delivery
- frame the approach as an evolution of the Agile Manifesto's second principle
- capture the rationale for treating documentation as co-product rather than overhead
- reference ADR-003 and ADR-004 as the specific governance structures this ADR motivates
"

# AI Engineer
git add -f docs/adr/adr-005-ai-agile-and-context-driven-development.md
git commit -m "docs(architecture: ADR): add ADR-005 for AI-Agile (A2) and Context-Driven Development (CDD)

- clarify the roles and responsibilities of an AI engineer
"
```
