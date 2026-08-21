---
name: prd-builder
description: >
  Builds structured Product Requirements Documents (PRDs) for AI-assisted development.
  Guides the user through ideation, scoping, and documentation to produce a complete PRD
  ready to feed into a Spec generator or coding agent. Supports multiple project profiles
  (web app, API/backend, mobile, automation/script, design system). Use when the user says
  "create a PRD", "build a PRD", "product requirements", "define requirements", "plan a product",
  "scope a project", "write a PRD", or needs to formalize what will be built before coding.
---

# PRD Builder

Constructs complete, AI-optimized Product Requirements Documents (PRDs) through a guided, interactive workflow. The PRD focuses on **product and business** — the "what" and "why" — not on technical implementation details. It is the critical input that prevents AI coding agents from building misaligned solutions.

## When to Use This Skill

- User wants to create, write, or build a PRD
- User needs to formalize requirements before development
- User says "plan a product", "define requirements", "scope a project"
- User mentions "PRD", "product requirements", "project spec" (in a product context)
- A new feature or product needs structured definition before any code is written

## When NOT to Use

- User already has a PRD and wants a **Technical Specification (Spec)** — use a spec-builder skill instead
- User wants to fix a single bug or make a trivial change
- User wants architecture/infra planning without product context

---

## Core Principles

1. **PRD ≠ Spec.** The PRD defines *what* and *why*. The Spec defines *how*. Never mix implementation details (endpoints, database schemas, file structures) into the PRD.
2. **Ideation before documentation.** The PRD writing process starts with structured discussion, not writing. Spend time refining goals, user stories, and scope before generating any document.
3. **Explicit scope boundaries.** Always define what is IN scope and what is OUT of scope. This is the #1 guard against AI agent scope creep.
4. **The PRD is a contract.** Once validated, it is the single source of truth fed to the next phase (Spec generation → Sprint execution).

---

## Workflow

### Phase 1: Discovery & Profiling

Before anything else, determine the project profile and gather context.

#### Step 1.1 — Identify Project Profile

Ask the user (or infer from context) which profile best fits:

| Profile | Description | Key Focus Areas |
|---------|-------------|-----------------|
| **Web App** | SPA, SSR, full-stack web application | Pages/views, auth, data flows, responsive behavior |
| **API / Backend** | REST/GraphQL service, microservice | Consumers, contracts, data models, error handling |
| **Mobile** | Native or cross-platform mobile app | Platform constraints, offline, push notifications, gestures |
| **Automation / Script** | CLI tool, pipeline, bot, scheduled job | Triggers, inputs/outputs, error recovery, idempotency |
| **Design System** | Component library, UI kit | Tokens, variants, accessibility, documentation |
| **Landing / Marketing** | Institutional, campaign, or content site | SEO, conversion goals, CMS integration, analytics |
| **Plugin / Extension** | Extension for existing platform (VSCode, Figma, etc.) | Host API constraints, lifecycle hooks, sandboxing |

> If the project spans multiple profiles, pick the **primary** and note secondary concerns.

#### Step 1.2 — Context Intake

Gather from the user:

- **Problem statement** — What pain/need drives this project?
- **Target users** — Who will use this? (personas if available)
- **Existing assets** — Is there a codebase, design, prototype, or competitor reference?
- **Constraints** — Budget, timeline, platform, regulatory, team size
- **Success metrics** — How will success be measured? (KPIs, OKRs)

If the user provides a codebase, explore it to understand the current state before proceeding.

For an existing project, first read its local instructions and identify the current stack from configuration and lockfiles. Record only constraints that affect product scope; leave implementation choices for the Spec.

---

### Phase 2: Ideation & Refinement

This is the most critical phase. Invest time here to prevent rework later.

#### Step 2.1 — Structured Discussion

Guide the user through targeted questions based on the project profile:

**For all profiles:**
- What is the single most important outcome?
- Who are the primary vs. secondary users?
- What existing solutions (if any) does this replace or compete with?
- What are the non-negotiable requirements vs. nice-to-haves?

**Profile-specific probes:**

<details>
<summary><strong>Web App</strong></summary>

- What are the main user journeys? (signup → onboard → core action → retention)
- Authentication model? (email/password, OAuth, magic link, none)
- Will there be role-based access?
- What data does the user create, read, update, delete?
- Is real-time interaction needed? (websockets, SSE)
- SEO requirements?
- Internationalization (i18n)?
</details>

<details>
<summary><strong>API / Backend</strong></summary>

- Who/what consumes this API? (frontend, mobile, third-party, internal)
- Sync vs. async operations?
- Expected load / concurrency?
- Authentication/authorization model for consumers?
- Data sensitivity and compliance requirements?
- Versioning strategy?
</details>

<details>
<summary><strong>Mobile</strong></summary>

- iOS, Android, or both? Native or cross-platform?
- Minimum OS versions?
- Offline-first requirements?
- Push notification needs?
- Device hardware access? (camera, GPS, biometrics)
- App Store compliance considerations?
</details>

<details>
<summary><strong>Automation / Script</strong></summary>

- What triggers execution? (cron, event, manual)
- What are the inputs and expected outputs?
- Idempotency requirements?
- Error recovery and retry strategy?
- Logging and observability needs?
- Dependencies on external services?
</details>

<details>
<summary><strong>Design System</strong></summary>

- Which frameworks/platforms must it support?
- Token architecture? (colors, spacing, typography)
- Accessibility standards? (WCAG level)
- Theming requirements? (dark mode, white-label)
- Documentation and Storybook needs?
- Versioning and distribution?
</details>

<details>
<summary><strong>Landing / Marketing</strong></summary>

- Conversion goals? (signup, download, contact)
- SEO keyword targets?
- CMS needs? (static, headless CMS, blog)
- Analytics and tracking requirements?
- A/B testing needs?
- Performance budgets?
</details>

<details>
<summary><strong>Plugin / Extension</strong></summary>

- Target host platform and API version?
- Lifecycle hooks needed?
- Sandboxing/permission constraints?
- Distribution channel? (marketplace, sideload)
- Update/versioning mechanism?
- Data persistence model within the host?
</details>

#### Step 2.2 — Running Notes

As the discussion progresses, maintain **running notes** of every decision made. This prevents context window degradation in long conversations. Structure notes as:

```markdown
## Decision Log
- [DECIDED] <topic>: <decision> (reason: <why>)
- [OPEN] <topic>: <options being considered>
- [DEFERRED] <topic>: <will decide in Spec phase>
```

Update the log after each significant exchange.

---

### Phase 3: PRD Generation

Once ideation is complete, consolidate everything into the final PRD document.

#### Step 3.1 — Generate the PRD

Create the PRD as a Markdown file (`.md`) using the structure defined in the **PRD Template** section below. The output file should be saved at a location agreed with the user (default: project root or `docs/` folder).

#### Step 3.2 — User Validation

After generating:

1. Present the PRD to the user for review
2. Highlight any sections that feel under-specified
3. Ask explicitly: *"Is there anything missing, incorrect, or that needs more detail?"*
4. Iterate until the user approves

#### Step 3.3 — Next Steps Guidance

Once the PRD is approved, advise the user:

> **Do not send this PRD directly to a coding agent.** Open a new, clean context and use this PRD to generate a **Technical Specification (Spec)** first. The Spec translates business needs into technical requirements (endpoints, data models, sprints, acceptance criteria), ensuring the coding agent works with precision.

---

## PRD Template

Use this structure for all generated PRDs. Omit sections that are genuinely not applicable, but prefer including a section with "N/A" over silently dropping it.

```markdown
# PRD: [Product/Feature Name]

> **Version:** 1.0
> **Date:** YYYY-MM-DD
> **Author:** [Name / AI-assisted]
> **Status:** Draft | In Review | Approved
> **Profile:** [Web App | API | Mobile | Automation | Design System | Landing | Plugin]

---

## 1. Problem Description

Clear explanation of the problem this product/feature solves.
- What is the current pain?
- Who experiences it?
- What is the cost of inaction?

## 2. Goals & Objectives

| Goal | Measurable Outcome | Priority |
|------|-------------------|----------|
| [Goal 1] | [KPI / metric] | Must-have |
| [Goal 2] | [KPI / metric] | Should-have |
| [Goal 3] | [KPI / metric] | Nice-to-have |

## 3. Target Users & Personas

### Persona 1: [Name]
- **Role:** ...
- **Needs:** ...
- **Pain points:** ...
- **Tech proficiency:** ...

### Persona 2: [Name]
(repeat as needed)

## 4. Scope Definition

### 4.1 In Scope
- [ ] Feature/capability 1
- [ ] Feature/capability 2
- [ ] Feature/capability 3

### 4.2 Out of Scope
- Feature X (reason: deferred to v2)
- Feature Y (reason: not aligned with current goals)

> ⚠️ **Critical:** The "Out of Scope" section is a direct instruction to coding agents.
> Anything listed here must NOT be implemented in this cycle.

## 5. User Stories

### Epic: [Epic Name]

#### US-001: [Story Title]
**As a** [persona], **I want to** [action], **so that** [benefit].

**Acceptance Criteria:**
- [ ] Given [context], when [action], then [result]
- [ ] Given [context], when [action], then [result]

#### US-002: [Story Title]
(repeat as needed)

## 6. User Flows

Describe the primary user journeys step by step.

### Flow 1: [Flow Name]
1. User does X
2. System responds with Y
3. User sees Z
4. ...

(Include diagrams if helpful — Mermaid, ASCII, or link to external tool)

## 7. Business Rules

| Rule ID | Description | Applies To |
|---------|-------------|------------|
| BR-001 | [Rule description] | [Feature/Story] |
| BR-002 | [Rule description] | [Feature/Story] |

## 8. Technical Context

> **Note:** This section captures high-level technical decisions and constraints
> agreed during planning. Detailed technical design belongs in the Spec.

- **Platform/Runtime:** (e.g., Web, Node.js, React Native)
- **Key integrations:** (e.g., Stripe, Supabase, SendGrid)
- **Known constraints:** (e.g., must run on Node 18+, must support IE11)
- **Performance expectations:** (e.g., <2s page load, <200ms API response)
- **Security requirements:** (e.g., LGPD/GDPR compliance, encryption at rest)

## 9. Non-Functional Requirements

| Category | Requirement |
|----------|-------------|
| Performance | ... |
| Accessibility | ... |
| Security | ... |
| Scalability | ... |
| Reliability | ... |
| Observability | ... |

## 10. Success Metrics

| Metric | Current Baseline | Target | Measurement Method |
|--------|-----------------|--------|-------------------|
| [Metric 1] | [value] | [value] | [how measured] |
| [Metric 2] | [value] | [value] | [how measured] |

## 11. Risks & Mitigations

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | High/Med/Low | High/Med/Low | [Strategy] |
| [Risk 2] | High/Med/Low | High/Med/Low | [Strategy] |

## 12. Dependencies

- **External:** [third-party APIs, services, approvals]
- **Internal:** [other teams, other features, infrastructure]

## 13. Timeline & Milestones

| Milestone | Target Date | Description |
|-----------|-------------|-------------|
| PRD Approved | YYYY-MM-DD | Requirements locked |
| Spec Complete | YYYY-MM-DD | Technical design done |
| MVP Ready | YYYY-MM-DD | Core features functional |
| Launch | YYYY-MM-DD | Production release |

## 14. Open Questions

- [ ] [Question 1 — who owns the answer]
- [ ] [Question 2 — who owns the answer]

## 15. Appendices

- Links to mockups, prototypes, competitive analysis
- Reference documents
- Glossary of terms

---

## Decision Log

| Date | Decision | Rationale | Decided By |
|------|----------|-----------|------------|
| YYYY-MM-DD | [Decision] | [Why] | [Who] |
```

---

## Best Practices

### For the Agent

1. **Never skip ideation.** Even if the user says "just write the PRD", push back gently and ask at least the core discovery questions.
2. **Keep running notes.** In long conversations, summarize decisions periodically to combat context degradation.
3. **Be explicit about scope boundaries.** The Out of Scope section is the most valuable guardrail for downstream AI agents.
4. **Validate user stories.** Each story should have clear acceptance criteria. If the user provides vague stories, help refine them.
5. **Don't bleed into Spec territory.** If you catch yourself writing database schemas, API endpoints, or file structures, stop — that belongs in the Spec.
6. **Use the profile to guide depth.** A CLI automation PRD doesn't need 5 personas. A consumer web app doesn't need idempotency rules. Adapt.
7. **Flag risks proactively.** If you identify risks the user hasn't mentioned, add them.

### For the User

1. **Treat ideation seriously.** Hours of planning save days of rework.
2. **Read the generated PRD end to end.** Don't blindly approve — the AI may have missed nuance.
3. **After PRD approval, open a clean context for Spec generation.** Long conversations degrade AI precision.
4. **Version your PRDs.** Requirements evolve. Track changes with version numbers and dates.

---

## Decision Tree

```
1. Does the user have a clear idea of what to build?
   ├─ Yes → Go to Phase 1 (Discovery) to formalize it
   └─ No  → Start with open-ended ideation in Phase 2

2. Is there an existing codebase?
   ├─ Yes → Explore it first, then start Discovery with context
   └─ No  → Standard Discovery flow

3. Does the project fit a single profile?
   ├─ Yes → Use that profile's question set
   └─ No  → Pick primary profile, note secondary concerns

4. Is the user providing enough detail?
   ├─ Yes → Move to PRD generation
   └─ No  → Continue probing with profile-specific questions

5. Is the PRD approved?
   ├─ Yes → Guide user to Spec generation (clean context)
   └─ No  → Iterate on feedback
```

---

## Output Conventions

- **File name:** `PRD-[project-name].md` (kebab-case)
- **Location:** Project root `docs/` folder, or as specified by the user
- **Format:** Markdown (`.md`)
- **Language:** Match the user's language (Portuguese if user writes in PT, English if EN, etc.)
- **Encoding:** UTF-8
