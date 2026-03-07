# 🦞🔮 Career Lobster

**Career Best Practice — For Everyone.**

> We believe every person deserves to discover their own Career Best Practice — not just those with elite networks or expensive advisors. OpenClaw makes world-class career intelligence accessible to everyone.

---

![Career Multiverse](docs/demo-multiverse.png)
*Career Multiverse — explore 15–30 parallel career timelines with success probabilities, salary trajectories, and visa pathways on an interactive Canvas.*

---

## What It Does

Career Lobster is an AI-powered career agent built for **UK job seekers** — international students on Graduate visas, professionals switching roles, and global talent looking to establish themselves in the UK market.

It starts with something no other tool offers: a **Career Multiverse Simulator** that generates 15–30 parallel career timelines based on your profile, skills, and visa status. Each timeline comes with success probabilities, salary projections, and visa pathway analysis, all rendered on an interactive HTML5 Canvas you can explore, compare, and branch.

But Career Lobster doesn't stop at simulation. Once you pick a path, it activates a **full end-to-end job pipeline**: searching real UK jobs, verifying employer sponsor licences against the official GOV.UK register, generating ATS-optimised CVs, running quality checks for legal compliance, and even automating application form submissions with screenshot evidence. Five specialised AI agents — all powered by **Z.AI GLM** — work together to take you from "I don't know what to do" to "I just applied."

---

## The Full Pipeline

| # | Agent | What It Does |
|---|-------|-------------|
| 1 | 🔮 **Career Multiverse Simulator** | Generates 15–30 parallel career timelines with success probabilities, salary trajectories, and visa pathway analysis. Results rendered on an interactive HTML5 Canvas with branching, comparison, and drill-down. |
| 2 | 🔍 **Scout Lobster** | Searches real UK job listings, cross-references employers against the GOV.UK Licensed Sponsor register (140,000+ employers), checks SOC codes against the Immigration Salary List, and validates the £38,700 salary threshold for Skilled Worker visas. |
| 3 | 📝 **Builder Lobster** | Generates UK-style 2-page CVs (no photo, no date of birth) and tailored cover letters. ATS-optimised formatting, achievement-focused bullet points, and keyword alignment with job descriptions. |
| 4 | ✅ **QC Lobster** | Catches exaggerations before they catch you. Checks Equality Act 2010 compliance, validates salary thresholds against visa requirements, ensures right-to-work consistency, and flags anything that could sink an application. |
| 5 | 📮 **Apply Lobster** | Browser automation that fills in application forms, takes screenshot evidence at each step, and pauses for your confirmation before submitting. You stay in control; the lobster does the clicking. |

---

## Key Features

- 🌐 **Visa Intelligence** — Skilled Worker, Graduate (PSW), and Global Talent visa pathway analysis baked into every recommendation
- 🎨 **Interactive Canvas Visualisation** — Explore parallel timelines on a zoomable, pannable HTML5 Canvas with real-time rendering
- 🏛️ **Sponsor Licence Verification** — Every employer checked against the official GOV.UK register of 140,000+ licensed sponsors
- 📡 **Multi-Channel** — Chat via WebChat dashboard or Telegram ([@CareerLobsterBot](https://t.me/CareerLobsterBot))
- 🤖 **Powered by Z.AI GLM** — GLM-5 for generation quality, GLM-4.7 for reasoning & orchestration, GLM-4.7-flash for speed-critical tasks
- 🌍 **Multilingual** — Automatically follows the user's input language

---

## Architecture

```
┌─────────┐     ┌──────────────────┐     ┌─────────────────────┐     ┌──────────────────┐
│  User   │────▶│  OpenClaw        │────▶│  Z.AI GLM           │────▶│  5 Lobster       │
│ WebChat │     │  Gateway         │     │  (via OpenRouter)    │     │  Agents          │
│Telegram │     │  :18789          │     │  GLM-5 / GLM-4.7    │     │                  │
└─────────┘     └──────────────────┘     └─────────────────────┘     └──────┬───────────┘
                                                                            │
                                                              ┌─────────────┼─────────────┐
                                                              ▼             ▼             ▼
                                                        ┌──────────┐ ┌──────────┐ ┌──────────┐
                                                        │  Canvas  │ │ GOV.UK   │ │ Browser  │
                                                        │  Render  │ │ Sponsor  │ │ Auto     │
                                                        │          │ │ CSV      │ │ (Apply)  │
                                                        └──────────┘ └──────────┘ └──────────┘
```

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Agent Framework | [OpenClaw](https://github.com/nicepkg/openclaw) |
| Core AI Models | Z.AI GLM-4.7, GLM-5, GLM-4.7-flash (via OpenRouter) |
| Containerisation | Docker & Docker Compose |
| Browser Automation | Playwright |
| Timeline Visualisation | HTML5 Canvas |
| Runtime | Node.js / TypeScript |
| Channels | WebChat (built-in) + Telegram Bot API |

---

## How It Works

```
1. 👋 Greeting & Profiling
   → Career Lobster collects your background, skills, visa status, and preferences

2. 🔮 Multiverse Simulation
   → Generates 15–30 parallel career timelines with probabilities and Canvas visualisation

3. 🔍 Job Search
   → Scout Lobster finds matching UK jobs, verifies sponsor licences, checks salary thresholds

4. 📝 CV & Cover Letter
   → Builder Lobster creates a UK-style 2-page CV and tailored cover letter

5. ✅ Quality Check
   → QC Lobster reviews everything for exaggerations, legal compliance, and consistency

6. 📮 Application
   → Apply Lobster automates form filling with screenshots, pausing for your approval
```

---

## Target Users

- 🎓 **UK University Students** — On Graduate visas (PSW) looking to transition to Skilled Worker sponsorship
- 💼 **Professionals Switching Jobs** — Already in the UK, wanting to explore new career directions
- 🌍 **International Talent** — Skilled workers worldwide evaluating UK career opportunities and visa pathways

---

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/) installed and running
- An [OpenRouter](https://openrouter.ai/) API key (for Z.AI GLM model access)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/smallpipi404/CareerLobster.git
cd CareerLobster/openclaw

# Set your OpenRouter API key
echo "OPENCLAW_GATEWAY_TOKEN=<your-token>" >> .env

# Start Career Lobster
docker compose up -d

# Access the WebChat dashboard
open http://localhost:18789
```

### Telegram

Chat with [@CareerLobsterBot](https://t.me/CareerLobsterBot) on Telegram — same full pipeline, mobile-friendly.

---

## Project Structure

```
openclaw/
├── workspace/
│   ├── SOUL.md          # Career Lobster personality & core instructions
│   ├── AGENTS.md        # 5-agent architecture definitions
│   ├── USER.md          # User context & preferences
│   ├── IDENTITY.md      # Agent identity configuration
│   ├── TOOLS.md         # Tool definitions & capabilities
│   └── MEMORY.md        # Conversation memory & state
├── src/
│   ├── browser/         # Playwright browser automation (Apply Lobster)
│   └── telegram/        # Telegram bot integration
├── Dockerfile           # Container build definition
├── docker-compose.yml   # Service orchestration
└── .env                 # Environment variables (API keys, tokens)
```

---

## Built For

🏆 **UK AI Hackathon — Z.AI (智谱) Bounty Track** ($4,000 prize pool)

- Core AI: Z.AI GLM models (GLM-5, GLM-4.7, GLM-4.7-flash)
- Solo developer project
- Working prototype with live demo

---

## License

MIT

---

<p align="center">
  🦞 <em>Don't job search alone. Bring a lobster.</em> 🦞
</p>
