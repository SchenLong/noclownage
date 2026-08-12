# noclownage — org config overlay (template)

Copy to `config.md` next to SKILL.md (or `<project>/.claude/noclownage.config.md`) and
fill in. The core skill never hardcodes org facts; everything org-specific lives here,
and where the overlay conflicts with a bundled voice profile, THE OVERLAY WINS. A
sanitized worked example follows the template.

## org
- name: `<Org>` — exact canonical spelling
- naming canon: `<Org>` (never `<0rg>`, `<Org Inc.>`); `<Product>` (never `<product>`)
- public contact: `<email>`

## voice profiles
### personal
- profile: `voices/personal.md` (bundled generic default) or `<path to your own>`
- anchor touchpoints (real org facts used to ground the analysis): `<list>`
### organisation
- profile: `voices/organisation.md` or `<path to your own>`
- exact vocabulary / naming source: `<path>`
- hashtag pool: `<tags>`

## ssot (internal fact checks — T2-INT)
- product capabilities & editions: `<repo>/<path>`
- release/shipped status: `<path>`
- publishable metrics: `<path>` — figures not listed here are not publishable
- verification rule: `<e.g. check against origin/main, never a working tree>`

## lexicon
- ban (adds to T0-HYPE, per voice): `<words>`
- allow (removes from default list): `<words>`
- dash policy: `<e.g. none in emitted copy, both voices>`

## surfaces
Rules are per-surface and never cross-applied; the audit selects one row before
running. Where a row conflicts with a bundled profile's bounds, this table wins.

| surface | voice | length | hashtags | links | emoji |
|---|---|---|---|---|---|
| linkedin-personal | personal | `<bound>` | `<n>` | `<body / first-comment / none>` | `<policy>` |
| linkedin-org | organisation | | | `<e.g. article link as distribution close>` | |
| x-post | either | | | | |
| x-article | either | | | | |
| blog | either | | | | |

- threads: `<policy>`
- images: `<policy per surface>`

## claims
- may never be claimed: `<list>` (T3-CLAIM)
- boundary rules: `<shipped vs planned wording; public vs internal figures>`
- editions: `<OSS vs commercial boundary rules>`
- product mention policy (T1-PROD): `<per voice, e.g. personal = once indirect no CTA;
  organisation = receipts with provenance>`

## pricing
- policy: `<e.g. no public prices; pricing routes to a conversation>`

## attribution
- style: `<in-text / source block; law article numbers count as attribution>`
- retellings: `<required marker, e.g. "as reported in <source>">`
- anecdotes: `<what counts as real and citable; where the record lives>`

## images
- allowed types: `<real screenshots / real charts / none …>`
- sanitization: `<what must never appear in a frame>`
- generation policy: `<AI imagery allowed? where?>`

---

# Worked example — BlackUnicorn (sanitized illustrative snapshot, 2026-08-11)

This example documents the overlay FORMAT. It is not the live overlay and is never
hand-synced: the live overlay is `config.md`, which wins on any difference.

## org
- name: BlackUnicorn — the only accepted spelling; never space-separated, never legacy
  security-suffix variants
- public contact: info@blackunicorn.tech

## voice profiles
### personal (the founder seat)
- profile: `voices/personal.md` (direct-assertion register: analysis asserted about the
  named subject, first-person hedging banned, byline owns the analysis)
- anchor touchpoints (facts, never morals): a 35-agent fleet, circuit breakers and
  approval gates, 3-tier memory, a data sanitization proxy, an 8-step provisioning
  pipeline, 3-layer LLM routing, a 5-stage quality pipeline
### organisation (the company seat)
- profile: `voices/organisation.md` (builder shows the work, receipts with provenance)
- exact vocabulary: the org's own vocabulary doc
- hashtag pool: #AI #AgenticAI #AIGovernance #BuildInPublic #LLMOps #MultiAgent
  #ProductionAI #AIInfra

## ssot
- product capabilities & editions: the org repo's `docs/product-catalog/`
- verification rule: audit against origin/main and live registries, never a working tree
- publishable metrics: only figures already recorded in the catalog

## lexicon
- ban (adds): honestly, genuinely, straightforward (personal voice); solution,
  seamless (organisation voice)
- dash policy: no em dashes and no en dashes in emitted copy, both voices

## surfaces
| surface | voice | length | hashtags | links | emoji |
|---|---|---|---|---|---|
| linkedin-personal | personal | 150 to 350 words | 0 | none in body; first comment only | none |
| linkedin-org | organisation | 200 to 500 standalone; 800 to 1,800 series | 3 to 10, bottom only | article link allowed as the distribution close | one labeling emoji max |
| x-post | either | 100 to 200 words (companion post) | 0 | allowed | none |
| x-article | either | 600 to 1,200 words | 0 | allowed | none |
| blog | either | essay 600 to 1,200 (personal); deep-dive 2,000 to 4,000 (org) | 0 | allowed | none |

- threads: never 1/n anywhere; each X beat = one Article + one long post
- images: personal = real artifacts only; org = screenshots part of the post, sanitized

## claims
- may never be claimed: "the only", "EU-backed", efficacy without recorded evidence,
  capabilities absent from the catalog, unreleased-product details
- boundary rules: shipped vs planned always explicit; internal figures never published
- editions: OSS and commercial surfaces never mixed in one claim
- product mention policy: personal = at most one, indirect, no CTA; organisation = the
  builder's receipts, each with catalog provenance

## pricing
- policy: no prices on any public surface; cost questions route to a scoping call

## attribution
- law articles cited by number; legal mechanics restated at the article's own precision
- retellings marked "as reported in <source>"
- anecdotes: only events traceable to something the author actually said or did;
  default is zero anecdotes

## images
- real artifacts only: sanitized product screenshots, charts with sourced data
- sanitization: no internal hostnames/URLs, no tokens, no customer names, no
  unreleased UI, no prices
- generation policy: no decorative AI imagery
