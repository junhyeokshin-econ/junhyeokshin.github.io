# Academic Website Design System

## 1. Atmosphere & Identity

The site is a quiet, editorial academic profile: warm paper-like surfaces, restrained borders, serif headings, and readable sans-serif body text. The signature is a two-column research CV layout in which paper titles carry the strongest visual emphasis and supporting citation details recede.

## 2. Color

| Role | Token | Value | Usage |
|------|-------|-------|-------|
| Text/primary | `--text` | `#2c2c2c` | Body copy and headings |
| Text/secondary | `--text-secondary` | `#5d5d5d` | Citation details and metadata |
| Text/tertiary | `--text-light` | `#767676` | Low-emphasis labels |
| Accent/primary | `--accent` | `#184d74` | Links and paper titles |
| Accent/hover | `--accent-hover` | `#0f334d` | Link hover state |
| Surface/page | `--background` | `#fcfcfa` | Page background |
| Surface/secondary | `--surface` | `#f0efe9` | Abstract disclosure panels |
| Border/default | `--border` | `#d8d4ca` | Section rules and panel borders |

## 3. Typography

| Level | Family | Size | Weight | Usage |
|-------|--------|------|--------|-------|
| Page title | Source Serif 4 | `30px` | `600` | Sidebar name |
| Section title | Source Serif 4 | `28px` | `600` | Content sections |
| Research title | Source Serif 4 | `34px` | `600` | Research section heading |
| Paper title | Source Sans 3 | `19px` | `600` | Standalone linked paper title |
| Body | Source Sans 3 | `16px` | `400` | About and supporting copy |
| Citation details | Source Sans 3 | `16px` | `400` | Authors, journal, and date |

Paper titles follow the hierarchy observed on Seungyong Yoo's academic website: accent-colored, semibold, and isolated on their own line above muted authorship and publication details.

## 4. Spacing & Layout

- Page max width: `980px`.
- Sidebar width: `250px`.
- Main column gap: `64px`.
- Section spacing: `40px`.
- The sidebar is sticky on wide screens and stacks above the content below `860px`.

## 5. Components

### Paper Listing

- **Structure**: title link, optional draft/paper link, citation details, and a native Details disclosure containing the abstract and representative figure.
- **Variants**: job-market paper and published paper.
- **Spacing**: title and metadata are grouped; the Details panel follows with visible separation, and the figure caption stays within the rendered figure width.
- **States**: default, hover, keyboard focus, and open/closed abstract disclosure.
- **Accessibility**: semantic heading and link elements; native `details`/`summary` controls for abstracts; visible keyboard focus.
- **Motion**: no decorative animation.

### Details Disclosure

- **Structure**: native `details` with a `summary` label, a bold `Abstract:` lead-in, a paragraph body, and a titled representative figure.
- **States**: closed by default and open after activation.
- **Accessibility**: keyboard-operable native disclosure control.

## 6. Motion & Interaction

There is no decorative motion. Links change to `--accent-hover` on hover, paper-title links gain an underline on hover, and native abstract disclosures provide the only content-revealing interaction.

## 7. Depth & Surface

The page uses a borders-only strategy with a subtle warm background gradient. Abstracts use the secondary surface color and an accent-colored left border to distinguish supporting material without adding cards or shadows to the main paper list.

## 8. Accessibility Constraints & Accepted Debt

### Constraints

- Preserve semantic headings and native disclosure controls.
- Keep body text at or above `16px`.
- Provide a visible keyboard focus state for paper-title links.
- Keep the paper list readable at desktop, tablet, and mobile widths.

### Accepted Debt

| Item | Location | Why accepted | Owner / Exit |
|------|----------|--------------|--------------|
| No automated component test suite | Static HTML site | The site has no runtime component layer or JavaScript behavior | Add only if the site gains interactive application behavior |
