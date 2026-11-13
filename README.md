# IS373 Individual Record — Peter Balasis

**Review 1 · Plan** · due Nov 17, 2026, 1 p.m. ET  
Section 3 (group system) lives in the team's shared record, not here.

> **Status labels:** **planned** = proposed, not run · **observed locally** · **observed in CI** · **observed hosted**. At Plan, almost everything is *planned*. Sketches and expected answers below are **not** test results.

---

## Research review index

| | 1. Portfolio + career | 2. RAG app + technical |
|---|---|---|
| Sources | [Employer postings](#11-original-employer-postings) | [Technical sources](#21-technical-sources) · [Permitted-source manifest](#24-permitted-source-manifest) |
| Comparisons | [Two career directions](#12-two-career-directions) · [Two layouts](#15-portfolio-outline-and-two-lightweight-layouts) | [Keyword vs. vector vs. graph](#23-comparison-and-decision) |
| Decisions | [Target role/reader](#13-target-role-and-reader) · [Layout choice](#15-portfolio-outline-and-two-lightweight-layouts) | [Architecture](#25-planned-architecture) |
| Evidence / checks | [Responsibility → evidence map](#14-responsibility-to-evidence-map) | [Sample trace](#26-sample-representation-and-trace-sketch) · [Evaluation questions](#27-evaluation-questions) · [Stories/checks](#28-observable-storieschecks) |
| Peer review | [Workshop notes](#workshop-notes-peer-review) | [Workshop notes](#workshop-notes-peer-review) |

**Related repositories (existing, observed):**
- [`pb392/is373_ci_cd`](https://github.com/pb392/is373_ci_cd): containerized site with tested QA → production promotion on my DigitalOcean droplet ([xenoshin.com](https://xenoshin.com), [qa.xenoshin.com](https://qa.xenoshin.com)).
- [`pb392/my-app-studio`](https://github.com/pb392/my-app-studio): FastAPI app with accounts and server-enforced member/admin roles (APP-001–003).

---

## 1. Individual portfolio + career research

### 1.1 Original employer postings
| # | Employer · title | Original source | Date checked | Level / eligibility | Three responsibilities (paraphrased) | Required / preferred skills |
|---|---|---|---|---|---|---|
| P1 | 2K / Cat Daddy Games · **Associate Gameplay Engineer** | [Greenhouse](https://job-boards.greenhouse.io/2k/jobs/7724801003) | 2026-11-13 (open) | Full-time associate; onsite Kirkland, WA; BS in CS or related; $71,400–$105,660 (WA) | Design, write and debug gameplay code for mobile games · write system docs and test cases · work with QA to fix bugs and build new tools | Req: game dev experience, gameplay/UI/AI systems, C/C++/C#. Pref: mobile, iOS/Android |
| P2 | Riot Games · **Software Engineering Intern – Summer 2027 (Remote)** | [Riot careers](https://www.riotgames.com/en/work-with-us/job/8222014/software-engineering-intern-summer-2027-remote-los-angeles-usa) | 2026-11-13: **closed** (applications closed Nov 6, 2026; Riot's university Greenhouse board shows no openings). Kept as research evidence of direction B's responsibilities, not as an application target | 12-week internship; graduating in **2028**; enrolled in CS/Eng/Tech; GPA ≥ 2.5; US work authorization | Build back-end services for shared social/client/platform features · process real-time game data · build and maintain SDKs/APIs for internal game teams | Req: OOP language (Java/C++/C#), data structures and algorithms. Pref: game project in Unity/Unreal |
| P3 | Epic Games · **Engine Programmer Intern (Fortnite Online)**, 2027 | ☐ *Peter: open on [epicgames.com/careers](https://www.epicgames.com/site/en-US/careers/jobs) (intern filter) and paste the original link. Aggregators show it posted 2026-09-22, still accepting applications* | ☐ | Internship, Cary, NC, in person; BS in CS; US work authorization | Build and maintain shared online gameplay technology · contribute to online systems/toolsets for Unreal licensees · take solutions from concept to stable shipped code | Req: OOP + C++, networking/REST/back-end services. Pref: Java, interest in online multiplayer and games-as-a-service, Unreal/UEFN |

*Alternate for direction B:* Epic Games **Tools Programmer Intern** (Build Operations – Tools team, 2027 start), which works on internal tools used to make Fortnite and Unreal Engine. It is the closest match to my CI/CD work. ☐ Peter: confirm on Epic's careers site and consider swapping it in for the closed Riot posting.

*Eligibility check (Peter, private):* confirm graduation year against P2 and location/authorization for P1–P3. Record only the result here; keep the reasoning in Canvas.

### 1.2 Two career directions
| | **A. Gameplay programming** (P1, Epic gameplay intern roles) | **B. Game services, tools and build engineering** (P2, P3) |
|---|---|---|
| Day-to-day work | Player-facing mechanics in an engine (C++/Unreal, C#/Unity) | Back-end services, online features, build/test pipelines and developer tools behind the game |
| Main language signals | C++ almost everywhere | OOP language plus REST, services, CI/CD and Python/Java |
| My current evidence | No shipped engine project yet (gap) | CI/CD pipeline with tests gating releases; Docker deployment; FastAPI accounts and roles; planned RAG service |
| Gap to close | A small engine or gameplay prototype in C++/C# | More OOP depth (Java/C++), one game-adjacent service |

### 1.3 Target role and reader
**Provisional choice: Direction B.** The reader is a university recruiter or engineering manager hiring a game services/tools intern (P2 type). I chose B because my existing, verifiable work (tested deployment pipeline, auth/roles service) maps to its responsibilities, while A would currently rest on claims I can't back with evidence. I will keep a small gameplay prototype on the roadmap so A stays open.  
*Hypothesis, not employer fact:* that a game studio reader values service and pipeline work from a student without shipped game credits. *Planned check:* the peer workshop question below.

### 1.4 Responsibility-to-evidence map
| Employer responsibility (source) | My evidence | Status |
|---|---|---|
| Build and operate back-end services (P2, P3) | `my-app-studio` FastAPI app with REST endpoints, JWT sessions and role checks | observed (repo, CI) |
| Keep shipped code stable / tests before release (P1, P3) | `is373_ci_cd`: unit, integration and browser tests gate image publication; QA → prod promotion | observed in CI + hosted (Oct 15, 2026) |
| Write docs and test cases (P1) | READMEs, test evidence tables, SPEC.md in both repos | observed |
| Process game data / APIs for game teams (P2) | Elestrals meta-deck RAG app (section 2) | **planned** |
| C++ / gameplay systems (P1, P3) | — | **gap** → next action: small C++ or Unity prototype, date ☐ |

### 1.5 Portfolio outline and two lightweight layouts
**Pages:** (1) Home: one-line target ("game services & tools engineer"), plus top 2 projects · (2) Case study: Elestrals meta RAG app · (3) Case study: CI/CD deployment pipeline · (4) Case study: group system with my named contribution · (5) About + resume + GitHub/contact.

| | Layout 1 · **Evidence-first** | Layout 2 · **Biography-first** |
|---|---|---|
| Above the fold | Target role line + two project cards with "what I built / how it's checked" | Photo, personal intro, interests in games |
| Reviewer finds the work | 1 click | Scroll past intro |
| Risk | Can feel impersonal | Reviewer may leave before seeing evidence |

**Provisional decision:** evidence-first, since a recruiter skimming many applicants should reach verifiable work in one click. *This is a design hypothesis, not a measured finding.*

**Changed:** created this section; chose direction B and evidence-first layout (provisional).  
**Checked:** 2026-11-13: P1 open; P2 closed (kept as research). ☐ P3 original still to check.  
**Next:** open P3 (and the Tools intern alternate) on Epic's site; confirm eligibility; peer walkthrough; sketch both layouts.

---

## 2. Individual RAG app + technical research

**Research question / intended user:** Can an Elestrals player preparing for a tournament ask plain-language questions about the current meta ("what won Worlds?", "what Solar decks are strong?") and get answers grounded in, and linked to, permitted sources?

### 2.1 Technical sources
*Peter: open each one, add the date checked, and confirm my summaries against the course handout ([Vector/graph/RAG PDF](https://njit.instructure.com/courses/70733/files?preview=10598448)).*

| ID | Source | Used for | Date checked |
|---|---|---|---|
| T1 | Lewis et al., *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks* (2020), [arXiv:2005.11401](https://arxiv.org/abs/2005.11401) | Definition of RAG | 2026-11-13 ✓ |
| T2 | [pgvector](https://github.com/pgvector/pgvector) README | Vector storage in PostgreSQL | 2026-11-13 ✓ |
| T3 | [Neo4j graph database concepts](https://neo4j.com/docs/getting-started/graph-database/) | Nodes, relationships, properties | 2026-11-13 ✓ |
| T4 | [SQLite FTS5](https://www.sqlite.org/fts5.html) | Keyword-search baseline | 2026-11-13 ✓ |
| T5 | [Sentence-Transformers docs](https://www.sbert.net/) | Local embedding models (compared, not chosen; see 2.5) | 2026-11-13 ✓ |
| T6 | [sqlite-vec](https://github.com/asg017/sqlite-vec) README | Vector search inside SQLite | 2026-11-13 ✓ |

### 2.2 Concepts (my words; to verify against T1–T5)
- **RAG:** before the model answers, retrieve relevant passages from my own sources and put them in the prompt, so the answer is grounded in and can cite those sources instead of the model's memory.
- **Chunking:** splitting documents into small retrievable pieces (e.g., one deck summary or one paragraph). Too big and retrieval is vague; too small and context is lost.
- **Embeddings:** a model turns text into a vector of numbers; texts with similar meaning land close together, so "Celestleo deck" can match "Pride archetype".
- **Vector database:** stores those vectors and finds the nearest ones to a question's vector.
- **Graph database:** stores **entities** (Deck, Card, Archetype, Tournament, Element) and **relationships** (Deck–CONTAINS{qty}→Card, Deck–PLACED{rank}→Tournament). This is good for counting and "which decks share card X" questions.
- **Import:** the repeatable pipeline from source → cleaned text/records → chunks/entities → stored, with stable source IDs so re-importing doesn't duplicate anything.

### 2.3 Comparison and decision
| Question type (example) | Keyword (FTS5) baseline | Vector | Graph / structured |
|---|---|---|---|
| "What archetype won the 2026 World Championship?" | Works if wording matches | Works with paraphrase | Works if results are modeled |
| "Which deck did the champ use?" (paraphrase) | Likely misses | **Good** | Works |
| "How many copies of card X are in the winning list?" | Unreliable | **Poor** (similarity ≠ counting) | **Good** |
| "Which cards appear in both top archetypes?" | Poor | Poor | **Good** |

**Decision: both, in a lightweight form.** Meta-deck data is mostly *relationships and counts* (decks, cards, quantities, placements), which vectors handle badly. My written strategy notes are *passages*, which vectors handle well. Plan: one **SQLite** database file with **relational tables for the deck→card→archetype graph**, **sqlite-vec for text-chunk vectors**, and **FTS5 keyword search** as the baseline to beat.
**Revised 2026-11-13 after checking hosting (see 2.5):** my first plan was PostgreSQL + pgvector. On a 1 GB droplet already running two app containers and a proxy, a separate database server costs RAM I don't have. SQLite runs inside the app process, as one file, with no extra service. PostgreSQL + pgvector stays the fallback if the data outgrows SQLite.  
**Alternative rejected for now:** Neo4j, a true graph database. It's more expressive, but it runs on the Java VM and needs more memory than my whole 1 GB droplet has to spare, and my graph is shallow (2–3 hops).  
**Check that could change this:** if the evaluation's relationship questions need deeper traversals than simple SQL joins handle cleanly, I'll revisit Neo4j (it would need a bigger droplet or a hosted graph database).

### 2.4 Permitted-source manifest
Governing rule: [Elestrals Fan Content Policy](https://www.elestrals.com/fan-content-policy) (last updated Sep 6, 2024; read 2026-11-13). Fan content must be free and non-commercial, must state it is unofficial and display the required notice, and must not exactly copy Elestrals IP (e.g., card reproductions).

| ID | Source | Owner | Permission basis | How I'll use it |
|---|---|---|---|---|
| S1 | [2026 World Championship results](https://www.elestrals.com/news/2026-world-championship-results-your-bride-is-here) (official) | Elestrals LLC | Fan Content Policy **+ direct permission from the Elestrals team** (personal contact) | Facts (winner, top archetypes, elements) in **my own words**, linked back. No copied text or images |
| S2 | [TopElestrals](https://www.topelestrals.com) tournament results and decklists | TopElestrals site owner | **Direct permission from the site owner** (personal contact) | Decklists (deck → card → quantity) and placements, attributed and linked. Articles by other authors are excluded unless their writers agree |
| S3 | My own deck/strategy notes | Me | Own work | Main text corpus. Each note cites the S1/S2 facts it relies on |

**Permission record:** both permissions were given to me directly. ☐ Before Build, get each in writing (a short email or DM reply) and save it, or a screenshot with personal details removed, as `docs/permissions/` evidence, recording who confirmed, the date and what they agreed to. This also settles the policy's "game mechanics" consent clause. No card text or card art is stored. Every page shows the required unofficial-fan-content notice.

### 2.5 Planned architecture
```
S1 + S2 + S3 → admin import (stable source IDs, version, date)
   ├─ structured: Tournament · Deck · Archetype · Card · Element tables + deck_cards(qty)
   └─ text: notes → heading/paragraph chunks → embeddings → sqlite-vec
Question → keyword + vector retrieval (+ SQL lookup for count/relationship questions)
   → top chunks/records → LLM prompt ("answer only from these; cite IDs; say if missing")
   → answer with clickable source citations
```
- **App (decided 2026-11-13):** a **new repository** for the RAG app, reusing the FastAPI accounts/admin-role pattern from `my-app-studio`. That repo is still awaiting grading, so it stays unchanged. The admin role guards import controls.
- **Hosting:** Docker on my DigitalOcean droplet behind the existing Traefik HTTPS proxy, at the **planned** URL `rag.xenoshin.com` (chosen 2026-11-13; DNS record not yet created).
- **Droplet (observed 2026-11-13, DigitalOcean dashboard):** Basic · 1 vCPU · **1 GB RAM** · 25 GB disk. Already running: QA + production containers, Traefik proxy, WUD updater.
- **Freeing memory (decided 2026-11-13):** the CI/CD assignment (`is373_ci_cd`) is already graded, so at Build I may retire its QA and production containers to free RAM for the RAG app. Its record of observed results (Oct 15, 2026) stays in that repo. ☐ Planned check: `free -m` before and after.
- **Models (decided):** a **hosted embedding API**, not a local model. A local Sentence-Transformers model pulls in PyTorch, which alone can use most of 1 GB of RAM. The corpus is small (tens of notes and decklists), so embedding it costs very little. Generation via a hosted LLM API. API keys live in server env only, never in Git. ☐ Pick the provider and record its price.
- **Constraints:** RAM is the tight one. ☐ Planned check: run `free -m` and `docker stats` on the droplet before Build and record free memory. ☐ Add a 1–2 GB swap file as a safety margin. Disk (25 GB) is ample for a few-MB SQLite file. ☐ Monthly API budget · ☐ rate limiting so visitors can't run up costs.

### 2.6 Sample representation and trace sketch
> **Illustrative sketch, not an executed result.**

*S1 fact, restated:* the first Elestrals World Championship (2026) was won by Mike Thomas ("Trishula"); Celestleo's Pride and Fish Nexus were the top archetypes.

```
tournament: {id: T-2026-WORLDS, name: "2026 Elestrals World Championship", source: S1}
archetype:  {id: A-CELESTLEO-PRIDE, name: "Celestleo's Pride", source: S1}
deck:       {id: D-2026W-1, tournament: T-2026-WORLDS, rank: 1, archetype: A-CELESTLEO-PRIDE, source: S1}
chunk:      {id: S3-note-01#2, text: "<my own summary of how the deck plays>", cites: [S1]}
```
**Trace:** "What deck won Worlds?" → vector match on `S3-note-01#2` + lookup on `D-2026W-1` → answer: "Celestleo's Pride [S1]" with link.  
**Where it can fail:** if S1 isn't imported, a model might still "remember" an answer. The prompt and the absent-evidence check (Q5) are meant to catch this.

### 2.7 Evaluation questions
Expected sources are recorded **before** running anything.

| # | Question | Tests | Expected evidence |
|---|---|---|---|
| Q1 | What archetype won the 2026 Elestrals World Championship? | Direct fact | S1 / D-2026W-1 |
| Q2 | Which deck did the first world champ play? | Paraphrase (vector) | S1 / D-2026W-1 |
| Q3 | Which elements showed up most in the top cards at Worlds? | Aggregate fact | S1 |
| Q4 | How many copies of [card] are in the winning list? | Count (structured) | S2 decklist → deck_cards row for D-2026W-1 |
| Q5 | What is the ban list for the 2027 season? | **Deliberately absent** | None. The app must say it lacks evidence |

### 2.8 Observable stories/checks
All **planned**; no pass results claimed.
1. A reader can click any citation in an answer and reach the cited source.
2. Running the same import twice creates no duplicate decks, cards or chunks.
3. Q5 (absent evidence) gets an "I don't have a source for that" answer, not a guess.
4. A logged-out visitor or member cannot reach import/admin endpoints (server returns 401/403).
5. Every page shows the Elestrals unofficial-fan-content notice.

**Changed:** created this section; decided on hybrid structured + vector search. Chose `rag.xenoshin.com` and a new app repo (my-app-studio stays untouched until graded); may retire the graded CI/CD containers at Build. After recording the droplet size (1 GB RAM), switched from PostgreSQL + pgvector to SQLite + sqlite-vec, and from a local embedding model to a hosted embedding API.  
**Checked:** read the Fan Content Policy and S1 on 2026-11-13. Droplet size recorded 2026-11-13. T1–T6 and the course handout checked against section 2.2 on 2026-11-13: all match, no corrections.  
**Next:** get written copies of the Elestrals and TopElestrals permissions; check droplet RAM; write 3–5 S3 notes; record expected answers for Q1–Q5.

---

## Workshop notes (peer review)
*Fill in after a real classmate walks through this index without my explanation first. AI critique doesn't count.*

| | Career | RAG |
|---|---|---|
| Peer / date | ☐ | ☐ |
| Prompt | Can you trace one portfolio choice back to an employer responsibility and my actual work? Which part is employer fact vs. my hypothesis? | Can you follow S1 through the representation, retrieval and answer? Where could missing evidence give an unsupported answer? Why hybrid over keyword-only? |
| Their question / problem | ☐ | ☐ |
| GitHub issue | ☐ link | ☐ link |
| My decision + doc change | ☐ | ☐ |

## AI use
Claude helped find candidate postings, draft concept explanations and structure this record. I verified: ☐ each posting on its original page · ✓ each technical source (2026-11-13) · ☐ the Fan Content Policy reading. Conclusions and choices are mine; anything unchecked stays marked ☐.
