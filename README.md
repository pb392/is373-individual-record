# IS373 Individual Record — Peter Balasis

**Review 2 · Build** · due Nov 24, 2026, 1 p.m. ET (Review 1 · Plan, Nov 17, is preserved below)  
**Live:** portfolio [xenoshin.com](https://xenoshin.com) · RAG app [rag.xenoshin.com](https://rag.xenoshin.com) · code [pb392/xenoshin-site](https://github.com/pb392/xenoshin-site)  
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
| **Build (Review 2)** | [Hosted portfolio + finding that shaped it](#16-build-hosted-portfolio-foundation-review-2) · **observed hosted** | [Hosted app, import record, trace, checks](#29-build-hosted-import--retrieval--cited-chat-review-2) · **observed hosted + CI** |

**Related repositories (existing, observed):**
- [`pb392/is373_ci_cd`](https://github.com/pb392/is373_ci_cd): containerized site with tested QA → production promotion on my DigitalOcean droplet ([xenoshin.com](https://xenoshin.com), [qa.xenoshin.com](https://qa.xenoshin.com)).
- [`pb392/my-app-studio`](https://github.com/pb392/my-app-studio): FastAPI app with accounts and server-enforced member/admin roles (APP-001–003).

---

## 1. Individual portfolio + career research

### 1.1 Original employer postings
| # | Employer · title | Original source | Date checked | Level / eligibility | Three responsibilities (paraphrased) | Required / preferred skills |
|---|---|---|---|---|---|---|
| P1 | 2K / Cat Daddy Games · **Associate Gameplay Engineer** | [Greenhouse](https://job-boards.greenhouse.io/2k/jobs/7724801003) | 2026-11-13: open. **2026-11-16: closed** (link now redirects to 2K's general board). Kept as dated research | Full-time associate; onsite Kirkland, WA; BS in CS or related; $71,400–$105,660 (WA) | Design, write and debug gameplay code for mobile games · write system docs and test cases · work with QA to fix bugs and build new tools | Req: game dev experience, gameplay/UI/AI systems, C/C++/C#. Pref: mobile, iOS/Android |
| P2 | Epic Games · **Tools Programmer Intern (Unreal Engine, Content Architecture team)**, 2027 | [Epic careers](https://www.epicgames.com/site/careers/jobs/6200355004?lang=en-US) | 2026-11-13 (open; read in full by me) | Internship, flexible 2027 start; location not stated in the text ("the posting location"); must be authorized to work there | Write clean, documented C++ for tool systems that configure how game content is packaged, distributed and streamed · resolve bugs and workflow issues for internal teams · work in Unreal Engine's editor and toolchain, owning implementation decisions | Req: strong C++ fundamentals; OOP, patterns, algorithms, data structures; debugging; developing on Windows. Plus: Unreal Engine experience (not required) |
| P3 | Epic Games · **Engine Programmer Intern (Fortnite Online)**, 2027 | [Epic careers](https://www.epicgames.com/site/careers/jobs/6202659004?lang=en-US) | 2026-11-13 (open; opened by me) | Internship, Cary, NC, in person; BS in CS; US work authorization | Build and maintain shared online gameplay technology · contribute to online systems/toolsets for Unreal licensees · take solutions from concept to stable shipped code | Req: OOP + C++, networking/REST/back-end services. Pref: Java, interest in online multiplayer and games-as-a-service, Unreal/UEFN |

*Also researched:* Epic **Tools Programmer Intern (Fortnite)**, [Epic careers](https://www.epicgames.com/site/careers/jobs/6147167004?lang=en-US), open 2026-11-13, the same role on the Fortnite side. Riot Games **Software Engineering Intern – Summer 2027** ([Riot careers](https://www.riotgames.com/en/work-with-us/job/8222014/software-engineering-intern-summer-2027-remote-los-angeles-usa)) was **closed** when checked on 2026-11-13 (applications closed Nov 6, 2026). I kept it as evidence of direction B's responsibilities: back-end services for shared social/platform features, real-time game data, and SDKs/APIs for game teams.

*Eligibility check (Peter, private):* confirm location/authorization: P1 Kirkland, WA (onsite); P3 Cary, NC (in person); P2's listing text does not state a location. Record only the result here; keep the reasoning in Canvas.

### 1.2 Two career directions
| | **A. Gameplay programming** (P1, Epic gameplay intern roles) | **B. Game services, tools and build engineering** (P2, P3) |
|---|---|---|
| Day-to-day work | Player-facing mechanics in an engine (C++/Unreal, C#/Unity) | Back-end services, online features, build/test pipelines and developer tools behind the game |
| Main language signals | C++ almost everywhere | C++ for engine tools (P2); OOP plus REST/services (P3) |
| My current evidence | No shipped engine project yet (gap) | CI/CD pipeline with tests gating releases; Docker deployment; FastAPI accounts and roles; planned RAG service |
| Gap to close | A small engine or gameplay prototype in C++/C# | **C++** (P2 requires it), plus one game-adjacent service |

### 1.3 Target role and reader
**Provisional choice: Direction B.** The reader is a university recruiter or engineering manager hiring a game services/tools intern (P2/P3 type: Epic tools and online-services internships). I chose B because my existing, verifiable work (tested deployment pipeline, auth/roles service) maps to its responsibilities, while A would currently rest on claims I can't back with evidence. I will keep a small gameplay prototype on the roadmap so A stays open.  
*Finding (2026-11-13):* reading P2 in full showed that Epic's tools internship is C++ engine work, not the Python/CI work I expected. So C++ is a gap for **both** directions, which makes a small C++ project my most important next step either way.
*Hypothesis, not employer fact:* that a game studio reader values service and pipeline work from a student without shipped game credits. *Planned check:* the peer workshop question below.

### 1.4 Responsibility-to-evidence map
| Employer responsibility (source) | My evidence | Status |
|---|---|---|
| Build and operate back-end/online services (P3) | `my-app-studio` FastAPI app with REST endpoints, JWT sessions and role checks | observed (repo, CI) |
| Keep shipped code stable; tests before release (P1, P3) | `is373_ci_cd`: unit, integration and browser tests gate image publication; QA → prod promotion | observed in CI + hosted (Oct 15, 2026) |
| Write docs and test cases (P1) | READMEs, test evidence tables, SPEC.md in both repos | observed |
| Resolve bugs and workflow issues for internal teams; packaging and distribution of builds (P2) | `is373_ci_cd`: automated build → test → publish → deploy pipeline (a release/distribution workflow, but in Python/Docker, not C++/Unreal); RAG app import pipeline (section 2) | observed in CI + hosted (Oct 15, 2026); RAG part **planned** |
| C++ / gameplay and engine-tool systems (P1, P2, P3) | — | **gap** → next action: small C++ or Unity prototype, date ☐ |

### 1.5 Portfolio outline and two lightweight layouts
**Pages:** (1) Home: one-line target ("game services & tools engineer"), plus top 2 projects · (2) Case study: Elestrals meta RAG app · (3) Case study: CI/CD deployment pipeline · (4) Case study: group system with my named contribution · (5) About + resume + GitHub/contact.

| | Layout 1 · **Evidence-first** | Layout 2 · **Biography-first** |
|---|---|---|
| Above the fold | Target role line + two project cards with "what I built / how it's checked" | Photo, personal intro, interests in games |
| Reviewer finds the work | 1 click | Scroll past intro |
| Risk | Can feel impersonal | Reviewer may leave before seeing evidence |

**Provisional decision:** evidence-first, since a recruiter skimming many applicants should reach verifiable work in one click. *This is a design hypothesis, not a measured finding.*

**Changed:** created this section; chose direction B and evidence-first layout (provisional).  
**Checked:** 2026-11-13: P1, P2 and P3 open on their original pages; Riot internship closed (kept as research). 2026-11-16: P1 closed (kept as dated research, as the peer review suggested).  
**Next (at Plan):** confirm eligibility; peer walkthrough; sketch both layouts.

### 1.6 Build: hosted portfolio foundation (Review 2)
**Site:** [xenoshin.com](https://xenoshin.com) · **source:** [`portfolio/`](https://github.com/pb392/xenoshin-site/tree/main/portfolio) · **status: observed hosted** (2026-11-19, commit [`84876ad`](https://github.com/pb392/xenoshin-site/commit/84876ad))

| Required part | Where | Status |
|---|---|---|
| Introduction + target direction | [Home](https://xenoshin.com): "I build and test the systems behind games", aiming for game services & tools engineering | observed hosted |
| Navigation | Home · Projects · About · GitHub on every page, plus a skip link | observed hosted |
| Project sections | [Elestrals Meta Assistant](https://xenoshin.com/projects/elestrals-rag.html) (**Live · case study in progress**), [Tested release pipeline](https://xenoshin.com/projects/ci-cd.html) (**Completed**), [Group content system](https://xenoshin.com/projects/group.html) (**In progress**, placeholder), C++ game tool (**Planned**) | observed hosted |
| About + skills with evidence | [About](https://xenoshin.com/about.html): each skill links to its project; C++ listed as a gap, not a claim | observed hosted |

**Career-research finding that shaped the site:** all three postings ask for C++, and reading Epic's tools internship in full (§1.1) showed it is C++ engine work. So the home page leads with work I can prove (tested pipeline, live RAG service) and lists a C++ tool as the next project instead of claiming the skill. The layout follows the §1.5 decision (evidence-first: projects reachable in one click). The site states this on the home page under "Why the site looks like this".

**Labels kept honest:** the RAG case study is marked *in progress*; the group project page is a placeholder that says so; the C++ tool is *planned*. The CI/CD demo sites were retired after grading, and its case study says so and links to the recorded evidence.

**Changed:** built the evidence-first layout from §1.5 (layout 1); hosted it on xenoshin.com in place of the graded CI/CD demo; added status badges.  
**Checked:** 2026-11-19: CI [run 44592155422](https://github.com/pb392/xenoshin-site/actions/runs/44592155422) passed `scripts/check_site.py` (6 pages: every internal link and anchor resolves, one `h1`, `lang`, viewport) and served the built image; [hosted check run](https://github.com/pb392/xenoshin-site/actions/runs/44594983532) fetched https://xenoshin.com over HTTPS. Opened in a browser: home, projects and about render.  
**Next:** keyboard-only and mobile walkthrough with notes (Release); add the group case study when that work exists; a real reader test of whether the target role is clear in 10 seconds.

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
| S3 | My own deck/strategy notes, e.g. [S3-note-01](docs/notes/S3-note-01-meta-overview.md) (2026-11-13) | Me | Own work | Main text corpus. Each note cites the S1/S2 facts it relies on |

**Permission record:** both permissions were given to me directly. ☐ Before Build, get each in writing (a short email or DM reply) and save it, or a screenshot with personal details removed, as `docs/permissions/` evidence, recording who confirmed, the date and what they agreed to. This also settles the policy's "game mechanics" consent clause. No card text or card art is stored. Every page shows the required unofficial-fan-content notice.

### 2.5 Planned architecture
```
S1 + S2 + S3 → admin import (stable source IDs, version, date)
   ├─ structured: Tournament · Deck · Archetype · Card · Element · Boss tables + deck_cards(qty), archetype_bosses
   │            every relationship row carries provenance (see 2.6)
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
- **Import cadence:** Elestrals runs a Premier event every other weekend, and TopElestrals (S2) posts results a few days later (the Columbus Open, Nov 7–8, was not yet posted on Nov 13). So the plan is to re-import about every two weeks, which makes "importing twice creates no duplicates" (story 2) a real requirement.
- **Constraints:** RAM is the tight one. ☐ Planned check: run `free -m` and `docker stats` on the droplet before Build and record free memory. ☐ Add a 1–2 GB swap file as a safety margin. Disk (25 GB) is ample for a few-MB SQLite file. ☐ Monthly API budget · ☐ rate limiting so visitors can't run up costs.

### 2.6 Sample representation and trace sketch
> **Illustrative sketch, not an executed result.** No import has run yet; this shows how one real permitted source would be represented.

**Source:** [S3-note-01](docs/notes/S3-note-01-meta-overview.md), my own meta overview (written 2026-11-13).

**Chunks** (one per idea, split at sentence boundaries, each keeping its source ID):
```
S3-note-01#1  "...at the last event, the Columbus Open, the majority of the decks played were
               Athena Dimenshen, Apollo Celestleo, Hades Trifernal, Fish, Hades Sloth, and Sulfury..."
S3-note-01#2  "The main topping decks were Hades Sloth, Fish, Dionysus Duggy ... with the winner playing Fish."
S3-note-01#3  "...the meta is less defined by the decks that are played, but rather by the bosses...
               Celestleo, Dimenshen, Neandersloth, and Fish ... are all very difficult bosses to beat..."
```
**Entities and relationships** (the graph-shaped part, stored as tables):
```
Tournament  T-COLUMBUS-OPEN  (2026-11-07 to 11-08)
Archetype   Athena Dimenshen · Apollo Celestleo · Hades Trifernal · Fish · Hades Sloth · Sulfury · Dionysus Duggy
Boss        Neandersloth CoKhione · Trifernal CoHades · Sulfury · Celestleo · Dimenshen CoAthena ·
            Apheros CoAphrodite · Magneros CoAphrodite · Lochagon · Duggabyss · Centaurbor CoDionysus
Archetype ─PLAYED_AT→ Tournament                     e.g. Athena Dimenshen ─→ T-COLUMBUS-OPEN (no numeric rank: the note gives an order, not counts)
Archetype ─TOPPED_AT{placement}→ Tournament          e.g. Fish ─{1st}→ T-COLUMBUS-OPEN
Archetype ─USES_BOSS→ Boss   (from S3-note-02)       e.g. Hades Sloth ─→ Neandersloth CoKhione
                                                           Dio Duggy   ─→ Neandersloth CoKhione (one boss, two archetypes)
```
**Provenance on every assertion** (added 2026-11-16 after peer review, [issue #1](https://github.com/pb392/is373-individual-record/issues/1)). Each relationship row, not just each entity, records where it came from and how sure it is:

| Assertion | Source · version | Event date | Imported / checked | Verification status |
|---|---|---|---|---|
| Fish ─TOPPED_AT{1st}→ Columbus Open | S3-note-01 · v1 | 2026-11-07/08 | 2026-11-13 | **author knowledge** (S2 results not yet posted) |
| Athena Dimenshen ─PLAYED_AT→ Columbus Open | S3-note-01 · v1 | 2026-11-07/08 | 2026-11-13 | **author knowledge**; "most played" order is my estimate, not a count |
| Hades Sloth ─USES_BOSS→ Neandersloth CoKhione | [S3-note-02](docs/notes/S3-note-02-archetype-bosses.md) · v1 | — | 2026-11-13 | **author knowledge** |
| Celestleo archetype won 2026 Worlds | S1 (official) | 2026 Worlds | ☐ at import | **externally verified** |

Statuses: *externally verified* (S1/S2 page), *author knowledge* (my notes), *unknown* (no source; the app must not guess). When S2 posts the Columbus Open results, those rows are re-imported as externally verified and the author-knowledge rows are kept, not overwritten.

**Trace:** "Who won the last big tournament?" → vector search matches `S3-note-01#2` ("winner playing Fish"), and the lookup Fish ─TOPPED_AT{1st}→ T-COLUMBUS-OPEN returns the same claim → answer: "According to my notes as of Nov 13, a Fish deck won the Columbus Open (Nov 7–8) [S3-note-01; not yet confirmed by tournament results]". The chunk and the row come from the **same note**, so their agreement is not independent confirmation; the answer says so.
**Where it can fail:** "last event" is relative: once a newer tournament is imported, this chunk would give an outdated answer unless the tournament's date is stored and the newest is preferred. That is why each tournament stores its date and answers say "latest **imported** event, as of <import date>". A stored date alone cannot prove that no newer event exists but hasn't been imported (checks 6–7 below). If no source is imported, a model might still "remember" an answer; the prompt and the absent-evidence check (Q5) are meant to catch that.

### 2.7 Evaluation questions
Expected sources are recorded **before** running anything.

| # | Question | Tests | Expected evidence |
|---|---|---|---|
| Q1 | What archetype won the 2026 Elestrals World Championship? | Direct fact | S1 / D-2026W-1 |
| Q2 | Which deck did the first world champ play? | Paraphrase (vector) | S1 / D-2026W-1 |
| Q3 | Which elements showed up most among the cards S1 lists for the Worlds top decks? | Aggregate fact over a stated set | S1 (denominator = the cards S1 lists) |
| Q4 | How many copies of a specific card are in the winning Worlds list? | Count (structured) | S2 decklist → deck_cards row for D-2026W-1. ☐ Choose the exact card and expected quantity from the imported list at Build |
| Q5 | What is the ban list for the 2027 season? | **Deliberately absent** | None. The app must say it lacks evidence |
| Q6 | Which deck won the Columbus Open? | Fact from my own note | S3-note-01#2 → Fish |
| Q7 | Which bosses are hardest to beat right now? | Paraphrase + opinion | S3-note-01#3 → Celestleo, Dimenshen, Neandersloth, Fish, **attributed as my opinion** ("according to the author's notes…"), not stated as fact |
| Q8 | Which decks run Neandersloth CoKhione? | Relationship (one boss, many archetypes); vectors alone tend to miss one | S3-note-02 → Hades Sloth and Dio Duggy |

### 2.8 Observable stories/checks
All **planned**; no pass results claimed.
1. A reader can click any citation in an answer and reach the cited source.
2. Running the same import twice creates no duplicate decks, cards or chunks.
3. Q5 (absent evidence) gets an "I don't have a source for that" answer, not a guess.
4. A logged-out visitor or member cannot reach import/admin endpoints (server returns 401/403).
5. Every page shows the Elestrals unofficial-fan-content notice.

*Added 2026-11-16 from peer review ([issue #1](https://github.com/pb392/is373-individual-record/issues/1)), also planned:*

| # | Fixture (input data) | Question | Expected behavior |
|---|---|---|---|
| 6 | Columbus Open + a newer test event (e.g. a Premier dated 2026-11-21) | "Who won the last tournament?" | Answers with the newer event and cites it; includes "latest imported event, as of <date>" |
| 7 | Only Columbus Open imported, newer event exists but not imported | Same | Answers Columbus **with** the "as of" coverage date, so the reader can see it may be stale |
| 8 | Columbus Open with no decklist (S2 not posted) | "How many copies of <card> did the winner run?" | "Insufficient evidence"; never returns 0 or guesses from the archetype |
| 9 | Empty corpus (nothing imported) | Any question, e.g. Q1 | "I have no sources loaded"; no answer from model memory |
| 10 | Two sources disagree (e.g. S3-note-01 says Fish won; a test S2 row says another deck) | "Who won the Columbus Open?" | Cites both with versions and says they disagree, or applies the documented rule *externally verified > author knowledge* and says it did. Neither row is silently overwritten |

**Changed:** created this section; decided on hybrid structured + vector search. Chose `rag.xenoshin.com` and a new app repo (my-app-studio stays untouched until graded); may retire the graded CI/CD containers at Build. After recording the droplet size (1 GB RAM), switched from PostgreSQL + pgvector to SQLite + sqlite-vec, and from a local embedding model to a hosted embedding API.  
**Checked:** read the Fan Content Policy and S1 on 2026-11-13. Droplet size recorded 2026-11-13. T1–T6 and the course handout checked against section 2.2 on 2026-11-13: all match, no corrections.  
**Changed 2026-11-16 (peer review, issue #1):** removed the unsupported numeric popularity rank; added per-assertion provenance and verification status; added Boss/archetype_bosses to the schema; made Q3 and Q4 specific; marked Q7 as opinion; added planned checks 6–10 for stale, missing and conflicting evidence.  
**Next (at Plan):** get written copies of the Elestrals and TopElestrals permissions; check droplet RAM; link the Columbus Open S2 results once posted; record expected answers for Q1–Q5; at Build, save the exact chunk text/offsets and a small SQL fixture so another reviewer can reproduce the trace.

### 2.9 Build: hosted import → retrieval → cited chat (Review 2)
**App:** [rag.xenoshin.com](https://rag.xenoshin.com) · **code:** [`rag/`](https://github.com/pb392/xenoshin-site/tree/main/rag) · **revision:** [`84876ad`](https://github.com/pb392/xenoshin-site/commit/84876ad) (shown in the app footer and at [/health](https://rag.xenoshin.com/health)) · **status: observed hosted** 2026-11-19

| Stage | Actual evidence | Status |
|---|---|---|
| Source manifest + import | [Manifest](https://github.com/pb392/xenoshin-site/blob/main/rag/corpus/manifest.json) (4 sources with owner, permission, version, status) · live [import record](https://rag.xenoshin.com/import-record): 4 sources, 16 chunks, 16 embedded, 3 tournaments, 12 placements, 28 decklist rows, 12 boss links | observed hosted |
| Repeat import | Test `test_repeat_import_creates_no_duplicates_and_embeds_nothing` and admin re-import test (0 new, 0 changed, 0 embedded) | observed in CI |
| Sample representation | Text chunks: [S3-note-02 source page](https://rag.xenoshin.com/sources/S3-note-02) · structured rows: [winning decklist table](https://rag.xenoshin.com/sources/S2-premier-2026-10-24#deck-d-premier-2026-10-24-1) | observed hosted |
| Query → retrieval → answer trace | [Live question](https://rag.xenoshin.com/?q=Which%20decks%20run%20Neandersloth%20CoKhione%3F), then open "How this answer was found": evidence IDs, keyword/vector/fusion scores, verification status and the exact prompt sent to Gemini | observed hosted |
| Cited answers + evaluation | [Hosted results, 9/9 passed](https://github.com/pb392/xenoshin-site/blob/main/rag/eval/hosted/2026-11-19/results.md) ([raw JSON](https://github.com/pb392/xenoshin-site/blob/main/rag/eval/hosted/2026-11-19/results.json)), expected answers [written first](https://github.com/pb392/xenoshin-site/blob/main/rag/eval/questions.json) | observed hosted |
| Missing evidence | Q5 (2027 ban list) → "I don't have a source for that…"; C8 (Columbus card count, no decklist) → refused, not "0 copies" | observed hosted |
| Tests | 23 tests ([CI run 44592155422](https://github.com/pb392/xenoshin-site/actions/runs/44592155422)): import idempotence, re-embed only changed text, boss relationship, exact count, missing decklist ≠ 0, latest event + coverage line, newer event, conflicting sources, empty corpus, citation removal/withholding, admin 401/403, rate limit, source anchors | observed in CI |

**Real trace (hosted, 2026-11-19):** question "Which decks run Neandersloth CoKhione?" → SQL lookup `S3-note-02#boss-neandersloth-cokhione` (author knowledge) + fused keyword/vector chunks `S3-note-02#5`, `S3-note-02#2` → Gemini answer: "According to the author's notes, the archetypes that run Neandersloth CoKhione are Dio Duggy (Dionysus Duggy) and Hades Sloth [S3-note-02#boss-neandersloth-cokhione; S3-note-02#5; S3-note-02#2]". The citation check confirmed all three IDs were in the retrieved evidence. This is Q8 from §2.7: the relationship question that vectors alone tend to half-answer.

**Changes from the Plan, and why:**
- **No sqlite-vec:** with 16 chunks, cosine similarity over vectors stored in SQLite is simpler and needs no native extension. Revisit if the corpus grows past a few thousand chunks.
- **S2 = October 24 Premier, not the Columbus Open:** Columbus results still weren't on TopElestrals (checked 2026-11-19), so the newest posted Premier was imported, with its full winning decklist. Q4 now asks about that deck. Player handles are deliberately not stored.
- **Admin token instead of accounts:** import is the only privileged action, so a server-only bearer token protects it (401 without, 403 wrong). Accounts from `my-app-studio` weren't needed for one endpoint.
- **New repo + retired CI/CD containers** as decided at Plan, with models `gemini-embedding-2` (768 dims) and `gemini-3.5-flash-lite` (current Gemini model list checked 2026-11-19).

**Mocks and limits (labeled):**
- The automated tests use **test-only** hash embeddings and scripted generators. They check the pipeline's logic, not Gemini's quality. Only the hosted evaluation uses the real models.
- 9 questions is a small check; a pass means correct status, citation source and key terms, not that every sentence is true.
- Columbus Open facts are **author knowledge** only. The Worlds event date isn't in S1, so the app shows the article date (2026-03-27).
- Free-tier Gemini: Google may use free-tier inputs; only public tournament data is sent. Public use is capped (300-char questions, 8/min per visitor, 300/day).
- Not yet shown: persistence across a container restart, keyboard/mobile checks, written permission copies (Release stage).

**Changed:** built and hosted the app; switched the S2 event and dropped sqlite-vec (above).  
**Checked:** 2026-11-19: CI 23/23 tests + container smoke test; hosted evaluation 9/9; live answer and trace opened in a browser; `/admin/import` returns 401 over HTTPS.  
**Next:** add **play.elestrals.com** as source S4, the official site where Premier decklists are submitted, which also has the Worlds winning decklist dated 2026-03-21 (fixes the date limit); import the Columbus Open once posted; restart-persistence and repeat-import checks on the server; save written permissions; a real peer test of the live app.

---

## Workshop notes (peer review)
*The course counts only a real classmate's walkthrough, not AI critique. Jorge used AI to help write his review, and confirmed to me on 2026-11-16 that he walked through the record himself and that the feedback is his. ☐ His written confirmation on [issue #1](https://github.com/pb392/is373-individual-record/issues/1).*

| | Career | RAG |
|---|---|---|
| Peer / date | Jorge Sanchez · review written 2026-11-15 with AI assistance; **Jorge walked through the record himself** (confirmed to me 2026-11-16) | Same |
| Prompt | Can you trace one portfolio choice back to an employer responsibility and my actual work? Which part is employer fact vs. my hypothesis? | Can you follow S1 through the representation, retrieval and answer? Where could missing evidence give an unsupported answer? Why hybrid over keyword-only? |
| Their question / problem | Is CI/CD a fair match for Epic's C++ tools role? Partial: shows release discipline, not engine-tool C++. Direction B is realistic only with a C++ project (Unity/C# alone wouldn't close it). Also: P1 link now redirects; P2 location unstated | The trace is clear but the note→row "agreement" isn't independent; the popularity rank had no basis; checks didn't cover stale, missing-decklist, empty-corpus or conflicting evidence; the schema lacked Boss/archetype_bosses |
| GitHub issue | Smaller points kept in [his review](https://github.com/yungjorge/is373-individual-record/blob/main/docs/peer-review.md) | [#1 Add provenance and freshness cases](https://github.com/pb392/is373-individual-record/issues/1) |
| My decision + doc change | Accepted. Marked P1 closed (2026-11-16), corrected the location line, kept direction B with C++ as the next action (§1.3–1.4). Confirmed by me 2026-11-16 | Accepted all five acceptance criteria: §2.5 schema, §2.6 provenance table and trace wording, §2.7 Q3/Q4/Q7, §2.8 checks 6–10. Still **planned**; nothing executed. Confirmed by me 2026-11-16 |

## AI use
Claude helped find candidate postings, draft concept explanations and structure this record. I verified: ✓ each posting on its original page (P2 text read in full by me 2026-11-13; P1 recheck 2026-11-16) · ✓ each technical source (2026-11-13) · the Fan Content Policy was read on 2026-11-13 with AI help (summary in §2.4); ☐ I re-read it myself. Conclusions and choices are mine; anything unchecked stays marked ☐.

**Build (Review 2):** Claude wrote the app, portfolio, tests and deploy scripts in [pb392/xenoshin-site](https://github.com/pb392/xenoshin-site) and ran the checks listed in §1.6 and §2.9. I chose Gemini and xenoshin.com, created the repo, added the API key and ran the server setup myself, and supplied the meta notes and boss list. The hosted results above are actual runs, not AI claims.
