
## SpicyMiso Photo Portfolio

## Submission Links

**GitHub Repository:**  
https://github.com/kriswojcik-dev/SpicyMisoPhoto

**Published Design System Specimen:**  
https://kriswojcik-dev.github.io/SpicyMisoPhoto/


## Design System Documentation

### Project Context and Audience

SpicyMisoPhoto is a street photography portfolio designed to
showcase urban environments, architecture, and everyday moments.

The intended audience includes photography enthusiasts,
potential clients, and creative collaborators. The design
uses an earthy, editorial aesthetic with forest-green tones
to complement the photography without distracting from it.

### Reset Strategy

The stylesheet uses a selective CSS reset instead of
removing all browser defaults.

Global `border-box` sizing makes element dimensions
more predictable by including padding and borders.

The default body margin is removed to allow intentional
spacing through the design system.

Media elements use `max-width: 100%` to prevent overflow,
and form controls inherit typography for consistency.

Native control appearances are preserved, and visible
keyboard-focus indicators support accessibility.

### Design Tokens

CSS custom properties are defined in `:root` and organized
into six categories:

- Color: Brand colors and semantic interface colors.
- Spacing: A consistent 4px-based spacing scale.
- Sizing: Maximum container widths, an 80ch reading
  measure, and minimum component dimensions.
- Radius: Consistent corner treatments for components.
- Elevation: Subtle shadows for distinguishing surfaces.
- Typography: Font families, sizes, weights, and line heights.

Brand tokens define the visual palette, while semantic
tokens describe how colors function within components.

Using semantic properties allows components to share
styles across different themes.

### Typography

The display font is Cormorant Garamond, used for headings
and editorial titles. The body font is Inter, used for
paragraphs, buttons, labels, and controls.

Both fonts are loaded through Google Fonts and use the
SIL Open Font License 1.1.

Cormorant Garamond uses weights 400, 500, 600, and 700,
plus italic 400. Inter uses weights 400, 500, 600, and 700.

Fallback stacks are Georgia, serif for headings and
Arial, sans-serif for body text.

Responsive headings use `clamp()` to adjust font sizes
between mobile and desktop layouts. Longer text uses
an 80ch reading measure for consistent line lengths.

### Theme System

The default theme uses warm cream backgrounds, forest-green
headings, and charcoal body text.

The alternate Dark Forest theme uses deep green backgrounds,
cream typography, and pale sage accents.

The alternate theme is scoped using `.theme-dark`, which
overrides semantic custom properties without duplicating
component rules.

Both themes reuse the same cards, buttons, and controls.

### Accessibility and Usage Guidance

The design system prioritizes readable contrast, keyboard
focus visibility, responsive layouts, and semantic HTML.

Controls use associated labels, and radio options are
grouped with a fieldset and legend.

CSS Grid and flexible layouts allow content to adapt
to different viewport widths.

The preferred fonts include fallback stacks in case
Google Fonts cannot load.

Photography placeholders are used during development
because the specimen tests the design system rather
than presenting a finished portfolio.

The specimen does not require JavaScript, working
navigation between pages, or functional form submission.


## Testing and Evidence

### Test 1 — Responsive Layout

**Condition:** Chrome DevTools at 320px, 768px, and
1280px viewport widths.

**Expected:** Content adapts to each viewport without
horizontal scrolling, clipping, or overlapping.

**Observed:**
- 320px: Tables, typography, photography cards, forms,
  and Dark Forest components fit correctly. Cards stack
  vertically.
- 768px: Photography cards display side by side
  without horizontal scrolling.
- 1280px: Content remains centered, properly spaced,
  and free of horizontal overflow.

**Revision:** None required.

### Test 2 — Browser Zoom

**Condition:** Chrome at 200% browser zoom.

**Expected:** Text remains readable, controls remain
accessible, and layouts adapt without overlapping.

**Observed:** The page remained readable and properly
formatted without reported overflow or overlapping.

**Revision:** None required.

### Test 3 — Keyboard Navigation

**Condition:** Keyboard-only navigation using Tab,
Space, and arrow keys.

**Expected:** Interactive elements are accessible
without a mouse and display visible focus indicators.

**Observed:**
- S4 links and buttons displayed visible focus outlines.
- Disabled buttons were skipped.
- S6 text inputs, select controls, checkboxes, radio
  buttons, and buttons responded correctly.
- Dark Forest controls were keyboard accessible
  with visible focus indicators.

**Revision:** None required.

### Test 4 — Color Contrast

**Condition:** Color combinations evaluated using
WebAIM Contrast Checker.

**Expected:** Normal text achieves at least 4.5:1
contrast. Essential control boundaries and focus
indicators target at least 3:1 contrast.

| Combination | Ratio | Result |
|---|---|---|
| Default body text | 12.8:1 | Pass |
| Default primary button | 11.83:1 | Pass |
| Dark Forest body text | 13.23:1 | Pass |
| Dark Forest primary button | 10.79:1 | Pass |
| Dark Forest focus indicator | 10.08:1 | Pass |
| Default focus indicator | 5.21:1 | Pass |
| Original default control border | 1.84:1 | Below target |
| Revised default control border | 5.21:1 | Pass |
| Dark Forest control border | 10.79:1 | Pass |

**Observed:** Essential text and primary button
combinations exceeded contrast requirements. The
original Sage control border fell below the 3:1 target.

**Revision:** A dedicated `--color-control-border`
token was added. The default theme uses Moss Green,
and the Dark Forest theme uses Pale Sage.

### Test 5 — Font Fallback

**Condition:** Google Fonts URL blocked through
Chrome DevTools, followed by a page refresh.

**Expected:** Cormorant Garamond falls back to Georgia,
and Inter falls back to Arial without compromising
readability.

**Observed:** Typography visibly changed, but the
page remained readable.

**Revision:** None required. Font loading was restored
after testing.

### Test 6 — HTML and CSS Validation

**Condition:** HTML checked using Nu HTML Checker
and CSS checked using W3C CSS Validation Service.

**Expected:** No validation errors caused by the code.

**Observed:** Both HTML and CSS passed validation.

**Revision:** None required.

### Test 7 — Publication

**Condition:** Published GitHub Pages website opened
in a Chrome Incognito window.

**Expected:** CSS, fonts, media placeholders, links,
and interactive controls load correctly without
requiring a signed-in account.

**Observed:** The published website displayed and
functioned correctly in the private browser window.

**Revision:** None required.


## Code Defense

### Reset Strategy

I chose a selective CSS reset because it creates consistency
without removing useful browser defaults. Global border-box
sizing makes layouts more predictable, while removing the
default body margin allows me to control page spacing.

I also preserved native form controls and keyboard-focus
indicators to support accessibility.

### Token Hierarchy

I organized my CSS custom properties into brand and
semantic tokens within `:root`.

Brand tokens define the forest-green color palette,
while semantic tokens determine how colors are applied
to backgrounds, text, borders, and interactive elements.

I also created reusable tokens for spacing, sizing,
border radius, elevation, and typography. This approach
helps maintain consistency and makes future changes easier.

### Scoped Theme Override

I used `.theme-dark` to create the Dark Forest theme.
This selector overrides semantic color tokens while
reusing the same component classes.

For example, photography cards use `--color-surface`
in both themes, but the variable resolves to a
different color depending on the theme container.

This prevents unnecessary duplication of component rules.

### Evidence-Based Revision

During contrast testing, I discovered that the original
Sage border color (#A8B9A0) only achieved a 1.84:1
contrast ratio against the Warm Cream background.

Because this fell below the 3:1 target for essential
control boundaries, I introduced a dedicated
`--color-control-border` semantic token.

I changed the default control border to Moss Green,
which achieved 5.21:1 contrast. I also added a
Dark Forest override using Pale Sage, which achieved
10.79:1 contrast against the dark control background.

This allowed me to improve accessibility without
changing the overall visual identity.


## AI Disclosure

I used ChatGPT as a development assistant while creating
the SpicyMisoPhoto design-system specimen.

AI assistance included explaining CSS concepts, identify
accessibility considerations, and organize the README
documentation and testing records.

I reviewed and implemented the code, selected the project
context and visual direction, and adjusted design decisions
based on my preferences.

I verified the resulting work through responsive testing
at 320px, 768px, and 1280px, browser zoom testing,
keyboard navigation, WebAIM contrast checks, font fallback
testing, HTML/CSS validation, and publication testing.

I also made an evidence-based revision to the control-border
colors after identifying insufficient contrast.

AI-generated suggestions were evaluated through these
tests rather than accepted as automatically correct.
