---
name: spec-builder
description: >
  Builds structured Technical Specifications (Specs) from approved PRDs for AI-assisted development.
  Translates business requirements into precise technical blueprints — sprints, features, acceptance
  criteria, API specs, data models, stack definitions, file structures, and agent assignments.
  Supports multiple project profiles (web app, API/backend, mobile, automation/script, design system,
  landing/marketing, plugin/extension). Use when the user says "create a spec", "build a spec",
  "technical specification", "generate spec from PRD", "translate PRD to spec", "spec builder",
  or needs to convert product requirements into implementation-ready technical documents.
---

# Spec Builder

Transforms approved PRDs into complete, implementation-ready Technical Specifications. The Spec defines the **"how"** — translating business needs into precise technical requirements that AI coding agents can execute with high accuracy and zero guesswork.

## When to Use This Skill

- User has an approved PRD and wants to generate a Technical Specification
- User says "create a spec", "build a spec", "generate spec", "technical specification"
- User mentions "translate PRD to spec", "turn this PRD into a spec"
- User wants to define sprints, acceptance criteria, API contracts, or data models
- User needs a structured technical plan before handing off to coding agents

## When NOT to Use

- User needs to **define** what to build (product/business) — use `prd-builder` instead
- User wants to write code directly (no spec needed for single-bug fixes or trivial changes)
- User is building a disposable prototype or fixing a single isolated bug
- User already has a complete Spec and wants to start coding

---

## Core Principles

1. **Spec ≠ PRD.** The PRD defines *what* and *why*. The Spec defines *how*. Never duplicate business justification — reference the PRD.
2. **Clean context.** Always build the Spec in a **fresh conversation window**, never in the same chat that produced the PRD. Long contexts degrade LLM precision below 50%.
3. **No happy-path-only planning.** LLMs default to the "happy path". Proactively validate edge cases, error scenarios, and failure modes before finalizing.
4. **Atomic sprints.** Break work into small, independently executable sprints. AI agents cannot reliably execute an entire spec in one pass.
5. **Acceptance criteria are the test suite.** Every feature must have criteria covering success AND failure scenarios. Without this, validation is impossible.
6. **The Spec is a contract.** Once validated, it is the authoritative document fed to coding agents — one sprint at a time.

---

## Workflow

### Phase 1: Input & Context

#### Step 1.1 — Receive the PRD

Request the approved PRD from the user. If the user provides it:

1. Read the entire PRD carefully
2. Extract: problem statement, goals, user stories, scope, business rules, technical context, NFRs
3. Identify the **project profile** (same profiles as the PRD: Web App, API/Backend, Mobile, Automation/Script, Design System, Landing/Marketing, Plugin/Extension)

If no PRD exists, advise the user to create one first using the `prd-builder` skill.

#### Step 1.2 — Explore Existing Codebase (if applicable)

If the project has an existing codebase:

1. Explore the file structure, key configs, and architecture
2. Identify existing patterns: naming conventions, framework usage, test setup
3. Document constraints imposed by the current architecture
4. Note integration points where new code must interface with existing code
5. Read project-level instructions and detect the actual runtime, framework, package manager, test setup, deployment target, and dependency versions from tracked configuration before proposing changes
6. When the Spec depends on a library, SDK, CLI, API, or cloud service, consult its current official documentation instead of assuming its API

#### Step 1.3 — Clarification Round

Before generating the Spec, ask targeted questions to fill gaps the PRD may not cover:

**For all profiles:**
- Are there naming conventions or code standards to follow?
- What is the testing strategy? (unit, integration, e2e, manual)
- Is there a CI/CD pipeline this must integrate with?
- Are there performance/latency SLAs?

**Profile-specific probes:**

<details>
<summary><strong>Web App</strong></summary>

- SSR, SSG, or SPA? Which framework? (Next.js, Nuxt, Astro, Vite+React, etc.)
- State management approach? (Zustand, Redux, Context, Pinia)
- CSS strategy? (CSS Modules, Tailwind, styled-components, vanilla CSS)
- Auth provider? (Supabase Auth, NextAuth, Clerk, Firebase Auth)
- Database? (PostgreSQL, MySQL, SQLite, MongoDB)
- Hosting target? (Vercel, Netlify, AWS, self-hosted)
</details>

<details>
<summary><strong>API / Backend</strong></summary>

- REST or GraphQL? OpenAPI/Swagger?
- Runtime and framework? (Node/Express, Node/Fastify, Python/FastAPI, Go/Chi)
- Database and ORM? (Prisma, Drizzle, SQLAlchemy, TypeORM)
- Auth mechanism? (JWT, API keys, OAuth2, session)
- Rate limiting and throttling requirements?
- Background jobs/queues? (BullMQ, Celery, SQS)
</details>

<details>
<summary><strong>Mobile</strong></summary>

- React Native, Flutter, Swift, or Kotlin?
- Navigation library? (React Navigation, Go Router)
- Local storage strategy? (AsyncStorage, SQLite, Realm)
- API communication layer? (Axios, Dio, URLSession)
- Push notification service? (FCM, APNs, OneSignal)
- Build and distribution? (Expo, Fastlane, manual)
</details>

<details>
<summary><strong>Automation / Script</strong></summary>

- Language/runtime? (Python, Node, Bash, Go)
- Scheduling mechanism? (cron, GitHub Actions, Cloud Functions)
- Input format and source?
- Output format and destination?
- Retry and error handling strategy?
- Logging framework?
</details>

<details>
<summary><strong>Design System</strong></summary>

- Framework targets? (React, Vue, Web Components, Figma tokens)
- Token structure? (design tokens JSON, CSS custom properties)
- Documentation tool? (Storybook, Docusaurus, custom)
- Package distribution? (npm, monorepo, private registry)
- Versioning strategy? (semver, independent per component)
</details>

<details>
<summary><strong>Landing / Marketing</strong></summary>

- Static or SSG framework? (Astro, Next.js static export, Hugo, 11ty)
- CMS integration? (headless CMS, markdown files, Contentful)
- Forms and lead capture? (native, Formspree, HubSpot)
- Analytics stack? (GA4, Plausible, Mixpanel)
- CDN and hosting? (Vercel, Cloudflare Pages, Netlify)
</details>

<details>
<summary><strong>Plugin / Extension</strong></summary>

- Host platform API version?
- Build toolchain? (webpack, esbuild, Vite, UXP)
- Communication model? (message passing, shared state, events)
- Persistent storage within host?
- Sandboxing restrictions?
- Marketplace packaging requirements?
</details>

---

### Phase 2: Spec Construction

Build the Spec following the **8 Structural Topics** — each topic is a required section of the final document.

#### Topic 1: Sprints — Divisão do Trabalho em Ciclos

Decompose the project into sequential sprints. Each sprint should be:

- **Small enough** for a coding agent to execute in a single session
- **Self-contained** — produces a testable, runnable increment
- **Ordered by dependency** — infrastructure → data → logic → UI → polish

```
Sprint naming: S01, S02, S03...
Target: 3-8 features per sprint (max)
```

**Sprint structure:**
```markdown
### Sprint S01: [Sprint Name]
**Goal:** [What this sprint achieves]
**Dependencies:** [None | S0X]
**Agent:** [optional — which agent executes this]
```

#### Topic 2: Features — O que cada Sprint Entrega

For each sprint, list the features with precise descriptions. Each feature should map back to one or more user stories from the PRD.

```markdown
#### Feature F01: [Feature Name]
**Sprint:** S01
**PRD Reference:** US-001, US-002
**Description:** [Exactly what this feature does — not why, that's in the PRD]
**Dependencies:** [None | F0X]
```

#### Topic 3: Acceptance Criteria — Como Validar

> ⚠️ **This is the most critical section.** Without proper acceptance criteria, coding agents cannot validate their own output and testing becomes impossible.

For each feature, define criteria using the Given/When/Then format. **Always include both success AND failure scenarios:**

```markdown
##### Acceptance Criteria for F01

**Success scenarios:**
- [ ] Given [precondition], when [action], then [expected result]
- [ ] Given [precondition], when [action], then [expected result]

**Failure / Edge-case scenarios:**
- [ ] Given [invalid input], when [action], then [error handling behavior]
- [ ] Given [missing data], when [action], then [fallback behavior]
- [ ] Given [concurrent access], when [action], then [conflict resolution]
```

**Checklist for edge cases to consider:**
- Empty/null inputs
- Invalid data formats
- Unauthorized access attempts
- Network failures / timeouts
- Concurrent modifications
- Rate limit exceeded
- Large data volumes / pagination boundaries
- Special characters / encoding issues

#### Topic 4: API Spec — Endpoints, Métodos, Payloads

Define every API endpoint that will exist. For REST APIs, use this format:

```markdown
#### `POST /api/v1/auth/login`
**Feature:** F01
**Auth:** None (public)
**Rate Limit:** 5/min per IP

**Request Body:**
```json
{
  "email": "string (required, valid email)",
  "password": "string (required, min 8 chars)"
}
```

**Responses:**

| Status | Description | Body |
|--------|-------------|------|
| 200 | Success | `{ "token": "string", "user": { ... } }` |
| 400 | Validation error | `{ "error": "VALIDATION_ERROR", "details": [...] }` |
| 401 | Invalid credentials | `{ "error": "INVALID_CREDENTIALS" }` |
| 429 | Rate limited | `{ "error": "RATE_LIMITED", "retryAfter": number }` |
```

For GraphQL, document queries, mutations, and subscriptions with their type signatures.

For projects without APIs (e.g., scripts, design systems), replace this section with **Interface Spec** documenting CLI flags, function signatures, component props, or event contracts.

#### Topic 5: Data Models — Schemas e Relações

Define all data entities, their fields, types, constraints, and relationships:

```markdown
#### Entity: User
**Table:** `users`

| Field | Type | Constraints | Description |
|-------|------|-------------|-------------|
| id | UUID | PK, auto-generated | Unique identifier |
| email | VARCHAR(255) | UNIQUE, NOT NULL | User email |
| password_hash | VARCHAR(255) | NOT NULL | Bcrypt hash |
| created_at | TIMESTAMP | DEFAULT NOW() | Creation timestamp |
| updated_at | TIMESTAMP | ON UPDATE NOW() | Last update |

**Relations:**
- `User` 1:N `Post` (user_id FK)
- `User` N:N `Role` (via `user_roles` join table)

**Indexes:**
- `idx_users_email` on `email` (unique)
```

For NoSQL databases, document collection structures and embedding strategies.
For projects without databases, document data structures, state shapes, or configuration schemas.

**Include migrations** — list the SQL/migration commands or ORM migration steps needed.

#### Topic 6: Stack — Tecnologias e Dependências

Explicitly declare every technology, library, and tool. AI agents must never guess or choose their own dependencies.

```markdown
#### Runtime & Framework
- Node.js 20 LTS
- Next.js 14 (App Router)
- TypeScript 5.x (strict mode)

#### Database
- PostgreSQL 16 (via Supabase)
- Prisma ORM 5.x

#### Authentication
- Supabase Auth (email/password + OAuth)

#### Styling
- Tailwind CSS 3.4
- shadcn/ui components

#### Testing
- Vitest (unit)
- Playwright (e2e)

#### DevOps
- Vercel (hosting)
- GitHub Actions (CI)

#### Key Dependencies
| Package | Version | Purpose |
|---------|---------|---------|
| zod | ^3.22 | Schema validation |
| react-hook-form | ^7.49 | Form handling |
| @tanstack/react-query | ^5.0 | Server state |
```

#### Topic 7: Coder Agent ID — Quem Executa (Opcional)

For advanced pipelines with multiple specialized agents, assign execution responsibility:

```markdown
| Sprint | Agent | Responsibility |
|--------|-------|---------------|
| S01 | Backend Agent | Database setup, API scaffold |
| S02 | Backend Agent | Auth system, middleware |
| S03 | Frontend Agent | UI components, pages |
| S04 | Frontend Agent | Forms, client validation |
| S05 | Full-Stack Agent | Integration, e2e tests |
```

If a single agent handles everything, this section can be omitted or replaced with a note: `Single agent execution — no assignment needed.`

#### Topic 8: File Structure — Árvore de Arquivos

Define the exact file tree that will be created or modified. This prevents AI agents from inventing their own directory conventions:

```markdown
#### Project Structure
```
project-root/
├── src/
│   ├── app/
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   ├── (auth)/
│   │   │   ├── login/page.tsx
│   │   │   └── register/page.tsx
│   │   └── api/
│   │       └── v1/
│   │           ├── auth/
│   │           │   └── route.ts
│   │           └── users/
│   │               └── route.ts
│   ├── components/
│   │   ├── ui/
│   │   └── forms/
│   ├── lib/
│   │   ├── db.ts
│   │   ├── auth.ts
│   │   └── validations.ts
│   └── types/
│       └── index.ts
├── prisma/
│   └── schema.prisma
├── tests/
│   ├── unit/
│   └── e2e/
├── .env.example
├── package.json
└── tsconfig.json
```

**Per-sprint file mapping:**

| Sprint | Files Created/Modified |
|--------|----------------------|
| S01 | `prisma/schema.prisma`, `src/lib/db.ts`, `.env.example` |
| S02 | `src/lib/auth.ts`, `src/app/api/v1/auth/route.ts` |
| S03 | `src/components/ui/*`, `src/app/(auth)/*` |
```

---

### Phase 3: Validation & Edge-Case Audit

> ⚠️ **Never skip this phase.** LLMs naturally plan for the happy path. This phase forces adversarial review.

#### Step 3.1 — Self-Review Checklist

Before presenting the Spec, verify:

- [ ] Every user story from the PRD has at least one feature mapped to it
- [ ] Every feature has acceptance criteria covering **both** success and failure
- [ ] Every API endpoint has error responses defined (not just 200)
- [ ] Data models have constraints, not just field names
- [ ] The file structure matches the stack (no Next.js structure for a Python project)
- [ ] Sprint dependencies form a valid DAG (no circular dependencies)
- [ ] Stack versions are pinned (no "latest")
- [ ] Environment variables are listed in `.env.example` or equivalent

#### Step 3.2 — Edge-Case Stress Test

Run through these scenarios mentally for each feature:

1. **What happens when the input is empty?**
2. **What happens when the user is not authenticated?**
3. **What happens when the external API/DB is down?**
4. **What happens with concurrent requests to the same resource?**
5. **What happens when the data exceeds expected size?**
6. **What happens on the first run (empty state)?**
7. **What happens if the operation is executed twice?**

Add any missing edge cases to the Acceptance Criteria.

#### Step 3.3 — Present to User

1. Present the complete Spec to the user
2. Highlight any assumptions made
3. Flag areas where the PRD was ambiguous
4. Ask: *"Are there scenarios, constraints, or edge cases missing?"*
5. Iterate until approved

---

### Phase 4: Handoff

Once the Spec is approved:

1. **Save the final document** at the agreed location
2. **Advise the user on execution:**

> **How to use this Spec with a coding agent:**
> 1. Open a **new, clean context** (chat window)
> 2. Feed the Spec to the agent
> 3. Execute **one sprint at a time** — do NOT send the entire Spec for execution at once
> 4. After each sprint, validate against the acceptance criteria before proceeding
> 5. If a sprint fails validation, fix it before moving to the next one

---

## Spec Template

```markdown
# Spec: [Project/Feature Name]

> **Version:** 1.0
> **Date:** YYYY-MM-DD
> **Author:** [Name / AI-assisted]
> **Status:** Draft | In Review | Approved
> **Profile:** [Web App | API | Mobile | Automation | Design System | Landing | Plugin]
> **PRD Reference:** [link or filename of the source PRD]

---

## 1. Sprints

### S01: [Sprint Name]
**Goal:** [objective]
**Dependencies:** None
**Estimated Effort:** [S/M/L]

### S02: [Sprint Name]
**Goal:** [objective]
**Dependencies:** S01
**Estimated Effort:** [S/M/L]

(repeat as needed)

---

## 2. Features

### S01 Features

#### F01: [Feature Name]
**PRD Ref:** US-001
**Description:** [precise description]

#### F02: [Feature Name]
**PRD Ref:** US-002
**Description:** [precise description]

### S02 Features
(repeat pattern)

---

## 3. Acceptance Criteria

### F01: [Feature Name]

**✅ Success:**
- [ ] Given [context], when [action], then [result]
- [ ] Given [context], when [action], then [result]

**❌ Failure / Edge Cases:**
- [ ] Given [invalid state], when [action], then [error handling]
- [ ] Given [missing data], when [action], then [fallback]

### F02: [Feature Name]
(repeat pattern)

---

## 4. API Spec

### `METHOD /path/to/endpoint`
**Feature:** F0X
**Auth:** [required/public]

**Request:**
(document body, params, headers)

**Responses:**
| Status | Description | Body |
|--------|-------------|------|
| 2XX | Success | `{...}` |
| 4XX | Client error | `{...}` |
| 5XX | Server error | `{...}` |

(repeat for all endpoints)

---

## 5. Data Models

### Entity: [Name]
**Table/Collection:** `name`

| Field | Type | Constraints | Description |
|-------|------|-------------|-------------|
| ... | ... | ... | ... |

**Relations:** ...
**Indexes:** ...
**Migrations:** ...

(repeat for all entities)

---

## 6. Stack

### Runtime & Framework
- ...

### Database
- ...

### Key Dependencies
| Package | Version | Purpose |
|---------|---------|---------|
| ... | ... | ... |

---

## 7. Agent Assignment (Optional)

| Sprint | Agent | Responsibility |
|--------|-------|---------------|
| S0X | ... | ... |

---

## 8. File Structure

```
project-root/
├── ...
```

**Sprint → File Mapping:**

| Sprint | Files |
|--------|-------|
| S01 | ... |
| S02 | ... |

---

## Validation Checklist

- [ ] All PRD user stories mapped to features
- [ ] Acceptance criteria cover success + failure for every feature
- [ ] API error responses defined
- [ ] Data constraints specified
- [ ] Stack versions pinned
- [ ] File structure matches stack conventions
- [ ] Environment variables documented
- [ ] Sprint dependencies are acyclic

---

## Decision Log

| Date | Decision | Rationale |
|------|----------|-----------|
| YYYY-MM-DD | [Decision] | [Why] |
```

---

## Best Practices

### For the Agent

1. **Always start from a PRD.** If the user doesn't have one, redirect to `prd-builder` first.
2. **Never work in a polluted context.** If the conversation already has thousands of tokens from PRD creation, insist on a clean chat.
3. **Force edge-case thinking.** After writing each feature's acceptance criteria, ask yourself: "What happens when this goes wrong?" Add those scenarios.
4. **Pin versions.** Never write `"latest"` or `"^X"` without specifying the major version. AI agents will pick random versions otherwise.
5. **Map PRD → Spec traceability.** Every feature should reference its source user story. Every sprint should reference its features. The chain is: PRD (US) → Spec (Feature) → Sprint → Code.
6. **Adapt depth to profile.** A CLI script spec doesn't need 15 API endpoints. A SaaS web app doesn't need idempotency rules for every endpoint. Scale appropriately.
7. **Include error contracts.** For every API endpoint, define error response shapes — not just success responses.
8. **File structure must match the stack.** Don't propose a `src/app/` structure for a Python Flask project.

### For the User

1. **Use the PRD as the single source of truth.** Don't verbally add requirements during Spec generation — update the PRD first.
2. **Review acceptance criteria carefully.** They become your test suite. Missing criteria = untested behavior.
3. **Execute one sprint at a time.** Feed the coding agent a single sprint, validate it, then proceed.
4. **Version your Specs.** As the project evolves, the Spec should evolve too — with tracked changes.
5. **After Spec approval, open yet another clean context for coding.** The chain is always: PRD (context 1) → Spec (context 2) → Code (context 3).

---

## Decision Tree

```
1. Does the user have an approved PRD?
   ├─ Yes → Proceed to Phase 1 (Input & Context)
   └─ No  → Redirect to prd-builder skill

2. Is this a new conversation (clean context)?
   ├─ Yes → Continue
   └─ No  → Recommend opening a new context window

3. Is there an existing codebase?
   ├─ Yes → Explore it first (Step 1.2), then proceed
   └─ No  → Skip Step 1.2, proceed to clarification

4. Is the project multi-agent?
   ├─ Yes → Include Topic 7 (Agent Assignment)
   └─ No  → Omit or note "single agent"

5. Has the Spec passed the edge-case audit?
   ├─ Yes → Present to user for review
   └─ No  → Add missing scenarios, re-validate

6. Is the Spec approved?
   ├─ Yes → Save and guide handoff (Phase 4)
   └─ No  → Iterate on user feedback
```

---

## Output Conventions

- **File name:** `SPEC-[project-name].md` (kebab-case)
- **Location:** Project root `docs/` folder, or as specified by the user
- **Format:** Markdown (`.md`)
- **Language:** Match the user's language (Portuguese if user writes in PT, English if EN, etc.)
- **Encoding:** UTF-8
