# AI Skills Library

> A curated collection of AI agent skills covering visual engineering, code explanation, product research, skill discovery, marketing, design, and more. Built to compound — every skill makes the system smarter.

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-22c55e?logo=github)](https://marktantongco.github.io/ai-skills-library/)
[![Skills](https://img.shields.io/badge/New_Skills-4-6366f1?logo=robot)]()
[![Sources](https://img.shields.io/badge/Research_Sources-7-eab308)]()
[![License](https://img.shields.io/badge/License-CC--BY--SA_4.0-ec4899)]()

---

## Overview

This repository is the result of a comprehensive research effort into the AI agent skills ecosystem. It includes:

- **4 newly created skills** adapted from community research
- **Evaluation of 7+ external sources** (skills.sh, Anthropic Academy, GitHub, etc.)
- **40+ existing skills** documented in the system
- **Security-first methodology** for skill vetting and installation
- **MECE discipline** — one owner skill per type of work, zero overlap

### New Skills Added

| Skill | Category | Description | Source |
|-------|----------|-------------|--------|
| [Photography AI](skills/photography-ai/SKILL.md) | Creative | Professional visual engineering framework for AI image/video generation | [marktantongco/aiskills-photog](https://marktantongco.github.io/aiskills-photog/) |
| [Explained Code](skills/explained-code/SKILL.md) | Education | Beginner-friendly code explanation using analogies, diagrams, and walkthroughs | Anthropic official example |
| [JTBD Research](skills/jtbd-research/SKILL.md) | Strategy | Jobs to be Done product research methodology with segmentation, job mapping, and interview guides | [snowtema/ajtbd-skills](https://github.com/snowtema/ajtbd-skills) |
| [Skill Finder](skills/skill-finder/SKILL.md) | Meta | Discovery, evaluation, security vetting, and installation of AI agent skills | [skills.sh](https://skills.sh), [agentskills.io](https://agentskills.io) |

---

## Quick Start

### For AI Agents

1. Copy any skill's `SKILL.md` into your agent's skills directory
2. Each skill follows the 4-section format:
   - **Context**: When to use this skill
   - **Instructions**: Step-by-step workflow
   - **Constraints**: Hard rules (what the skill must never do)
   - **Examples**: Ideal output samples

### For Developers

```bash
# Clone this repository
git clone https://github.com/marktantongco/ai-skills-library.git

# Browse skills
ls skills/

# Read any skill
cat skills/photography-ai/SKILL.md
```

---

## Skill Directory

### `skills/photography-ai/`
Professional visual engineering skills framework covering 6 core categories:

1. **Technical Prompt Engineering** — Scaffold method, front-loading, photographic vocabulary
2. **Photographic Literacy** — Lighting patterns, lens selection, aperture control, anamorphic mastery
3. **Strategic Negation** — Skin realism, anatomical correction, temporal consistency
4. **Identity Preservation** — Seed locking, reference tools, multi-reference consistency
5. **Post-Processing** — Iterative refinement, inpainting, external enhancement, quality checklist
6. **Agent Orchestration** — Multi-agent systems, role-based teams, auditable workflows

### `skills/explained-code/`
5-step methodology for explaining code to beginners:

1. **Start with an Analogy** — Real-world comparison before any code
2. **Draw a Diagram** — ASCII art or Mermaid diagrams
3. **Walk Through** — Step-by-step, 5-15 lines per section
4. **The Gotcha** — Common pitfall that trips beginners
5. **Your Turn** — Practice challenge to reinforce learning

### `skills/jtbd-research/`
8-step Jobs to be Done product research methodology:

1. **Define Research Scope** — Product/domain, target market, research goal
2. **Segment the Market** — JTBD segmentation with TAM/SAM/SOM
3. **Build the Job Map** — Full hierarchy: functional, emotional, social
4. **Identify Risky Assumptions** — Top-5 with desirability/viability/feasibility analysis
5. **Conduct Customer Interviews** — Structured interview guide (adapted from The Mom Test)
6. **Synthesize JTBD Statements** — Push/pull/anxiety/habit force analysis
7. **Generate Landing Page Copy** — Customer-language copy from research
8. **Plan Respondent Recruitment** — Ongoing recruitment channel strategy

### `skills/skill-finder/`
7-step discovery and installation meta-skill:

1. **Check Existing Skills** — Prevent duplication before searching
2. **Search External Sources** — skills.sh, GitHub, Anthropic Academy, agentskills.io
3. **Evaluate Candidates** — 50-point scorecard (relevance, quality, compatibility, security, maintainability)
4. **Security Vet** — 10 red-flag checks (automatic rejection on any)
5. **Install the Skill** — Adapt to SKILL.md format, log installation
6. **Verify Installation** — Checklist for correctness
7. **Schedule Audits** — Monthly recurring audit cycle

---

## Research Sources

This library was built by researching and evaluating these sources:

| Source | URL | Type | Compatibility |
|--------|-----|------|---------------|
| **skills.sh** | [skills.sh](https://skills.sh) | Marketplace | Open Standard (40+ agents) |
| **Anthropic Academy** | [anthropic.skilljar.com](https://anthropic.skilljar.com/claude-code-skills) | Official Courses | Claude-specific |
| **Agent Skills Standard** | [agentskills.io](https://agentskills.io) | Open Spec | Universal |
| **Claude Skills Library** | [GitHub](https://github.com/aiaiohhh/claude-skills-library) | Collection (36 skills) | Claude-specific |
| **AJTBD Skills** | [GitHub](https://github.com/snowtema/ajtbd-skills) | Product Research | Claude-specific (methodology universal) |
| **GSAP Animation Skill** | [GitHub](https://github.com/xerxes-on/gsap-animation-skill) | Animation Reference | Universal |
| **Photography AI Skills** | [GitHub Pages](https://marktantongco.github.io/aiskills-photog/) | Visual Engineering | Universal |

### Key Findings from Research

1. **Most Claude skills are Claude-specific** — they use the SKILL.md format native to Claude Code. However, the **methodology is almost always portable**.

2. **The Agent Skills open standard** (agentskills.io) was created by Anthropic and released December 2025. Skills following this standard work across **40+ AI platforms**.

3. **The "secret hack" is real** — pasting `https://anthropic.skilljar.com/claude-code-skills` into Claude allows it to read the course and extract skill recommendations. All courses are free with certificates.

4. **"Marketing Skills Library by Cory Haynes"** could not be verified. The actual creator of the most prominent marketing skills library is **tyr0nin / AiAiOHHH** (36 skills, not 32).

5. **Deep Research** is a built-in Claude Code subagent feature — equivalent to the Task tool with subagent types in other agent systems.

---

## Existing Skills in System

These skills were already installed in the environment before this research:

| Skill | Category | Description |
|-------|----------|-------------|
| GSAP Animations | Dev | Animation engineering for React (ScrollTrigger, timelines, micro-interactions) |
| UI/UX Pro Max | Creative | Design intelligence across frameworks |
| Marketing Mode | Strategy | 23 marketing disciplines |
| Fullstack Dev | Dev | Next.js 16, TypeScript, Tailwind CSS 4, shadcn/ui, Prisma |
| Coding Agent | Dev | Plan-before-code, verify-everything discipline |
| Visual Design Foundations | Creative | Typography, color, spacing, iconography, accessibility |
| Content Strategy | Strategy | Content marketing playbook |
| Charts & Visualization | Data | matplotlib, seaborn, ECharts, D3.js, Mermaid, flowcharts |
| Image Generation | Creative | AI image generation via z-ai-web-dev-sdk |
| Web Reader | Data | Page content extraction |
| Web Search | Data | Web search capabilities |
| Finance | Data | Financial data analysis |
| Blog Writer | Creative | Blog content creation |
| SEO Content Writer | Strategy | SEO-optimized content |
| Interview Designer | Strategy | Interview guide creation |
| Podcast Generate | Creative | Podcast episode generation |
| Storyboard Manager | Creative | Story and storyboard management |
| Market Research Reports | Strategy | Market analysis and visual reports |
| Coding Agent | Dev | Structured coding workflow with verification |
| Skill Creator | Meta | Create, test, and improve skills |
| Skill Assessor | Meta | Evaluate skill quality and performance |

---

## Operating Principle

> **Build systems, not one-off tasks. Every skill added makes the system smarter. Every cron scheduled removes one more thing to think about.**

### The Rule

1. **Prototype first** — Do it manually with 3-10 real examples
2. **Get approval** — Show output, ask "Does this look right?"
3. **Codify** — Write SKILL.md with context, instructions, constraints, examples
4. **Schedule** — If it repeats, put it on a cron
5. **Monitor** — Check first 3 automated runs, iterate

### MECE Discipline

- **One type of work** per skill
- **One owner skill** per capability
- **Zero overlap** between skills
- **Zero gaps** in coverage

---

## Deployment

| Platform | URL | Status |
|----------|-----|--------|
| **GitHub Pages** | [marktantongco.github.io/ai-skills-library](https://marktantongco.github.io/ai-skills-library) | Live |
| **Vercel** | [ai-skills-library-three.vercel.app](https://ai-skills-library-three.vercel.app) | Live |
| **GitHub Repo** | [github.com/marktantongco/ai-skills-library](https://github.com/marktantongco/ai-skills-library) | Live |

---

## License

This project is licensed under **CC-BY-SA 4.0** — share, adapt, and contribute improvements back to the community.

---

## Contributing

1. Fork this repository
2. Create a new skill following the SKILL.md format
3. Run it through the Skill Finder evaluation scorecard (minimum 30/50)
4. Submit a pull request with a description of what the skill does

---

*Built with the principle: your job is not to answer — your job is to make yourself unnecessary, one skill at a time.*
