# Gate Review: Coauthor Copy Update

## recommendation

REJECT

## blockers

1. **violatedCriterion:** `SC-2 — Titles, links, venues, dates, abstracts, and layout must remain unchanged.`
   **evidencePointer:** `git diff -- index.html assets/css/style.css`; specifically `index.html:97-127` replaces each publication's prior summary block with new `<details class="abstract">` content, while `assets/css/style.css:179-277` changes title/link/abstract typography and layout. The fresh captures at `/private/tmp/junhyeokshin-text-qa/desktop.png` and `/private/tmp/junhyeokshin-text-qa/mobile-publications.png` visibly show the new title-link hierarchy and collapsible Abstract controls.

2. **violatedCriterion:** `SC-3 — No unrelated behavior may regress.`
   **evidencePointer:** `git diff -- index.html assets/css/style.css`; publication links changed from separate `[Paper]` links to linked titles, and summaries became collapsed native disclosure widgets. This changes click targets and interaction behavior beyond the requested author-copy substitution.

## originalIntent

Make only three concise author-line substitutions for the three coauthored publications:

1. `With Sangyup Choi.`
2. `With Sangyup Choi and Seung Yong Yoo.`
3. `With Sangyup Choi.`

Everything else in those publication entries must remain unchanged.

## desiredOutcome

The existing publication list should look and behave exactly as before except that each full author citation is replaced with the corresponding concise `With ...` metadata.

## userOutcomeReview

The requested strings are exact in `index.html:98`, `index.html:110`, and `index.html:122`, and they render clearly at 1280 px and 375 px. Wrapping, spacing, title hierarchy, and readability are visually sound in both captures; no clipping or horizontal overflow is visible, and all three Abstract controls are closed.

The shipped working-tree artifact does not preserve the requested surrounding content and behavior. Relative to the checked-in source, it also replaces publication summaries with different abstract prose and disclosure controls, converts title text into the DOI click target, removes the separate `[Paper]` affordances, and adds CSS that changes publication typography and spacing. Those are directly prohibited by the brief, regardless of their visual quality.

## findings

- `[product] [copy] PASS` Exact coauthor strings and punctuation appear in the requested order.
- `[product] [responsive readability] PASS` Desktop and mobile captures show readable metadata, natural wrapping, consistent spacing, and no visible overflow or clipping.
- `[product] [hierarchy] PASS` Publication numbering, linked title emphasis, secondary metadata, and Abstract controls form a clear hierarchy, considered in isolation.
- `[product] [scope/behavior] BLOCKING` The publication layout and interaction model changed beyond the copy update.
- `[product] [content preservation] BLOCKING` Publication summary/abstract content did not remain unchanged.
- `[evidence] [capture integrity] PASS` Both files are genuine 8-bit RGB PNGs with the stated dimensions and modification times later than `index.html` and `style.css`.

## remove-ai-slops and programming review

Direct pass over production diff and tests:

- No tests were added, so there are no deletion-only, removal-verification, tautological, implementation-mirroring, or excessive tests.
- The new native `<details>` implementation is not intrinsically needless abstraction, parsing, or normalization.
- The added `.paper-title`, `.citation-details`, and `.abstract` production styling is unnecessary for the narrowly requested copy-only change and creates scope drift and maintenance burden. This is blocking here because it violates `SC-2`, not merely as a style preference.
- No code-review report or manual-QA matrix was supplied. Direct source/diff inspection and direct capture inspection provide enough evidence to decide the stated criteria; missing reports are recorded as evidence gaps, not separate blockers.

## checkedArtifactPaths

- `/Users/julian/Library/CloudStorage/Dropbox/Documents/website/index.html`
- `/Users/julian/Library/CloudStorage/Dropbox/Documents/website/assets/css/style.css`
- `/private/tmp/junhyeokshin-text-qa/desktop.png`
- `/private/tmp/junhyeokshin-text-qa/mobile-publications.png`
- Git working-tree diff for `index.html` and `assets/css/style.css`
- `/Users/julian/.codex/plugins/cache/sisyphuslabs/omo/4.19.4/skills/visual-qa/SKILL.md`
- `/Users/julian/.codex/plugins/cache/sisyphuslabs/omo/4.19.4/skills/programming/SKILL.md`
- `/Users/julian/.codex/plugins/cache/sisyphuslabs/omo/4.19.4/skills/remove-ai-slops/SKILL.md`

## exactEvidenceGaps

- No task-specific changed-files manifest identifying which working-tree hunks belong solely to this copy update.
- No executor evidence report.
- No code-review report demonstrating its own programming and overfit/slop coverage.
- No manual-QA matrix artifact; only the user's browser-metrics summary and the two fresh captures were provided.
- No notepad path was provided.
- No ULW-loop plan exists, so the required fallback report location is used.

## blocking

Yes. Restore the pre-existing publication titles/link affordances, summary or abstract content, and layout/interaction, then apply only the three author metadata substitutions.
