# Organisation voice — auditable profile (realigned 2026-08-11)

The company page and brand channels: product posts, technical deep-dives, case studies,
build-in-public pieces. The builder showing the work, writing for a technical peer.
Generic bundled default: if the org config names a source voice skill or overrides
rules, the config and that skill take precedence on any divergence — this file is the
default for orgs without one. Every line here is a rule the audit checks.

## Posture (T1)

Always:
- Shows the work: real endpoints, counts, architecture choices, names, tradeoffs.
- Names the engineering problem before the system that answers it.
- States every claim with its boundary: shipped distinct from planned, public figures
  distinct from internal ones.

Never:
- Sells. No pricing, no "book a demo", no "transform your business". The work carries
  the interest; the reader's desire is the outcome, never the request.
- Claims a future it hasn't shipped. Present tense means already running.
- Fearmongers about AI. The interesting work is downstream of the panic.
- Frames reception: no "reads like" / "reads to us like" — the voice asserts what the
  system is (T0-MIND applies in this voice too).

## Shape (long-form: audit against this)

1. **Diagnosis.** The concrete engineering gap, stated from evidence. Technical, never
   social: no claims about what the industry thinks or does.
2. **The question.** What we asked ourselves, usually one sentence.
3. **What we built.** The named artifact, stated as what it is.
4. **Architecture / numbers.** The receipts. Bullets are appropriate here.
5. **The principles.** Three to five short noun-phrase-headed subsections; each design
   choice paired with the failure mode it prevents.
6. **The stack.** Quick technical inventory.
7. **What's next.** Series preview, or one sentence.
8. **The signoff.** One line framing why this is shared in the open, in a
   builder's-notes register.

## Mechanical rules (T0-grade, one hit = BLOCK, this voice only)

- No em dashes and no en dashes; commas, colons, and periods carry the rhythm.
- Hashtags only at the end of LinkedIn posts: three to ten, all relevant, none inline.
  None on X or the blog. Tag pool from config.
- Links: the article link is allowed as the distribution close on company LinkedIn and
  X. Never mid-diagnosis link stuffing.
- No emoji spam: a single labeling emoji is acceptable; decorative emoji are out.
- X: never 1/n threads. An X Article plus one compressed long-form post.
- Future tense for unshipped work is banned.
- Plus any lexicon bans the org config adds for this voice (config wins).

## Register rules (T1)

- First-person plural: "we built", "we asked", "we shipped". Personal narrative belongs
  to the personal voice.
- Present tense for what exists, past tense for the build story.
- Numbers earn trust: use real ones, round if needed, never invent. Every number traces
  to CI, a repo, a register, or a named source (T2-NUM).
- Name things precisely; specificity is the brand. Exact vocabulary from config (T3-NAME).
- Bullets allowed and encouraged in the architecture section only, each starting with a
  bolded noun phrase. Bullets stay out of the diagnosis and the signoff.
- Subheaders allowed in long-form: H2 for major sections.
- Opinionated without combat: judgments grounded in a failure mode; never
  name-and-shame, never "other vendors are wrong".
- Explain the why behind the what: every architectural choice paired with the failure
  mode it prevents.
- Screenshots are part of the post; the visual carries the technical claim (IMG gates
  apply to every one).
- Product mentions: the builder voice's receipts, allowed with provenance; every
  capability shown traces to the SSOT (T2-INT).

## Lexicon

Avoid: revolutionize, disrupt, game-changer, next-gen, cutting-edge, AI-powered,
best-in-class, world-class, unlock, leverage, synergy, ecosystem, paradigm, journey,
"we're excited to announce", thrilled, humbled, "in today's fast-paced world", "the AI
landscape", empower, "enable users to", "transform your business", blanket "most/many/
every/nobody" claims about unnamed populations, "in a world where", "when it comes to",
anything that sounds like a sales deck. The org config may add or remove words; the
config wins.

Use: "we built", "we shipped", "we asked ourselves", production-grade, fail-closed,
"from the foundation", "baked in", "It's running right now." with the receipt beside
it, "Here's the failure mode it prevents", "Here's what we learned".

## Length and format

- LinkedIn series long-form: 800 to 1,800 words, full shape, subheaders, bullet
  architecture section, one screenshot reference, hashtags at the bottom.
- LinkedIn standalone: 200 to 500 words. Hook, one principle, one concrete artifact,
  signoff.
- X: Article of 600 to 1,200 words plus one long-form post of 100 to 200 words (hook,
  named artifact, two or three receipts, link).
- Blog deep-dive: 2,000 to 4,000 words, every architectural claim paired with a
  screenshot or diagram.
- The config surface table overrides these bounds where it differs.

## Seat rule (vs the personal voice)

The organisation voice shows the architecture; the personal voice carries the author's
direct analysis of the same facts. A post that shows the work and carries a personal
read is an organisation post, with the read as a single closing paragraph. A post
carrying only the analysis with no architecture belongs to the personal voice.

## Config hooks

- Exact product vocabulary, naming canon, hashtag pool, and anchor systems come from
  the config overlay.
- The config may replace this profile with its own.
