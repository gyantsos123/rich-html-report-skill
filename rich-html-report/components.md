# Component Snippets

Drop-in markup for the house style. All classes are already defined in
`template.html`. Copy a block, paste it into a section, and edit the content.

## Section bands

Alternate these to create rhythm. Each takes a `.section-container` inside.

```html
<section class="section-light" id="...">   <!-- white -->
<section class="section-gray" id="...">    <!-- light gray -->
<section class="section-featured" id="..."><!-- dark blue, white text -->
```

Standard section opener:

```html
<div class="section-icon"><i class="fas fa-bolt"></i></div>
<h2 class="section-title">Heading</h2>
<p class="section-lede">Intro sentence.</p>
```

## Pills (status tags)

```html
<span class="pill"><i class="fas fa-tag"></i> Neutral</span>
<span class="pill pill-success"><i class="fas fa-check"></i> Pass</span>
<span class="pill pill-warn"><i class="fas fa-triangle-exclamation"></i> Caution</span>
<span class="pill pill-danger"><i class="fas fa-xmark"></i> Blocked</span>
```

## Quote / callout box

```html
<div class="quote-box">
    &ldquo;Key statement or pull quote.&rdquo;
    <span class="attribution">&mdash; Source, date</span>
</div>
```

## Card grid

```html
<div class="card-grid">
    <div class="card">
        <div class="card-title">Title</div>
        <div class="card-sub">Subtitle</div>
        <p>Body copy.</p>
    </div>
    <div class="card is-warning">
        <div class="card-title">Warning-accent card</div>
        <p>Body copy.</p>
    </div>
</div>
```

## Interactive stepper + slide deck

Pair a `.stepper` with a `.flow-deck`. Match `data-step` numbers, then call
`initStepper(stepperId, deckId, fillId)` at the bottom of the page. Best placed
inside a `.section-featured` band (the stepper is styled for dark backgrounds).

```html
<div class="stepper" id="demoStepper">
    <div class="stepper-track"></div>
    <div class="stepper-fill" id="demoFill"></div>
    <button class="stepper-btn is-active" data-step="1">
        <span class="stepper-circle"><span class="stepper-num">1</span></span>
        <span class="stepper-label">Step one</span>
    </button>
    <button class="stepper-btn" data-step="2">
        <span class="stepper-circle"><span class="stepper-num">2</span></span>
        <span class="stepper-label">Step two</span>
    </button>
    <button class="stepper-btn" data-step="3">
        <span class="stepper-circle"><span class="stepper-num">3</span></span>
        <span class="stepper-label">Step three</span>
    </button>
    <button class="stepper-btn" data-step="4">
        <span class="stepper-circle"><span class="stepper-num">4</span></span>
        <span class="stepper-label">Step four</span>
    </button>
</div>

<div class="flow-deck" id="demoDeck">
    <div class="flow-slide is-active" data-step="1">
        <div class="flow-slide-eyebrow"><i class="fas fa-play"></i> Step 1</div>
        <h3>Slide one heading</h3>
        <p>Slide content.</p>
    </div>
    <div class="flow-slide" data-step="2">
        <div class="flow-slide-eyebrow"><i class="fas fa-play"></i> Step 2</div>
        <h3>Slide two heading</h3>
        <p>Slide content.</p>
    </div>
    <div class="flow-slide" data-step="3">
        <div class="flow-slide-eyebrow"><i class="fas fa-play"></i> Step 3</div>
        <h3>Slide three heading</h3>
        <p>Slide content.</p>
    </div>
    <div class="flow-slide" data-step="4">
        <div class="flow-slide-eyebrow"><i class="fas fa-play"></i> Step 4</div>
        <h3>Slide four heading</h3>
        <p>Slide content.</p>
    </div>
</div>
```

Then near the other script calls:

```html
<script>initStepper('demoStepper', 'demoDeck', 'demoFill');</script>
```

For a 6-step stepper, just add more buttons/slides — the fill bar auto-scales.

## Brand logo in the hero (base64 embedded)

```html
<div class="hero-brand-logo">
    <img src="data:image/png;base64,PASTE_BASE64_HERE" alt="Brand">
</div>
```

Generate the data URI:

```bash
python3 -c "import base64; print('data:image/png;base64,'+base64.b64encode(open('logo.png','rb').read()).decode())"
```

## Internal-use banner (optional)

Place immediately after `<body>` to flag a non-customer-facing document:

```html
<div style="position: relative; z-index: 1000; background: #DC2626; color: #fff; font-weight: 700; text-align: center; padding: 12px 16px; text-transform: uppercase; letter-spacing: 0.5px;">
    Internal Use Only &mdash; Not Customer-Facing
</div>
```

## Icon reference

Icons are Font Awesome 6 Free (`fas`). Common picks: `fa-bolt`, `fa-shield-halved`,
`fa-layer-group`, `fa-diagram-project`, `fa-table`, `fa-bullseye`, `fa-comments`,
`fa-check`, `fa-triangle-exclamation`, `fa-lock`, `fa-eye`, `fa-gauge-high`.
