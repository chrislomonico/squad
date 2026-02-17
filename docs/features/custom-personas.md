# Custom Personas — Deep Researcher, Design Thinker & Synthetic SMEs

Expand your Squad with non-coding specialists. These personas produce research, analysis, and design artifacts — not code — and integrate with your team through the standard routing and decisions systems.

The **synthetic SME** pattern takes this further: the Design Thinker generates interview questions, and Squad spawns domain experts on-the-fly to answer them — building deep contextual understanding before a single line of code is written.

---

## Automatic Inclusion — Ask Classification

Squad detects high-level asks during Init Mode and **automatically includes discovery personas** when appropriate. You don't need to ask for them — the coordinator classifies your initial description and adjusts team composition.

### How it works

When you describe what you're building, the coordinator classifies the ask:

| Ask Type | Example | What Happens |
|----------|---------|-------------|
| **Executive / Strategic** | "Leadership wants us to explore a customer self-service portal" | Researcher + Design Strategist auto-included. SME spawning enabled. |
| **Exploratory / Research** | "We need to figure out the best approach for real-time sync" | Researcher auto-included. Design Strategist suggested if user-facing. |
| **Technical / Implementation** | "Build a React dashboard with a Node.js API" | Standard dev team. Discovery personas available on request. |

### What triggers automatic inclusion

The coordinator looks for these signals in your initial description:

**Executive signals** — discovery personas auto-included:
- Vague scope with business outcomes ("improve customer retention")
- No specific tech stack mentioned
- Phrasing like "we need", "the business wants", "leadership asked for"
- "Explore whether", "evaluate if we should", "figure out if"
- "I don't know the stack yet"

**Exploratory signals** — researcher auto-included:
- "Investigate", "compare options", "spike on", "proof of concept"
- "What's the best way to", "help me figure out"
- Technology evaluation requests without a clear deliverable

**Technical signals** — standard team, no discovery personas:
- Specific stack named ("React + Node + Postgres")
- Clear deliverable ("build the login page", "add OAuth")
- PRD or spec provided

### The coordinator tells you

When discovery personas are auto-included, the coordinator explains why:

> *"That sounds like a high-level ask — I'll include a Deep Researcher and Design Strategist on the team to help explore the problem space before we start building. The Design Strategist can also spawn synthetic subject matter experts to interview for domain context."*

You can always decline: *"No, just give me a dev team"* — and the coordinator falls back to a standard Technical composition.

### Discovery-first workflow

When discovery personas are on the team, the coordinator guides a discovery-first sequence:

1. **Research** — Researcher investigates the problem space and prior art
2. **SME identification** — Design Strategist identifies domain experts to interview
3. **Interviews** — Design Strategist runs interviews with spawned SMEs
4. **Synthesis** — Findings consolidated into a requirements brief
5. **Transition** — Lead decomposes the brief into work items and the team shifts to building

You can skip any phase or jump straight to implementation — discovery is recommended, not enforced.

---

## Adding the Personas Manually

### Deep Researcher

```plaintext
Add a deep researcher to the team. They investigate prior art, review documentation,
explore open-source solutions, and produce research summaries before we build.
They should be thorough, methodical, and present findings with citations.
```

### Design Thinker

```plaintext
Add a design strategist to the team. They run ideation, empathy mapping,
user journey mapping, and prototype planning before technical work begins.
They should always ask "who is this for?" before "how do we build it?"
```

### Both at once

```plaintext
Add two new team members:
1. A deep researcher — investigates prior art, evaluates libraries, produces
   comparison reports before the team commits to a technology choice.
2. A design strategist — creates user personas, journey maps, and feature
   specs grounded in user needs before development starts.
```

### Synthetic Subject Matter Experts

Synthetic SMEs are **not permanent team members**. They are spawned on demand by the coordinator when the Design Thinker needs domain expertise to validate assumptions, stress-test ideas, or fill knowledge gaps. Each SME adopts a realistic professional persona relevant to the ask.

```plaintext
From now on, when {Designer} needs domain context for a new feature,
spawn synthetic subject matter experts relevant to the problem space.
{Designer} will generate interview questions, and each SME will answer
in-character based on their domain expertise. Write all interview
transcripts to .ai-team/decisions/inbox/ so the Scribe can merge them.
```

#### How to trigger SME generation

```plaintext
We're building a telemedicine appointment platform.
{Designer}, identify 3-4 subject matter experts we should interview
to understand the problem space, then generate interview questions for each.
```

```plaintext
We need to add multi-currency support to our e-commerce platform.
Spawn SMEs for this domain — {Designer} will interview them.
```

```plaintext
Before we design the accessibility features, {Designer} should
interview SMEs who represent users with different accessibility needs.
```

#### Example: What gets generated

For the telemedicine ask, the Design Thinker might identify:

| SME Persona | Domain | Why They Matter |
|---|---|---|
| Dr. Patel — Primary Care Physician | Clinical workflow | Understands appointment flow, patient intake, time constraints |
| Maria — Clinic Office Manager | Operations & scheduling | Knows booking friction, no-shows, insurance verification |
| James — Patient (chronic condition) | End-user experience | Frequent telehealth user, accessibility needs, medication management |
| Compliance Officer Chen | HIPAA & regulation | Data handling requirements, consent flows, audit trails |

Each SME is spawned as a background agent with a charter scoped to their expertise. They respond to interview questions in-character, drawing on domain knowledge to surface requirements, edge cases, and constraints the team wouldn't discover otherwise.

---

## Deep Researcher — Sample Prompts

### Technology evaluation

```plaintext
{Researcher}, compare React, Vue, and Svelte for our dashboard.
Consider bundle size, learning curve, ecosystem maturity, and hiring pool.
```

```plaintext
{Researcher}, evaluate authentication libraries for Node.js.
We need OAuth2, magic links, and MFA support. Show license and maintenance status.
```

```plaintext
{Researcher}, research state management options for our frontend.
We're using React — compare Redux Toolkit, Zustand, Jotai, and React Query.
```

### Prior art & competitive analysis

```plaintext
{Researcher}, investigate how similar products handle real-time collaboration.
Look at Figma, Notion, and Google Docs approaches. Summarize trade-offs.
```

```plaintext
{Researcher}, research open-source alternatives to the Stripe billing API.
We need subscription management, usage-based billing, and invoice generation.
```

### Architecture research

```plaintext
{Researcher}, research microservices vs. modular monolith for our scale.
We expect 10K daily active users in year one. Summarize operational complexity trade-offs.
```

```plaintext
{Researcher}, investigate database options for our time-series data.
Compare TimescaleDB, InfluxDB, and ClickHouse. We need sub-second query times
on 30-day windows with 100M+ rows.
```

### Documentation & standards review

```plaintext
{Researcher}, review the OpenAPI 3.1 spec and summarize what changed from 3.0.
Flag anything that affects our current API documentation tooling.
```

```plaintext
{Researcher}, research WCAG 2.2 AA requirements relevant to our dashboard.
Produce a checklist the frontend team can work from.
```

### Research spikes

```plaintext
{Researcher}, run a spike on WebSocket vs. Server-Sent Events for our
notification system. We need to push updates to ~500 concurrent users.
Write your findings to a research doc.
```

```plaintext
{Researcher}, investigate whether we can use WebAssembly for our image
processing pipeline. Current JS implementation takes 3-4 seconds per image.
```

### Pre-build investigation

```plaintext
{Researcher}, before we build the search feature, research full-text search
options. Compare Elasticsearch, Meilisearch, and Typesense for our use case:
50K documents, faceted filtering, typo tolerance.
```

```plaintext
{Researcher}, we're about to add PDF export. Research libraries that support
styled HTML-to-PDF conversion in Node.js. Must handle tables, charts, and
custom fonts.
```

---

## Design Thinker — Sample Prompts

### User personas & empathy mapping

```plaintext
{Designer}, create user personas for our recipe sharing app.
Consider home cooks, professional chefs, and dietary-restricted users.
```

```plaintext
{Designer}, build an empathy map for first-time users of our CLI tool.
What are they thinking, feeling, and doing when they first run the command?
```

### User journey mapping

```plaintext
{Designer}, map the user journey for signing up and creating a first project.
Identify pain points, moments of delight, and drop-off risks.
```

```plaintext
{Designer}, map the journey for a user migrating from a competitor product.
What do they need to bring over? Where will they get stuck?
```

### Feature scoping & prioritization

```plaintext
{Designer}, review this feature list and prioritize from the user's perspective.
Which features solve the most painful problems? Which are nice-to-haves?
```

```plaintext
{Designer}, we have three approaches for the onboarding flow. Evaluate each
from a UX perspective and recommend which to build first.
```

### Design critique

```plaintext
{Designer}, review the proposed dashboard layout. Does it surface the right
information for a user checking in for 30 seconds vs. doing a deep dive?
```

```plaintext
{Designer}, critique our current error messages. Are they helpful?
Do they tell the user what went wrong AND what to do next?
```

### Jobs-to-be-done analysis

```plaintext
{Designer}, reframe our backlog using jobs-to-be-done.
What jobs are users hiring our product to do? Which tickets don't map to a real job?
```

```plaintext
{Designer}, what job is the user trying to do when they hit the settings page?
Redesign the information architecture around those jobs.
```

### Wireframe & prototype specs

```plaintext
{Designer}, write a text-based wireframe spec for the notification center.
Include layout, content hierarchy, interaction states, and empty states.
```

```plaintext
{Designer}, spec out the mobile-responsive behavior for our data table.
What changes at each breakpoint? What gets hidden, collapsed, or rearranged?
```

### Pre-development review

```plaintext
{Designer}, review this PRD before we start building. Does every feature
map to a user need? Flag anything that's engineering-driven rather than user-driven.
```

```plaintext
{Designer}, before the team starts on the checkout flow, define the user
stories and acceptance criteria from the buyer's perspective.
```

### SME interview question generation

The Design Thinker's core role in the SME workflow is crafting targeted interview questions that extract actionable context.

```plaintext
{Designer}, we're building a recipe sharing app. Identify the subject matter
experts we need to interview and generate 5-7 questions for each that will
uncover requirements, pain points, and edge cases.
```

```plaintext
{Designer}, generate interview questions for a compliance officer about
our payment processing feature. Focus on PCI-DSS requirements, data
retention policies, and audit trail needs.
```

```plaintext
{Designer}, we have SMEs for our fitness tracking app: a personal trainer,
a nutritionist, and a casual gym-goer. Write differentiated interview
scripts for each — the trainer cares about programming periodization,
the nutritionist about meal logging, and the casual user about motivation.
```

```plaintext
{Designer}, our first round of SME interviews surfaced questions about
insurance verification workflows. Generate follow-up questions for the
clinic office manager SME to dig deeper into that area.
```

```plaintext
{Designer}, synthesize all SME interview responses into a requirements
brief. Group findings by theme, flag conflicting perspectives, and
highlight the top 5 insights that should shape our architecture.
```

---

## Synthetic SME — Sample Prompts

Once SMEs are spawned, you interact with them directly or let the Design Thinker run the interview.

### Direct SME interaction

```plaintext
Dr. Patel, walk me through a typical telehealth appointment from your
perspective. Where do you lose time? What information do you wish you
had before the patient connects?
```

```plaintext
Maria, what's the most common reason appointments get rescheduled?
How do you handle insurance verification before a telehealth visit?
```

```plaintext
James, describe your last three telehealth experiences. What worked?
What made you want to switch providers?
```

```plaintext
Compliance Officer Chen, what are the minimum HIPAA requirements for
storing telehealth session recordings? What audit trail do regulators
expect?
```

### Design Thinker–led interviews

```plaintext
{Designer}, run the full interview sequence with all four SMEs.
Ask your prepared questions, then follow up on anything surprising.
Write a consolidated findings document when done.
```

```plaintext
{Designer}, interview the patient SME first. Use their responses to
refine the questions for the physician SME — what the patient struggles
with should inform what we ask the doctor.
```

```plaintext
{Designer}, run a panel discussion with all SMEs. Present the proposed
appointment booking flow and have each SME critique it from their
perspective. Capture points of agreement and conflict.
```

### Spawning additional SMEs mid-session

```plaintext
The interviews revealed we need insurance billing expertise.
Spawn a medical billing specialist SME and have {Designer} interview
them about claim submission workflows and denial handling.
```

```plaintext
We're getting conflicting feedback on the scheduling UX.
Spawn an SME representing a non-technical elderly patient and
have {Designer} test our proposed flow with them.
```

### SME output synthesis

```plaintext
{Designer}, synthesize the SME interviews into:
1. A stakeholder needs matrix (who needs what)
2. Conflicting requirements with your recommended resolution
3. Non-obvious constraints we wouldn't have found without interviews
4. Prioritized user stories derived from interview insights
```

```plaintext
{Researcher}, take the SME interview findings and cross-reference with
your prior art research. Where do our SMEs' needs align with existing
solutions? Where are we solving a novel problem?
```

---

## Combining All Personas

### Research → Design → SME Interview → Build pipeline

The full pipeline uses all three persona types in sequence:

```plaintext
We're building a telemedicine platform. Here's the sequence:
1. {Researcher} — investigate existing telehealth platforms, regulations,
   and technical requirements.
2. {Designer} — identify the SMEs we need and generate interview questions
   based on the research findings.
3. Spawn SMEs and run interviews.
4. {Designer} — synthesize research + interviews into a requirements brief.
5. Lead — decompose the brief into work items.
```

### Research → Design → Build pipeline

```plaintext
{Researcher}, investigate how top e-commerce platforms handle checkout.
Then {Designer}, take those findings and design our checkout user journey.
```

```plaintext
{Researcher}, research accessibility patterns for data-heavy dashboards.
{Designer}, use that research to define our dashboard's information hierarchy
and interaction model.
```

### Team-wide fan-out with SMEs

```plaintext
Team, we're adding a real-time collaboration feature.
{Researcher} — investigate CRDT vs. OT approaches and WebSocket frameworks.
{Designer} — identify SMEs (collaborative editor power user, product manager,
  accessibility specialist) and run interviews.
Lead — start decomposing into work items once research and interviews are done.
```

### Gate development behind research, design, and SME validation

```plaintext
From now on, any new feature over P1 priority must have:
1. A research summary from {Researcher}
2. SME interviews run by {Designer}
3. A synthesized requirements brief
before development starts.
```

### Iterative SME feedback

```plaintext
We've built the MVP checkout flow. Bring back the SMEs from the original
interviews and have {Designer} walk them through the implementation.
Capture what we got right and what needs revision.
```

---

## Routing Rules

After adding these personas, set up routing so work flows to them automatically:

```plaintext
From now on, route all "should we use X?" questions to {Researcher}.
```

```plaintext
From now on, have {Designer} review all user-facing features before
they're assigned to developers.
```

```plaintext
Route all technology evaluation tasks to {Researcher}.
Route all UX and user journey work to {Designer}.
```

---

## Skills to Seed

Optionally, create skills to give these personas structured methodologies:

### Research methodology skill

```plaintext
Create a skill called research-methodology. It should cover: how to structure
a technology comparison (criteria matrix), how to evaluate library health
(stars, last commit, open issues, bus factor), and how to format a research
summary with a clear recommendation and trade-offs section.
```

### Design thinking skill

```plaintext
Create a skill called design-thinking. It should cover: the double diamond
process, how to write user personas (demographics, goals, frustrations),
how to map user journeys (stages, actions, thoughts, emotions, pain points),
and how to define acceptance criteria from the user's perspective.
```

### SME interview skill

```plaintext
Create a skill called sme-interviewing. It should cover: how to identify
relevant SME personas from a problem statement, how to write open-ended
interview questions that surface hidden requirements, how to structure a
multi-stakeholder interview sequence (who to talk to first and why),
how to synthesize conflicting perspectives into actionable requirements,
and how to format a stakeholder needs matrix.
```

---

## SME Lifecycle

Synthetic SMEs follow a deliberate lifecycle:

| Phase | What Happens | Output |
|---|---|---|
| **Identify** | Design Thinker analyzes the ask and proposes SME personas | SME roster with domain rationale |
| **Spawn** | Coordinator creates short-lived agents with domain charters | `.ai-team/agents/{sme-name}/charter.md` |
| **Interview** | Design Thinker asks prepared questions; SMEs respond in-character | Interview transcripts in `decisions/inbox/` |
| **Follow-up** | Design Thinker probes surprising or contradictory responses | Additional transcript entries |
| **Synthesize** | Design Thinker consolidates findings into a requirements brief | Requirements doc with stakeholder matrix |
| **Archive** | SMEs are retired after synthesis; knowledge lives in decisions | SME charters moved to `.ai-team/agents/_alumni/` |
| **Recall** | If needed later (e.g., MVP review), SMEs can be re-spawned from alumni | Same persona, updated with project context |

SMEs are intentionally ephemeral — they exist to inject domain knowledge into the team's shared memory, not to persist as permanent members.
