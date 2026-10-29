<div align="center">

# Germán Mendonça

### I don't collect technologies. I build systems for people.

`Computer Engineering` × `Business Administration` × `Communication`

[![GitHub](https://img.shields.io/badge/GitHub-Yermandonka-111111?style=flat-square&logo=github)](https://github.com/Yermandonka)
[![Email](https://img.shields.io/badge/Email-Let's_build_something-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:yermandonka@gmail.com)

</div>

---

## `01 / The person before the product`

I study **Computer Engineering and Business Administration**, but most of what I build begins somewhere else: with a person trying to learn, teach, communicate, decide or run a small business.

My job is to understand that moment and turn it into software that feels natural. Then I work backwards into architecture, data and deployment.

```text
person → friction → conversation → prototype → real use → iteration → product
```

That process has taken me from a native focus timer to a typing course built around one learner; from a chef's editable menu to a data pipeline spanning 300+ debate tournaments.

> Good software does not ask people to understand the system. It understands them first.

---

## `02 / Nine projects, nine human problems`

This is not a gallery of screenshots. It is the blueprint behind each product: **why it exists, how it grew and what moves under the interface**.

<details open>
<summary><strong>⌨️ Bichimeca — learning to type without learning to fear mistakes</strong></summary>

### The human problem

Most typing tools reward speed too early. Bichimeca was designed for a real learner using a Spanish ISO keyboard: accuracy first, immediate non-punitive feedback and short sessions that turn weak keys into deliberate practice.

### Architecture — complete flow

```text
Next.js App Router / React UI
        │
        ├── data-driven curriculum ── 34 lessons, worlds and tips
        ├── virtual ISO-ES keyboard ─ finger guidance + dead-key handling
        │
        ▼
pure TypeScript domain
        ├── typing engine ─ learning mode / test mode / error recovery
        ├── metrics ─ net WPM / accuracy / robust consistency / error rate
        ├── mastery rules ─ configurable progression thresholds
        └── progress model ─ validation / versioning / safe migrations
        │
        ▼
ProgressStore interface
        ├── localStorage ─ progress and preferences
        └── IndexedDB ─ durable local data and records

Quality gate: ESLint → TypeScript → Vitest → Playwright → production build
Delivery: static export / Vercel, no account, backend or telemetry
```

### How it was built

I began with the learning model and deterministic metrics, not the interface. The typing engine came next, followed by a versioned persistence layer, a validated curriculum and only then the themed worlds, games and HUD. Each visual iteration was checked against the same domain invariants; the engine reached full test coverage before the experience expanded.

### Human impact

The learner keeps ownership of her progress and can practise without an account or surveillance. Errors become information rather than punishment; speed becomes a consequence of confidence, not a source of anxiety.

**Built with:** `Next.js` `React` `TypeScript` `Tailwind` `Vitest` `Playwright`<br>
**Explore:** [github.com/Yermandonka/bichimeca](https://github.com/Yermandonka/bichimeca)

</details>

<details>
<summary><strong>🧭 Método Kiru — one learning loop, four different points of view</strong></summary>

### The human problem

Students need motivation, mentors need context and families need visibility without taking control away from either. Método Kiru connects those needs through goals, habits, rewards, skills and AI-assisted practice.

### Architecture — complete flow

```text
public website / registration / authentication
                         │
              role-based session router
          ┌──────────────┼───────────────┐
          ▼              ▼               ▼                ▼
       student         mentor          family           admin
   goals / habits   student plans    read-only       users / levels
   SkillCoins       assignments      progress         platform view
   rewards / stats  AI generation    overview
          └──────────────┬───────────────┘
                         ▼
             shared PHP application layer
        auth / layouts / learner context / functions
                         │
              PDO data-access boundary
                         ▼
                  MySQL / MariaDB

External learning path: mentor → Gemini → five-skill exercise → student
Deployment path: GitHub → Docker (PHP runtime) → Railway + MySQL
```

### How it was built

The first MVP established the role model and relational data on PHP/MySQL. Deployment was hardened through several Railway and Docker iterations. The product then moved outwards from the learner dashboard: responsive access, mentor workflows, family visibility, English tasks, instant correction, skill rewards and finally AI generation with a local fallback.

### Human impact

It turns progress into a shared language. Students see achievable next steps, mentors spend less time assembling repetitive material, and families can understand progress without reducing learning to a final grade.

**Built with:** `PHP 8` `MySQL` `JavaScript` `Gemini API` `Docker` `Railway`<br>
**Explore:** [github.com/Yermandonka/metodokiru](https://github.com/Yermandonka/metodokiru)

</details>

<details>
<summary><strong>📊 BP Ringaos — hundreds of tournaments turned into one personal story</strong></summary>

### The human problem

Debaters leave years of results scattered across independent tournament servers. BP Ringaos reconnects those traces and turns raw rounds, ballots and motions into an explorable record of a person's debate journey.

### Architecture — complete flow

```text
Tabbycat / CalicoTab instances
        │
        ├── discover.py / discover_new.py ─ instance discovery
        ├── brute.sh ─ parallel host checks
        └── fetch.py ─ rounds, teams, speakers, judges, motions, ballots
        ▼
versioned raw JSON per tournament
        │
        ├── patch scripts ─ incomplete adjudicator and break-category data
        └── analyze.py ─ fuzzy identity matching + cross-tournament metrics
        ▼
data/stats.json
        │
        ├── Vercel API /stats ─ protected delivery
        ├── static HTML/CSS/JS ─ profile selector + horizontal story deck
        └── /hit + Upstash Redis ─ privacy-light visit counting
        ▼
GitHub Actions daily refresh → Vercel / GitHub Pages
```

### How it was built

The project started as a scraper and instance-discovery problem. Once more than one hundred tournaments were located, the focus moved to normalization, motion-to-round correctness and fuzzy name matching. The interface was then rebuilt around people instead of tables, with mobile navigation and progressive visual QA. The automated dataset now covers **310 tournaments**.

### Human impact

It gives a community memory. Competitors can see growth that was previously buried in disconnected databases, remember partners and motions, and celebrate a trajectory rather than a single result.

**Built with:** `Python` `JavaScript` `Tabbycat APIs` `Vercel Functions` `Upstash Redis`<br>
**Explore:** [github.com/Yermandonka/bpringaos](https://github.com/Yermandonka/bpringaos)

</details>

<details>
<summary><strong>🍽️ Bon Mos — a digital restaurant that the chef can actually operate</strong></summary>

### The human problem

A small food business should not need a developer every time a dish, photo or event changes. Bon Mos gives the chef a visual storefront and a deliberately simple private control panel.

### Architecture — complete flow

```text
static multi-page storefront
home / menu / dish / services / events / contact
        │
        ├── shared client renderer (bm.js) driven by page data attributes
        ├── responsive media, search and WhatsApp reservation journey
        └── hidden password-gated management panel
                              │
                              ▼
                    Vercel serverless APIs
          /platos /plato /ajustes /foto /clave
                              │
                              ├── JSON menu + settings
                              └── optimized JPG / PNG / WebP media
                              ▼
                         Vercel Blob

No-database fallback: read-only demo catalogue seeded automatically
```

### How it was built

The first version was a Valencian-inspired showcase. It briefly used Postgres, then the architecture was simplified to static pages, serverless functions and Blob storage—fewer moving parts for the real scale of the business. Most later commits came from operational details: an unobtrusive panel, editable branding, image crop and compression, WhatsApp previews, iPhone typography, video compatibility and smooth mobile scrolling.

### Human impact

The chef can change the menu and visual identity without touching code, while customers move from discovery to a personal WhatsApp reservation with very little friction.

**Built with:** `HTML` `CSS` `JavaScript` `Vercel Functions` `Vercel Blob` `Sharp`<br>
**Explore:** [github.com/Yermandonka/bonmos](https://github.com/Yermandonka/bonmos)

</details>

<details>
<summary><strong>🎄 El Prohibido en Navidad — democracy practised around a table</strong></summary>

### The human problem

Democratic trade-offs are abstract until people must negotiate them. This cooperative role-playing game makes information, trust, participation and pluralism visible—and makes communication part of the mechanics.

### Architecture — complete flow

```text
data-driven card deck (cards.json)
       │ scenarios + compatible pairs + four decision outcomes
       ▼
browser game-state engine (vanilla JavaScript)
       ├── role assignment and four democratic-health indicators
       ├── timed speaking turns + affective/effective communication prompts
       ├── group deliberation timer + shared decision
       ├── scenario-specific effects + round summary
       └── crisis / replay state machine
       │
       ▼
single-page HTML interface + responsive CSS + local settings
       │
       ▼
static Vercel deployment + Web Analytics
```

### How it was built

It began as a static card-game prototype. The rules and content were moved into a random, compatible A/B-card system; then the interaction grew through observed table needs: clearer roles, decision effects, speaking prompts, adjustable timing, summaries, saved settings and animations that make physical group play easy to follow from one screen.

### Human impact

It creates a safe rehearsal space for disagreement. Players practise listening, explaining interests and accepting that public decisions have costs—while a serious topic remains social, theatrical and fun.

**Built with:** `HTML` `CSS` `JavaScript` `JSON` `Vercel`<br>
**Explore:** [github.com/Yermandonka/elprohibidoennavidad](https://github.com/Yermandonka/elprohibidoennavidad)

</details>

<details>
<summary><strong>📖 Brigit — a dictionary where language is decided by its speakers</strong></summary>

### The human problem

Language evolves faster than formal dictionaries. Brigit lets a community propose words and meanings, discuss their legitimacy through votes and surface the terms that people believe deserve recognition.

### Architecture — complete flow

```text
server-rendered PHP views + reusable templates
        │
        ├── forms ─ registration / login / word and meaning creation
        ├── AJAX endpoints ─ meanings, votes and deletion without reloads
        └── role-aware search, ranking and personal area
        ▼
application services (users / words / meanings / votes)
        ▼
factories + interfaces
        ├── DAO implementations ─ production persistence
        └── mock implementations ─ replaceable development boundary
        ▼
DTOs + MySQLi prepared queries
        ▼
relational MySQL model
users ↔ roles | words → meanings → votes (one vote per user/meaning)
```

### How it was built

The project moved from basic PHP pages into a layered application. Navigation and responsive templates were consolidated first; user roles, DTOs, factories and DAOs then separated domain operations from storage. Voting arrived as its own model and was progressively moved to AJAX, followed by creator-owned deletion and safer output handling.

### Human impact

It treats speakers as participants in language rather than passive consumers of it. New expressions gain context, visible support and a shared space where cultural change can be documented.

**Built with:** `PHP` `MySQL` `JavaScript/AJAX` `Bootstrap`<br>
**Explore:** [github.com/Yermandonka/brigit](https://github.com/Yermandonka/brigit)

</details>

<details>
<summary><strong>⏱️ Pomodoro de estudio — focus that lives quietly on the desktop</strong></summary>

### The human problem

Focus tools often become one more tab to lose or one more notification to ignore. This Pomodoro stays visible without taking over the desktop: one small, calm control for starting a session, seeing its rhythm and returning to work.

### Architecture — complete flow

```text
native Python process / single GTK application instance
        │
        ├── Model ─ phase machine, cycles, countdown and weekly history
        ├── GTK3 window ─ always-on-top X11 surface under GNOME Wayland
        ├── Cairo + Pango ─ custom pill, dial, panel and animation rendering
        ├── GStreamer ─ local alarm
        ├── libnotify ─ phase notifications
        └── optional Pim companion ─ desktop character linked to sessions
        │
        ▼
atomic local JSON store (0600)
settings / widget position / active phase / seven-day statistics

Desktop integration: .desktop launcher → unique instance → open/fold panel
Privacy boundary: no account, cloud, analytics or network dependency
```

### How it was built

It began as a browser extension, was first wrapped in a transparent WebKitGTK desktop host and was then rewritten as a small native GTK/Cairo application. That evolution preserved the interaction and storage format while cutting idle memory dramatically and solving Linux-specific details: XWayland stacking, accidental Ctrl+W, desktop switching, click-through behaviour and persistent positioning.

### Human impact

It makes focus tangible without making productivity performative. The timer remains present when needed, disappears when it is not, and keeps study history entirely on the user's machine.

**Built with:** `Python` `GTK3` `Cairo` `Pango` `GStreamer` `libnotify` `X11`<br>
**Explore:** [github.com/Yermandonka/_pomodoro-estudio-linux](https://github.com/Yermandonka/_pomodoro-estudio-linux)

</details>

<details>
<summary><strong>📈 Trading Sim — proving a strategy wrong before money has to</strong></summary>

### The human problem

Trading ideas are persuasive when they show profits and educational when they reveal risk. Trading Sim uses real market data but fictitious points to test quantitative strategies, costs and leverage before real capital is involved.

### Architecture — complete flow

```text
Binance public market API ── fallback: Coinbase
        │ OHLCV, liquidity universe and perpetual funding rates
        ▼
cached data layer → technical indicators
EMA / MACD / RSI / Bollinger / ROC / Donchian / ATR
        │
        ▼
weighted strategy ensemble + regime filter
        │                    └── optional Gemini entry veto (fail-open)
        ▼
simulation engine
position sizing / long-short / stop / trailing / take-profit / liquidation
        ├── principal portfolio
        ├── shadow portfolios for live comparison
        └── delta-neutral cash-and-carry simulation
        │
        ▼
JSON state + SQLite trades/equity/history
        │
        ▼
FastAPI REST layer → vanilla JS monitoring dashboard

Research path: backtests → costs → leverage model → walk-forward validation
Operations path: user systemd service / optional Raspberry Pi 24×7 deployment
```

### How it was built

The system grew from six transparent signals into a risk engine, live simulator and research environment. Each promising improvement had to survive fees, slippage, funding, liquidation and out-of-sample windows. Failed ideas were kept as conclusions rather than hidden: leverage amplified variance, most parameter sweeps did not generalize, and only a narrow family remained stable enough for continued simulation.

### Human impact

It replaces financial overconfidence with measurable evidence. The user can learn how indicators, risk sizing and market costs interact—and discover a weak strategy with fictional points instead of real savings.

**Built with:** `Python` `FastAPI` `pandas` `SQLite` `JavaScript` `Gemini` `systemd` `Raspberry Pi`<br>
**Explore:** [github.com/Yermandonka/trading-sim](https://github.com/Yermandonka/trading-sim)

</details>

<details>
<summary><strong>🧵 Fibrilandos — the first thread</strong></summary>

### The human problem

Every architecture has a first sketch. Fibrilandos explored the basic contract of the web: how a visitor moves through a visual identity, navigation and a way to make contact.

### Architecture — complete flow

```text
static entry page
   ├── shared header isolated as an iframe component
   │     └── logo + navigation
   ├── page-level CSS and image assets
   └── contact page
         ├── semantic HTML form
         └── direct phone / email actions

Delivery: static files + custom-domain CNAME
```

### How it was built

This was an early web experiment: first the page shell, then reusable navigation, branding, a separate contact journey and custom-domain configuration. Its small size is part of the story—it is the baseline from which the later component, data and deployment architectures grew.

### Human impact

Its direct impact is intentionally modest: it made a small presence reachable and gave visitors a clear contact path. Its lasting impact is personal—it marks the point where consuming the web became building for it.

**Built with:** `HTML` `CSS` `JavaScript` `GitHub Pages`<br>
**Explore:** [github.com/Yermandonka/Fibrilandos](https://github.com/Yermandonka/Fibrilandos)

</details>

---

## `03 / What connects the systems`

| Principle | How it appears in the work |
|---|---|
| **Start with behaviour** | Pedagogy before gamification; kitchen workflow before database choice; conversation rules before game animation |
| **Keep complexity proportional** | Local-first when no server is needed, serverless when operations are small, relational data when roles and history matter |
| **Make data explain something** | Typing metrics recommend practice; tournament records tell a career story; democratic indicators reveal trade-offs |
| **Design for the person operating it** | A learner owns progress, a chef edits without code, a mentor sees the next action, a student asks about the current page |
| **Iterate in the uncomfortable details** | Dead keys, fuzzy names, iPhone video, duplicate AI requests, incomplete tournament records and failed deployments |

<p align="center">
  <img src="https://skillicons.dev/icons?i=ts,js,react,nextjs,tailwind,html,css,php,python,java,c,cpp,mysql,docker,git,vercel&perline=8" alt="TypeScript, JavaScript, React, Next.js, Tailwind CSS, HTML, CSS, PHP, Python, Java, C, C++, MySQL, Docker, Git and Vercel" />
</p>

---

## `04 / The human behind the systems`

- 🎓 Double degree in **Computer Engineering + Business Administration**
- 🏆 **3rd place — UCM Hackathon 2025**
- 🎙️ British Parliamentary debate competitor, judge and tournament staff member
- 🧑‍🏫 Experience teaching students across different ages and learning needs
- 🤝 Volunteer work in education, food assistance, elder care and social initiatives
- 🌍 Portuguese — native · English — B2 · French — B1

Debate taught me to structure ideas under pressure. Teaching taught me that an explanation only works when it meets the learner where they are. Volunteering taught me to notice needs that do not arrive formatted as requirements.

Those are not activities outside software. They are how I decide what software is worth building.

---

<div align="center">

### Have a human problem worth turning into a system?

[Let's talk](mailto:yermandonka@gmail.com) · [Explore the repositories](https://github.com/Yermandonka?tab=repositories)

</div>
