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

## Getting the best results

This skill shines when you give it **substance to shape** rather than asking for
a generic page. Two workflows work especially well:

### Workflow 1 — Start from an input document

The most reliable path: hand the agent a source document and let it transform
the content into a polished, structured page. Great for turning a rough capstone
doc, meeting notes, a chat transcript, a spec, or an analysis into something
presentation-ready.

**Example prompts:**

- *"Read `capstone.docx` and turn it into a rich HTML report in the house style.
  Pull out the key findings into cards and lead with an executive summary."*
- *"Take these meeting notes (`notes.md`) and build a single-page walkthrough —
  one section per topic, with a quote box for the most important decision."*
- *"Convert this transcript into a talk-track page: a stepper for the demo flow
  and pill tags for each component we touched."*

**Tips for document-first:**

- Tell the agent **what to emphasize** ("lead with the risk findings", "make the
  three options into a comparison").
- Ask it to **map content to components** — findings → `card-grid`, a sequence or
  demo → `stepper` + slides, a key statement → `quote-box`, status → pills.
- Point at the source explicitly with `@filename` so it reads the real content.

### Workflow 2 — Start from just an idea

When you only have a concept, describe the topic, audience, and the 3–5 sections
you want. The agent will scaffold the page and draft the copy.

**Example prompts:**

- *"Build a landing-style page pitching an internal observability POC. Sections:
  the problem, the hypothesis, four experiments (use a stepper), and findings."*
- *"Make a 5-minute video talk-track page for the governance gradient idea —
  hero with the headline, then one section per talking point."*
- *"Draft a one-pager explaining how CLI access to Salesforce works, with a
  comparison of connected-app vs ECA in a card grid."*

**Tips for idea-first:**

- Give it a **structure** ("hero + 4 sections + findings") so the page has rhythm.
- Specify the **audience and tone** ("internal team", "exec summary", "customer-safe").
- Iterate: generate v1, then ask for targeted changes ("make section 3 a stepper",
  "add a stats strip to the hero", "swap the featured band to gray").

### Polishing passes that work well

Once you have a draft, these follow-up asks consistently improve the result:

- *"Add a hero stats strip with the 4 headline numbers."*
- *"Turn the 'how it works' section into an interactive stepper."*
- *"Embed the company logo in the hero"* (the agent will base64-encode it so the
  file stays portable).
- *"Add an 'Internal Use Only — Not Customer-Facing' banner at the top."*
- *"Make a dark featured section to break up the white bands."*

### Output conventions

- The result is always **one self-contained `.html`** — open it directly in a
  browser, email it, or host it as-is.
- A good home for generated pages is an `output/` folder; ask the agent to write
  there (e.g., *"save it to `output/<slug>.html`"*).

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
