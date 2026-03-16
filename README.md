# Business Model Canvas — Claude Code Skill

A Claude Code skill that generates professional, interactive **Business Model Canvas (BMC)** visualizations as self-contained HTML files. Supports existing companies, new business ideas, and 20+ languages.

---

## What It Does

Creates an interactive 16:9 HTML canvas with all 9 BMC building blocks, click-to-expand modals, brand colors, and responsive design — ready to open in any browser.

**Triggers automatically when you say:**
- "Create a business model canvas for Airbnb"
- "How does Netflix make money?"
- "Help me develop a BMC for my SaaS idea"
- "Analiza el modelo de negocio de Mercado Libre"

---

## Three Modes

| Mode | When to use | Example |
|------|-------------|---------|
| **Research** | Existing company | "BMC for Spotify" |
| **Ideation** | New business idea | "Help me build a BMC for my food delivery startup" |
| **Manual** | You already have the data | "Here are my 9 blocks, build the canvas" |

---

## Features

- **9 Building Blocks** — Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partners, Cost Structure
- **Interactive modals** — click any block for detailed explanations
- **Brand colors** — auto-applies known brand palettes (e.g., Duolingo green, Netflix red)
- **20+ languages** — auto-detects conversation language; uses official translations from *Business Model Generation* (Osterwalder)
- **Responsive design** — desktop → tablet → mobile
- **Research-backed** — cites SEC filings, investor reports, and primary sources when in Research Mode

---

## Installation

1. Download `business-model-canvas.zip`
2. In Claude Code, run:
   ```
   /install-skill business-model-canvas.zip
   ```
3. That's it — the skill activates automatically on trigger phrases.

---

## Output Example

```
airbnb_bmc_2024.html     ← Research Mode
my_startup_bmc_concept.html  ← Ideation Mode
acme_corp_bmc.html       ← Manual Mode
```

Open the generated `.html` file in any browser to interact with the canvas.

---

## Skill Structure

```
business-model-canvas/
├── SKILL.md                    # Skill instructions for Claude
├── assets/
│   └── bmc-template.html       # Base HTML template with placeholders
└── references/
    ├── bmc-framework.md        # Definitions and examples for all 9 blocks
    └── bmc-translations.md     # Official block translations in 20+ languages
```

---

## Languages Supported

English, Spanish, Portuguese, French, German, Italian, Dutch, Polish, Swedish, Danish, Russian, Chinese, Japanese, Korean, Hindi, Arabic, Turkish, Vietnamese, Thai, Indonesian — and more.

---

## Author

Made by **Roger** · [DestruCreación](https://destrucreacion.com)

---

## License

MIT — free to use, modify, and share.
