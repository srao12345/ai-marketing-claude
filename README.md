<p align="center">
  <img src="banner.svg" alt="AI Marketing Suite for Claude Code" width="100%">
</p>

# AI Marketing Suite for Claude Code

![AI Marketing Suite for Claude Code](banner.svg)

A comprehensive marketing analysis and automation skill system for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Audit any website's marketing, generate copy, build email sequences, create content calendars, analyse competitors, and produce client-ready PDF reports — all from your terminal.

**Built for enterprise marketers, agency builders, and solopreneurs who want AI-powered marketing intelligence.**

---

## About This Fork

This repo is forked from [zubair-trabzada/ai-marketing-claude](https://github.com/zubair-trabzada/ai-marketing-claude) — credit to the original for the base architecture.

I'm a product marketing manager specialising in agentic AI and intelligent document processing (IDP) for enterprise software. I extended the base with two original contributions designed for enterprise B2B marketing contexts:

### What I added

**`market/SKILL.md` — substantially rewritten for enterprise B2B**

The original was a general-purpose marketing audit. I rebuilt the audit orchestration for enterprise B2B contexts, specifically for companies in the AI, automation, IDP, and agentic AI space:

- **Phase 0 context loading** — the auditor reads a `context.md` file before touching the website. Every finding is calibrated to your company's positioning, buyer personas, and competitor landscape — not generic observations
- **4-persona buyer journey mapping** — evaluates the site separately through the lens of technical evaluators (CTO, IT architects), business decision-makers (COO, CFO, Business Unit Heads), procurement/risk, and C-suite sponsors
- **Competitive positioning subagent** — written from scratch, weighted at 20% for enterprise B2B where differentiation is the primary purchase driver. Benchmarks against BPM, RPA, CRM, and AI-native automation vendors
- **Revenue impact estimation** — every recommendation is tied to estimated monthly pipeline lift, not vanity metrics
- **Regulated industry lens** — specific evaluation criteria for banking, healthcare, insurance, manufacturing, and retail buyers where compliance and governance signals matter

**`context-public.md` — context system written from scratch**

A template and working example of the context file the auditor reads before analysis. Built around an enterprise IDP/agentic AI product, it covers:
- Company positioning and value proposition
- Target industries and verticals
- Buyer personas by role and decision-making lens
- Core use cases with enterprise framing
- Competitor landscape across BPM, RPA, CRM, and workflow automation
- Messaging pillars and brand voice guidelines

The context system is the key architectural idea — it's what makes this tool produce specific, actionable findings rather than generic marketing observations that could apply to any company.

---

## What This Does

Type a command in Claude Code and get instant, actionable marketing analysis:

```
> /market audit https://example.com

Launching 5 parallel agents...
✓ Content & Messaging Analysis     — Score: 72/100
✓ Conversion Optimization          — Score: 58/100
✓ SEO & Discoverability            — Score: 81/100
✓ Competitive Positioning          — Score: 64/100
✓ Brand & Trust                    — Score: 76/100
✓ Growth & Strategy                — Score: 61/100

Overall Marketing Score: 69/100

Full report saved to MARKETING-AUDIT.md
```

With a `context.md` file in your working directory, every score and recommendation is calibrated to your specific market, buyers, and competitive position.

---

## Installation

### One-command install

```bash
curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/ai-marketing-claude/main/install.sh | bash
```

### Manual install

```bash
git clone https://github.com/srao12345/ai-marketing-claude.git
cd ai-marketing-claude
./install.sh
```

### Optional: PDF report support

```bash
pip install reportlab
```

---

## Using Context Files

The most important feature of this fork is context-aware analysis. Before running any audit, create a `context.md` file in your working directory.

A template is provided in `context-public.md`. Copy and edit it for your company:

```bash
cp context-public.md context.md
# Edit context.md with your company details
```

What to include in `context.md`:
- Company overview and one-liner value proposition
- Target industries and verticals
- Buyer personas by role
- Core use cases
- Known competitors and competitive landscape
- Key differentiators
- Messaging pillars and brand voice

When `context.md` is present, the auditor loads it before touching the target website and uses it to personalise every finding. Generic observations that could apply to any company are flagged as unacceptable — findings must reference actual site content and connect to your specific commercial context.

---

## Commands

| Command | What it does |
|---|---|
| `/market audit <url>` | Full marketing audit with 5 parallel agents |
| `/market quick <url>` | 60-second marketing snapshot |
| `/market copy <url>` | Generate optimised copy with before/after examples |
| `/market emails <topic>` | Generate complete email sequences |
| `/market social <topic>` | 30-day social media content calendar |
| `/market ads <url>` | Ad creative and copy for all platforms |
| `/market funnel <url>` | Sales funnel analysis and optimisation |
| `/market competitors <url>` | Competitive intelligence report |
| `/market landing <url>` | Landing page CRO analysis |
| `/market launch <product>` | Product launch playbook |
| `/market proposal <client>` | Client proposal generator |
| `/market report <url>` | Full marketing report (Markdown) |
| `/market report-pdf <url>` | Professional marketing report (PDF) |
| `/market seo <url>` | SEO content audit |
| `/market brand <url>` | Brand voice analysis and guidelines |

---

## Architecture

```
ai-marketing-claude/
├── market/SKILL.md                     # Main orchestrator — substantially rewritten (my contribution)
│
├── skills/                             # 14 sub-skills
│   ├── market-audit/SKILL.md           # Enterprise B2B audit — rebuilt (my contribution)
│   ├── market-copy/SKILL.md            # Copywriting analysis & generation
│   ├── market-emails/SKILL.md          # Email sequence generation
│   ├── market-social/SKILL.md          # Social media content calendar
│   ├── market-ads/SKILL.md             # Ad creative & copy
│   ├── market-funnel/SKILL.md          # Funnel analysis & optimisation
│   ├── market-competitors/SKILL.md     # Competitive intelligence — written from scratch (my contribution)
│   ├── market-landing/SKILL.md         # Landing page CRO
│   ├── market-launch/SKILL.md          # Launch playbook generation
│   ├── market-proposal/SKILL.md        # Client proposal generator
│   ├── market-report/SKILL.md          # Marketing report (Markdown)
│   ├── market-report-pdf/SKILL.md      # Marketing report (PDF)
│   ├── market-seo/SKILL.md             # SEO content audit
│   └── market-brand/SKILL.md           # Brand voice analysis
│
├── agents/                             # 5 parallel subagents
│   ├── market-content.md               # Content & messaging analysis
│   ├── market-conversion.md            # CRO & funnel optimisation
│   ├── market-competitive.md           # Competitive positioning
│   ├── market-technical.md             # Technical SEO & tracking
│   └── market-strategy.md              # Brand, pricing & growth strategy
│
├── scripts/                            # Python utility scripts
│   ├── analyze_page.py                 # Webpage marketing analysis
│   ├── competitor_scanner.py           # Competitor website scanner
│   ├── social_calendar.py              # Social content calendar generator
│   └── generate_pdf_report.py          # PDF report generator
│
├── templates/                          # Marketing templates
│   ├── email-welcome.md                # Welcome email sequence (5 emails)
│   ├── email-nurture.md                # Lead nurture sequence (6 emails)
│   ├── email-launch.md                 # Product launch sequence (8 emails)
│   ├── proposal-template.md            # Client proposal template
│   ├── content-calendar.md             # 30-day content calendar
│   └── launch-checklist.md             # Launch checklist
│
├── context-public.md                   # Context template — written from scratch (my contribution)
├── install.sh                          # One-command installer
├── uninstall.sh                        # Clean uninstaller
├── requirements.txt                    # Python dependencies
└── LICENSE                             # MIT License
```

---

## Scoring Methodology

The full marketing audit scores websites across 6 dimensions. Competitive Positioning is weighted higher than the original (20% vs 15%) for enterprise B2B contexts where differentiation is the primary purchase driver:

| Category | Weight | What it measures |
|---|---|---|
| Content & Messaging | 25% | Copy quality, value props, headlines, CTAs, persona targeting |
| Conversion Optimisation | 20% | Funnels, forms, social proof, friction, enterprise conversion flow |
| SEO & Discoverability | 20% | On-page SEO, technical SEO, commercial intent coverage |
| Competitive Positioning | 20% | Differentiation, category claim, switching narratives, moat clarity |
| Brand & Trust | 8% | Design quality, trust signals, executive credibility, ecosystem health |
| Growth & Strategy | 7% | Growth model, retention signals, market timing, regulated industry readiness |

**Overall Marketing Score** = Weighted average of all categories (0–100)

---

## How It Works

1. **You type a command** — e.g., `/market audit https://example.com`
2. **Context is loaded** — if `context.md` exists, the auditor reads it and calibrates all analysis to your company
3. **Claude reads the skill files** — they tell Claude exactly how to analyse the site
4. **5 subagents launch in parallel** — each analyses a different dimension with enterprise B2B rigour
5. **Python scripts run** — automated page analysis, competitor scanning
6. **Results are compiled** — into a scored, prioritised, actionable report tied to pipeline impact
7. **Output is saved** — as a Markdown file or professional PDF

---

## Use Cases

### For enterprise product marketers

- Run `/market audit` on a competitor before a sales campaign
- Use the context system to get findings calibrated to your specific market
- Generate `/market competitors` to build battlecards before a product launch
- Deliver `/market report-pdf` as a stakeholder-ready marketing intelligence brief

### For agency builders

- Run `/market audit` on a prospect's website before a sales call
- Generate `/market proposal` with specific findings and pricing
- Deliver `/market report-pdf` as a professional client deliverable

### For solopreneurs

- Use `/market copy` to optimise your own landing pages
- Generate `/market emails` for your product launches
- Build `/market social` calendars for consistent posting

---

## What I Learned Building This

I work in product marketing for enterprise AI and automation software. The problem I kept running into with generic marketing audit tools was that they produced observations that could apply to any company — "improve your CTAs", "add social proof", "write clearer headlines."

Useful in theory. Useless in practice without knowing who the buyers are, what the competitive landscape looks like, and what actually drives enterprise purchase decisions in regulated industries.

The context system solves this. By loading company-specific positioning, buyer personas, and competitor context before touching the target website, the auditor produces findings that are specific enough to act on — referencing actual site content and connecting every recommendation to a commercial outcome.

If you work in B2B marketing for AI, automation, or IDP products — the `context-public.md` template is a good starting point. Edit it for your company and the audit findings will be immediately more useful.

---

## Uninstall

```bash
./uninstall.sh
```

Or manually:

```bash
rm -rf ~/.claude/skills/market*
rm -f ~/.claude/agents/market-*.md
```

---

## Credits

Base architecture: [zubair-trabzada/ai-marketing-claude](https://github.com/zubair-trabzada/ai-marketing-claude)

Extensions and enterprise B2B adaptations: [srao12345](https://github.com/srao12345)

---

## License

MIT License — see [LICENSE](LICENSE) for details.
