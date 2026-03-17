# KartSan

**A personal karting coach, data analyst, and performance engineer for young competitive kart racers.**

KartSan is a skill for [Claude](https://claude.ai) (Anthropic's AI assistant) that transforms it into a specialized karting coach for youth racers aged 7-14 in the Rotax MAX Challenge series. Upload your MyChron telemetry, ask a setup question, or get race-day coaching — KartSan responds with data-driven, age-appropriate advice backed by interactive dashboards.

## What it does

**Data Analysis & Visualization**
- Analyzes MyChron 5/5S/6 telemetry exports (CSV, Excel), TRAX data, and GPS traces
- Produces interactive HTML dashboards with Chart.js — hoverable charts, sortable tables, lap comparisons
- Track maps with performance overlays showing where you're fast and where to improve
- KPI cards, sector breakdowns, trend analysis, theoretical best lap calculation

**Performance Engineering**
- Chassis tuning guidance (seat position, track width, axle stiffness, caster)
- Tire pressure targets by compound and conditions (dry, damp, wet)
- Gearing recommendations based on RPM data
- Jetting and carburettor tuning within Rotax regulations
- Data-driven diagnosis: is it the driver or the kart?

**Coaching**
- Age-adapted communication: 7-9 (simple, visual), 10-12 (data-friendly), 13-14 (technical)
- Maximum 3 focus items per session — no information overload
- Every recommendation includes WHY, WHAT TO OBSERVE, and WHAT TO REPORT BACK
- Visual SVG explanations of racing concepts (racing line, braking, weight transfer)
- Pre-race pump-up messages and post-race debrief guidance

**Rotax Expertise**
- Micro MAX, Mini MAX, Junior MAX regulations and tech specs
- Sealed engine rules, weight minimums, approved tires and fuel
- Flag procedures, penalties, race start procedures
- Tech inspection checklists

**Device Knowledge**
- MyChron 5, 5 2T, 5 S, MyChron 6, 6 2T setup and configuration
- Race Studio 3 analysis workflow
- Rotax TRAX device and app
- Data export and troubleshooting

**Track Knowledge**
- Major European karting circuits (Zuera, Genk, Lonato, Sarno, Portimao, and more)
- Corner-by-corner coaching tied to telemetry data
- Can research any track worldwide

**Personalization**
- Ice-breaker on first use captures driver name, age, favorite number, idol driver, team
- Dashboards branded with driver's identity
- Idol driver referenced in motivation and analogies

**Bilingual: English & Portuguese**
- Auto-detects language from user input
- Full coaching in both languages
- Karting terminology translations included

## Quick start

### Install in Claude Desktop (Cowork mode)

1. Download `karting-advisor.skill` from [Releases](../../releases)
2. In Claude Desktop, open any Cowork session
3. Drag the `.skill` file into the chat, or use "Copy to your skills" when prompted
4. Start a new conversation and mention anything karting-related — KartSan activates automatically

### Install in Claude.ai (Chat)

Same process — upload the `.skill` file and Claude will install it.

### Install from source

If you prefer to install from the skill directory:

```bash
git clone https://github.com/YOUR_USERNAME/kartsan.git
cd kartsan
# The skill/ directory contains the full skill
# Zip it to create a .skill file:
cd skill && zip -r ../karting-advisor.skill SKILL.md references/
```

## Usage

Once installed, just talk to Claude about karting. KartSan triggers automatically when it detects karting context.

**First conversation — ice-breaker:**
KartSan introduces itself and asks for the driver's name, age, favorite number, idol driver, and kart details.

**Analyze a session:**
Upload a MyChron CSV export and ask "How was my session today?"

**Get setup advice:**
"It's cold and damp tomorrow. What tire pressures for MG Reds on a Mini Swift?"

**Learn a concept:**
"Can you explain the racing line to my 8-year-old with a drawing?"

**Check rules:**
"Is it legal to change the exhaust restrictor on Micro MAX?"

See `examples/example-prompts.md` for more.

## Repository structure

```
kartsan/
├── README.md                  # This file
├── LICENSE                    # MIT License
├── CONTRIBUTING.md            # How to contribute
├── karting-advisor.skill      # Pre-packaged skill (ready to install)
├── skill/                     # Skill source files
│   ├── SKILL.md               # Main skill definition
│   └── references/            # Domain knowledge (loaded on demand)
│       ├── rotax-regulations.md
│       ├── performance-engineering.md
│       ├── kid-communication.md
│       ├── devices-and-tools.md
│       └── track-knowledge.md
└── examples/                  # Example data and prompts
    ├── sample_telemetry.csv   # Sample MyChron export for testing
    └── example-prompts.md     # Example prompts to try
```

## How it works

KartSan is a Claude "skill" — a structured prompt with domain knowledge that Claude loads when relevant. The main `SKILL.md` file (~15KB) is always in context when the skill triggers. The five reference files (~60KB total) are loaded on demand when specific topics come up (e.g., Rotax rules are only loaded when a rules question is asked).

This means KartSan doesn't slow down simple questions but has deep knowledge available when needed.

## Limitations

- **Not a substitute for real coaching.** KartSan is a data analysis and knowledge tool. It can't watch your driving or feel the kart's handling. Always work with experienced coaches and mechanics.
- **Regulations change.** Rotax updates rules annually. The regulations reference is based on 2025-2026 rules. Check the [official Rotax Racing site](https://www.rotax-racing.com/rmc-regulations) for the latest.
- **Track data is approximate.** Track layouts are based on general knowledge and GPS data. Corner-by-corner advice should be validated with local knowledge.
- **Setup advice is general.** Every kart, driver, and track combination is unique. KartSan's recommendations are starting points — always test and measure.
- **Video analysis is limited.** KartSan can analyze telemetry data and screenshots but cannot directly play or analyze video files.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). We especially welcome:
- Updated Rotax regulations
- Track data for circuits not yet covered
- Language translations
- Real-world testing feedback

## Disclaimer

**This project is not affiliated with, endorsed by, or sponsored by any of the companies or organizations mentioned herein.** It is an independent, community-driven tool created to help young kart racers improve.

All product names, logos, brands, and trademarks mentioned in this project — including but not limited to Rotax, BRP, AIM Sportline, MyChron, Dellorto, Mojo, MG Tires, LeCont, Tony Kart, OTK, CRG, Birel ART, Parolin, Energy, Insta360, GoPro, and any others — are the property of their respective owners. Their use here is purely for informational and educational purposes.

**This is not professional coaching or engineering advice.** KartSan is an AI-powered tool that provides general guidance based on publicly available karting knowledge. Always consult qualified coaches, mechanics, and official regulations before making decisions that affect safety or competition compliance.

## License

MIT License. See [LICENSE](LICENSE).

You are free to use, modify, and distribute this project for any purpose, including commercial use, subject to the terms of the MIT License.

## Credits

Built with [Claude](https://claude.ai) by Anthropic. Created by [Sandeep Moolayil](https://github.com/smoolayil).
