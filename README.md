# pallas-pricing-content

Single source of truth for Pallas's pricing-plan feature lists
(`pricing-content.json`), grouped by plan (`free` / `core` / `plus`) and
language (`en` / `fr`). Public so both consumers can install it as a plain
git dependency with no auth:

- `pallas` (private app repo) — `universal/app/(protected)/pricing.tsx`,
  rendered for the Monthly and Yearly plan cards (`core` + `plus`).
- `pallas-marketing-site` — `src/pages/pricing.tsx`, rendered for the Free,
  Monthly, and Yearly plan cards.

Price, plan names, taglines, and CTAs are **not** here — each repo keeps
those local since pricing itself isn't shared between the two.

To change the feature list: edit `pricing-content.json` here, commit,
push, then in each consuming repo run `npm update pallas-pricing-content`
(or `pnpm update pallas-pricing-content` in pallas-marketing-site) to pick
up the new commit — a plain `install` reuses whatever commit is already
recorded in the lockfile and won't refetch on its own.

`core` and `plus` are two separate groups (not one combined list) because
the marketing site renders them under separate headings ("Plus:" intro
line before the `plus` group) — keep that split when editing either list.
