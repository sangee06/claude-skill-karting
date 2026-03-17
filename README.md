# KartSan — Claude Skill for Kart Racing

> **A Claude AI skill that turns Claude into a personal karting coach, data analyst, and performance engineer for young competitive kart racers.**

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0wIDE4Yy00LjQxIDAtOC0zLjU5LTgtOHMzLjU5LTggOC04IDggMy41OSA4IDgtMy41OSA4LTggOHoiLz48L3N2Zz4=)](https://claude.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Bilingual](https://img.shields.io/badge/Languages-EN%20%7C%20PT-blue.svg)](#bilingual-english--portuguese)

---

**KartSan** is a **skill for [Claude](https://claude.ai)** (Anthropic's AI assistant). Install it in **Claude Desktop (Cowork)** or **Claude.ai Chat** and Claude becomes a specialized karting coach for youth racers aged 7-14 in the Rotax MAX Challenge series.

Upload your MyChron telemetry, ask a setup question, or get race-day coaching — KartSan responds with data-driven, age-appropriate advice backed by interactive dashboards.

**What is a Claude skill?** A skill is a structured knowledge pack that gives Claude specialized capabilities in a specific domain. Once installed, Claude automatically activates the skill when it detects relevant context in your conversation. [Learn more about Claude skills](https://docs.claude.com).

---

## Key features

| Capability | Details |
|---|---|
| **Telemetry analysis** | MyChron 5/5S/6 CSV/Excel, Rotax TRAX, GPS traces — full data pipeline with sector analysis, trends, RPM, temps |
| **Interactive dashboards** | Chart.js HTML dashboards with hoverable charts, track maps, KPI cards, lap comparisons, sortable tables |
| **Performance engineering** | Chassis tuning, tire pressures, gearing, jetting, carb tuning — all within Rotax regulations |
| **Visual explanations** | SVG diagrams of racing concepts (racing line, braking, weight transfer) — animated, interactive, age-appropriate |
| **Rotax regulations** | Micro MAX, Mini MAX, Junior MAX rules, tech specs, weight minimums, tech inspection checklists |
| **Track knowledge** | European circuits (Zuera, Genk, Lonato, Sarno, Portimao...) + worldwide research, corner-by-corner coaching |
| **Device expertise** | MyChron 5, 5 2T, 5 S, MyChron 6, 6 2T, Race Studio 3, Rotax TRAX — setup, config, troubleshooting |
| **Age-adapted coaching** | 7-9 (visual, simple), 10-12 (data-friendly), 13-14 (technical) — max 3 focus items, always starts with positives |
| **Bilingual** | English and Portuguese (auto-detects), karting terminology translations included |
| **Personalized** | Ice-breaker captures name, age, fav number, idol driver, team — used in dashboards and coaching |
| **Why-Observe-Report** | Every recommendation explains WHY, WHAT TO WATCH FOR, and WHAT TO REPORT BACK |

---

## Quick start

### Option 1: Download and install (easiest)

1. Download **[karting-advisor.skill](../../releases)** from Releases
2. Open **Claude Desktop (Cowork)** or **Claude.ai Chat**
3. Drag the `.skill` file into the conversation
4. Talk about karting — KartSan activates automatically

### Option 2: Install from source

```bash
git clone https://github.com/smoolayil/claude-skill-karting.git
cd claude-skill-karting
cd skill && zip -r ../karting-advisor.skill SKILL.md references/
```

Then drag the generated `.skill` file into Claude.

---

## Usage examples

Once installed, just talk to Claude about karting. Here are some things you can try:

| What you say | What KartSan does |
|---|---|
| *"How was my session today?"* + CSV upload | Full telemetry analysis + interactive dashboard + coaching advice |
| *"What tire pressures for rain on MG Reds?"* | Specific numbers + WHY + what to observe + what to report back |
| *"Explain the racing line to my 8-year-old"* | Interactive HTML with SVG diagrams, age-appropriate language |
| *"Is it legal to change the exhaust restrictor?"* | Cites specific Rotax regulation, suggests legal alternatives |
| *"How do I set up my new MyChron 6?"* | Step-by-step configuration for your class and engine |
| *"We're racing at Zuera this weekend"* | Track-specific setup, gearing, corner-by-corner strategy |
| *"Aqui está a minha telemetria do treino"* | Responds in Portuguese, full analysis |
| *"I'm nervous about the final race"* | Pre-race focus plan + motivational message |

See [`examples/example-prompts.md`](examples/example-prompts.md) for more, and try with the included [`sample_telemetry.csv`](examples/sample_telemetry.csv).

---

## Repository structure

```
claude-skill-karting/
├── README.md                  # This file
├── LICENSE                    # MIT License
├── CONTRIBUTING.md            # How to contribute
├── karting-advisor.skill      # Pre-packaged skill (ready to install)
├── skill/                     # Skill source files
│   ├── SKILL.md               # Main skill definition (~15KB)
│   └── references/            # Domain knowledge, loaded on demand (~60KB)
│       ├── rotax-regulations.md
│       ├── performance-engineering.md
│       ├── kid-communication.md
│       ├── devices-and-tools.md
│       └── track-knowledge.md
└── examples/                  # Try it yourself
    ├── sample_telemetry.csv   # Sample MyChron export
    └── example-prompts.md     # Example prompts to copy-paste
```

## How it works

KartSan is a Claude "skill" — a structured prompt with domain knowledge that Claude loads when relevant. The main `SKILL.md` (~15KB) is always loaded when the skill triggers. The five reference files (~60KB total) are loaded on demand — Rotax rules only when a rules question comes up, device help only when you ask about MyChron, etc.

This means KartSan doesn't slow down simple questions but has deep knowledge available when needed.

---

## Who is this for?

- **Young kart racers (7-14)** who want to understand their data and improve
- **Karting parents** who want data-driven coaching tools without hiring a full-time engineer
- **Karting coaches** who want a quick analysis tool for session debriefs
- **Anyone in Rotax MAX Challenge** (Micro, Mini, Junior) who uses MyChron or TRAX
- **Portuguese-speaking karting families** who want coaching in their language

---

## Limitations

- **Not a substitute for real coaching.** KartSan is a data analysis and knowledge tool. Always work with experienced coaches and mechanics.
- **Regulations change.** Based on 2025-2026 Rotax rules. Check the [official Rotax Racing site](https://www.rotax-racing.com/rmc-regulations) for the latest.
- **Track data is approximate.** Validate corner-by-corner advice with local knowledge.
- **Setup advice is general.** Every kart/driver/track combination is unique. Recommendations are starting points.
- **Video analysis is limited.** Can analyze telemetry and screenshots, but cannot play video files directly.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). We especially welcome:

- Updated Rotax regulations (they change yearly)
- Track data for circuits not yet covered
- New language translations
- Real-world testing feedback from the track

---

## Disclaimer

**This project is not affiliated with, endorsed by, or sponsored by any of the companies or organizations mentioned herein.** It is an independent, community-driven tool created to help young kart racers improve.

All product names, logos, brands, and trademarks mentioned in this project — including but not limited to Rotax, BRP, AIM Sportline, MyChron, Dellorto, Mojo, MG Tires, LeCont, Tony Kart, OTK, CRG, Birel ART, Parolin, Energy, Insta360, GoPro, and any others — are the property of their respective owners. Their use here is purely for informational and educational purposes.

**This is not professional coaching or engineering advice.** KartSan is an AI-powered tool that provides general guidance based on publicly available karting knowledge. Always consult qualified coaches, mechanics, and official regulations before making decisions that affect safety or competition compliance.

---

## License

MIT License. See [LICENSE](LICENSE).

You are free to use, modify, and distribute this project for any purpose, including commercial use, subject to the terms of the MIT License.

## Credits

Built with [Claude](https://claude.ai) by Anthropic. Created by [Sandeep Moolayil](https://github.com/smoolayil).

---

## Setup for GitHub discoverability

After creating the repo, do these things to maximize search visibility:

### 1. Repository description (Settings > General)

Set the "About" description to:

> Claude AI skill — personal karting coach for young Rotax racers. Telemetry analysis, MyChron dashboards, setup advice, Rotax regulations. Ages 7-14. EN/PT.

### 2. Topics (Settings > General > Topics)

Add all of these:

`claude-skill` `claude-ai` `anthropic` `claude` `cowork` `karting` `kart-racing` `rotax` `rotax-max` `mychron` `telemetry` `data-analysis` `coaching` `youth-sports` `motorsport` `ai-coaching` `ai-skill` `race-engineering` `karting-data`

### 3. Social preview image

Upload a social preview image (Settings > General > Social preview) so the repo looks good when shared on social media or in chat links. Recommended: 1280x640px, showing KartSan branding + a dashboard screenshot.

### 4. Create a Release

Go to Releases > Create new release:
- Tag: `v1.0.0`
- Title: `KartSan v1.0.0 — Claude Skill for Kart Racing`
- Description: Copy the "Key features" table from this README
- Attach: `karting-advisor.skill` file

Releases make the `.skill` file downloadable with one click and show up in GitHub search.

### 5. Enable Discussions (optional)

Settings > Features > Discussions. This lets the karting community ask questions, share track data, and request features without cluttering Issues.
