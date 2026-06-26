# Rich HTML Report — a Cursor Agent Skill

A [Cursor](https://cursor.com) **Agent Skill** that teaches the agent to generate
rich, beautiful, single-file HTML reports and presentations in a polished house
style: a Salesforce-blue palette, an animated particle background, frosted-glass
navigation, glossy 3D buttons, deep drop-shadow cards, pill tags, and interactive
steppers.

Everything is produced as **one self-contained `.html` file** — inline CSS/JS,
CDN libraries, and base64-embedded images — so the output never has broken links
and can be emailed or hosted as-is.

![style: Salesforce blue](https://img.shields.io/badge/style-Salesforce%20blue-0176D3)
![format: single-file HTML](https://img.shields.io/badge/output-single--file%20HTML-032D60)

---

## What you get

| File | Purpose |
|------|---------|
| `rich-html-report/SKILL.md` | The skill definition: triggers, workflow, and the non-negotiable design rules. |
| `rich-html-report/template.html` | A complete copy-paste skeleton with the full `<style>` block, particle background, glass nav + mobile menu, hero, example sections, and footer. |
| `rich-html-report/components.md` | A snippet library: section bands, pills, quote boxes, card grids, the interactive stepper + slide deck, base64 logo, and an internal-use banner. |

## Design highlights

- **Color system** — a fixed Salesforce-blue token set (`#032D60` → `#57A3FD`) plus amber/green/red status colors.
- **Animated particle background** — `particles.js` over a deep blue gradient.
- **Depth** — stacked-shadow 3D buttons (lift on hover, press on click) and glossy multi-layer card shadows.
- **Glassmorphism** — frosted nav, hero stat tiles, and slides via `backdrop-filter`.
- **Responsive** — desktop/tablet/mobile breakpoints with a hamburger mobile menu.
- **Self-contained** — Inter + JetBrains Mono + Font Awesome 6 via CDN; images embedded as data URIs.

---

## Installation

Skills live in a `.cursor/skills/` directory. Copy the `rich-html-report/`
folder into either location:

| Scope | Path | Who gets it |
|-------|------|-------------|
| **Personal** | `~/.cursor/skills/rich-html-report/` | You, across all projects |
| **Project (shareable)** | `<your-repo>/.cursor/skills/rich-html-report/` | Anyone who clones that repo |

### Quick install (personal)

```bash
git clone https://github.com/<you>/rich-html-report-skill.git
mkdir -p ~/.cursor/skills
cp -R rich-html-report-skill/rich-html-report ~/.cursor/skills/
```

### Quick install (one project, shareable with your team)

```bash
git clone https://github.com/<you>/rich-html-report-skill.git
mkdir -p /path/to/your/project/.cursor/skills
cp -R rich-html-report-skill/rich-html-report /path/to/your/project/.cursor/skills/
```

Restart or reload Cursor so it picks up the new skill.

---

## How to use it

Once installed, just ask the Cursor agent for a page in this style. The agent
will pull the skill automatically when your request matches its triggers.

**Example prompts:**

- "Create a rich HTML report summarizing this analysis."
- "Build a polished single-page walkthrough/deck for X in the house style."
- "Make a landing-style HTML page for these findings."

The agent will:

1. Copy `template.html` as the starting point.
2. Swap in your title, nav, hero copy, and sections.
3. Pull components (cards, pills, steppers, quote boxes) from `components.md`.
4. Write a single self-contained `.html` file you can open in any browser.

### Adding an image / logo

To keep the file portable, embed images as base64 data URIs:

```bash
python3 -c "import base64; print('data:image/png;base64,'+base64.b64encode(open('logo.png','rb').read()).decode())"
```

Paste the result into an `<img src="...">`.

---

## Customizing the look

All visual tokens are CSS variables in the `:root` block of `template.html`.
Change the palette there once and every component follows. Keep the
`#particles-js` layer and the `particlesJS(...)` init intact to preserve the
animated background.

---

## Credits

Distilled from the "Governance Gradient" report design. Built as a reusable
Cursor Agent Skill.

## License

[MIT](LICENSE)
