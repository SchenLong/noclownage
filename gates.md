# noclownage — gate catalog

Tier order is token order: T0 mechanical (near-zero) → T1 voice → T2 truth (expensive)
→ T3 brand → IMG. Pattern lists narrow; definitions decide. A miss on a listed phrase
does not clear a disguised form of the same move, and a listed-phrase hit becomes a
finding only once it matches the definition.

**Before any gate runs, the audit selects the surface profile (config surface table
row) and the voice (`personal` | `organisation`).** Mechanical and voice gates apply
ONLY as scoped by that selection and are never cross-applied between surfaces or
voices. On any conflict between the config and a bundled voice profile, the config
wins; the profile is the default for orgs without one.

## T0 — mechanical

### T0-NEG — negation-correction family
Banned in ANY position and ANY disguise, both voices. The move: demote a framing
(usually one you invented), then substitute your own. Disguises:
- "is not X. It is Y." / "This isn't X. It's Y."
- "not because X but because Y" / "not as X but as Y"
- "X, not Y" appositions
- "no X, no Y, just Z"
- cleft substitution pairs: "What changed is…" / "What it measures is…" paired with a
  line that demotes a rival framing
- "without X it is Y" used as a correction
- "Far from X, Y" openers
- imperative recasts: "Rather than treat X as A, treat it as B"
The list is not closed: any demote-then-substitute construction is a hit.

Violations:
- "Compliance is not a checkbox. It is a capability."
- "No exam, no certificate, just an enforceable expectation."
- "We adopted it not because it is fashionable but because audits kept failing."
- "Far from a checkbox exercise, Article 4 compliance is a capability question."

Fix: delete the demoted half; state the positive claim alone. If the contrast is real
and load-bearing, name who actually holds the rival position, with a source — otherwise
it is shadow-boxing.

### T0-MIND — reader/world mind-reading & discourse framing
Claims about how the world reads/treats/debates the topic, or what the reader thinks:
"reads like", "keeps getting filed under", "there is a reading that", "the debate
around", "everyone treats", "the industry thinks", "you might think", "it is easy to
laugh at". Both voices. The piece talks about its subject, never about the audience or
an imagined consensus. "Reads to us like" is not an escape hatch in either voice: in
the personal voice it is T0-HEDGE; in the organisation voice it is a T0-MIND hit (the
org voice asserts what the system is, never how things read).

Violations:
- "AI literacy keeps getting filed under paperwork."
- "You might think this doesn't apply to your team."
- "This reads to us like the natural next step." (organisation voice)

Fix: state the fact and the analysis directly; never position against an imagined
take.

### T0-HEDGE — first-person hedging (personal voice ONLY, never cross-applied)
Singular self-referential framing of analysis: "For me", "to me", "I think",
"I believe", "I suspect", "I keep thinking about", "I keep coming back to", "I keep
arriving at", "in my view", "Personally,", "My take is", "My sense is", "reads to us
like" — and ANY equivalent, enumerated or not; the list narrows, the definition
decides. The register asserts analysis directly about the named subject; the byline
owns it. "We"/"our" is allowed only for organizational practice facts ("In our own
operations, nothing ships without a human gate."), never as a hedge. The organisation
voice's builder plural ("we asked ourselves") is compliant in its own seat and is not
a hedge.

Violations:
- "For me, I keep thinking the real gap is cultural."
- "Personally, the real gap here is cultural."
- "My take is that the exemption carries the design."

Fix: strip the hedge and assert the analysis about the subject: "The real gap is
cultural." / "The exemption carries the design."

### T0-FAKE — fake-relatable openers
Manufactured intimacy or urgency: "The conversation I keep hearing", "Someone asked
me", "I was talking to a founder last week", "Unpopular opinion", "Let that sink in".

Violations:
- "The conversation I keep hearing is about budget."
- "I was talking to a founder last week who had never heard of Article 4."
- "Unpopular opinion: your compliance program is theater."

Fix: open with the fact, date, or mechanism itself. A conversation that really happened
is a T2-ANEC question — and still rarely earns the opener.

### T0-SWEEP — sweeping quantifiers as claims
"most teams/companies/people", "everyone", "nobody does X", "every <group>" — unless
grounded to a named, listed set in the same sentence. A grounded count is compliant:
"Of the 12 vendors listed in <named source>, every vendor claims conformity." names
its set and passes.

Violations:
- "Most companies still treat this as a legal problem."
- "Nobody reads the annexes."
- "Every CISO is asking the same question this quarter."

Fix: name the actual set ("of the N vendors listed in <source>…"), or state the single
observation actually made with its provenance — or drop the sentence.

### T0-HYPE — hype lexicon
Default list: revolutionize, game-changer, unlock, leverage, cutting-edge, thrilled,
excited to announce, journey, ecosystem, paradigm, delve, elevate, supercharge. The
config adds or removes words (config wins). A listed word used in a precise technical
sense ("the audit table leverages a monotonic clock ID") is a candidate to confirm
against the definition — the gate targets hype, not vocabulary per se; when in doubt,
suggest the plainer verb.

Violations:
- "Thrilled to announce we're revolutionizing compliance."
- "This unlocks a new paradigm for security teams."

Fix: name the concrete thing and its date: "X does Y as of <date>."

### T0-BAIT — engagement bait
"What do you think?", "DM me", "follow for more", "agree?", "drop a comment",
"repost if", "link in bio".

Violations:
- "What do you think? Drop a comment below."
- "Repost if this helped your team."

Fix: delete. The value is the post; the pull is the reader's.

### T0-SURF — surface rules (config-driven, selected before the run, never cross-applied)
Hashtag count and placement, link placement, emoji policy, em/en-dash policy, thread
policy, length bounds — from the SELECTED surface row plus the Mechanical rules
section of the SELECTED voice profile. On any conflict the config surface row wins
(the profile's Length section is the default for configless orgs). Rules never leak
across surfaces or voices:
- personal surfaces: no hashtags, no body links, no CTA, no em/en dashes.
- company LinkedIn: hashtags at the bottom (three to ten) are compliant; the article
  link as the distribution close is compliant.
- company X: no hashtags; the link is allowed.
Flagging bottom hashtags on a company LinkedIn post, or the distribution link on a
company surface, is an audit error — those rules belong to the personal profile.

Violations:
- A body link or any hashtag in a `linkedin-personal` post.
- An em dash in either voice's emitted copy.
- A "1/7 🧵" thread anywhere.

Fix: mechanical — apply the selected profile's value.

### T0 quick-scan aid (optional)
If the draft is a file, a single case-insensitive grep narrows candidates fast:

```
grep -inE "is not [^.]+\. (It|This) is|isn'?t [^.]+\.|not (because|as) [^,.]+ but|no [^,.]+, no [^,.]+, just |far from (a|an|the) |rather than treat|, not [a-z][^.]{0,40}[.!]|what (changed|it (actually )?measures|matters( most)?) is|reads like|reads to us like|filed under|there is a reading|the debate around|everyone treats|the industry thinks|you might think|for me|to me,|I think|I believe|I suspect|I keep (thinking|coming back|arriving)|in my view|personally,|my take|my sense|conversation I keep hearing|someone asked me|I was talking to a|unpopular opinion|let that sink in|\b(most|every|all) (team|company|companies|people|founder|org|ciso|vendor)s?\b|everyone|nobody|no one|revolutioni|game.?chang|unlock|leverag|cutting.?edge|thrilled|excited to|journey|ecosystem|paradigm|what do you think|dm me|follow for more|agree\?|drop a comment|repost if|link in bio|(^|[[:space:]])#[[:alnum:]]+|—|–" draft.md
```

Hits are CANDIDATES, not verdicts — each is confirmed against its gate definition
before it becomes a finding (the `, not` apposition and technical-verb patterns are
deliberately over-broad), and a miss clears nothing: disguised forms still count. The
hedge terms apply to the personal voice only. A 300-word paste is faster to scan
directly.

## T1 — voice & tone (vs the loaded voice profile)

### T1-VOICE — the loaded profile, line by line
`voices/personal.md` or `voices/organisation.md` (or the config's override) is a rule
set, not a vibe. Audit the draft against every line of its Posture, Shape, Register,
Lexicon, and Length sections, with config overrides applied first. Each violated rule
is one finding, quoting the rule.

Violations:
- A personal post with headers, or seven dense paragraphs (profile: short paragraphs,
  no headers).
- An organisation post whose diagnosis contains bullets (profile: bullets only in the
  architecture section).
- Future tense for an unshipped capability in the organisation voice.

Fix: apply the quoted profile rule.

### T1-REG — register
Lecturing, teaching-the-obvious, triumphant, fearmongering, salesy — vs settled and
informative. In the personal voice, analysis is asserted directly about the named
subject (see T0-HEDGE for the hedging ban); in the organisation voice, judgments are
grounded in a failure mode.

Violations:
- "Let me explain why this matters." (lecturing)
- "The clock is ticking, and regulators will not wait." (fearmongering)
- "This is the future of compliance." (unscoped universal)

Fix: settled, informative, scoped to the subject.

### T1-APH — aphorisms and general truths (amended)
ALLOWED, and expected: direct analytical assertions SCOPED TO THE NAMED SUBJECT (a law,
an article, a mechanism, a named system), even when evaluative: "Article 5 compliance
starts as an inventory question." / "The exemption carries the design."

BANNED: general truths about the world, life, or people; morals; compressed wisdom;
advice; imperatives at the reader. Exactly one banned sentence is a FINDING reported
on an otherwise-PASS verdict (the single PASS-with-findings case — see SKILL.md
output format); more than one is a BLOCK.

Violations:
- "Paperwork can be bought. Understanding cannot."
- "Trust is earned in drops and lost in buckets."

Fix: scope the assertion to the named subject with its grounding — or delete.

### T1-PROD — product/practice mention policy (per voice, from config)
- personal voice: at most one mention, indirect, no CTA.
- organisation voice: the builder's receipts, allowed and expected, each with
  provenance (T2-INT applies to every capability shown).

Violations:
- A product named twice, or named with a CTA, in a personal post.
- An organisation post showing a capability with no SSOT trace.

Fix: apply the voice's policy; the reader's product curiosity is earned by the content,
never requested by it.

## T2 — truth (the expensive tier — only for claims that survive T0/T1)

### T2-CLASS — claim extraction (procedure)
Extract every factual claim; classify: internal (about the org/product) → T2-INT,
external (law, dates, studies, incidents) → T2-EXT/T2-LAW, opinion → T1 (scoped?).
Numbers → T2-NUM. First-person experiential → T2-ANEC.

### T2-INT — internal claims vs SSOT
Verify each internal claim against the config's SSOT paths (product catalog, release
registers). A capability claim with no SSOT trace = BLOCK. Every claim carries its
boundary: shipped vs planned, public vs internal figures.

Violations:
- "Our scanner covers the full OWASP LLM Top 10" — absent from the catalog.
- "We already support X" — where the SSOT marks X planned.

Fix: align to the SSOT wording and boundary, or cut the claim.

### T2-EXT — external claims & attribution
Every external claim needs an attribution in-text or in the piece's source block (law
article numbers count as attribution). Third-party retellings must be attributed as
retellings ("as reported in X"), never asserted as own knowledge. Historical anchors
must match the record precisely — no dramatized details the source does not contain.

Violations:
- "The AI Act requires AI literacy training" — no article number anywhere.
- "A German hospital was fined for exactly this" — no source.
- "Since February" — which year?

Fix: attach the article/source; mark retellings; correct the anchor to exactly what the
record says — or cut.

### T2-LAW — legal precision
Claims about a law's mechanics must match the provision's actual scope: which party a
duty or exemption attaches to, what the provision literally requires, what it leaves
open. Paraphrase drift on legal mechanics = BLOCK, even when the drifted version sounds
better. If the article text cannot be checked and the claim is load-bearing, it is
unverifiable = BLOCK.

Violations:
- "If you buy your AI instead of building it, Article 4 exempts you." (no such
  exemption; the duty attaches to providers AND deployers)
- Assigning a visible-label duty to the tool provider when the article splits it:
  machine-readable marking to the provider, the visible label to whoever publishes.

Fix: re-read the article; restate at the article's own precision, naming the party each
duty or exemption attaches to.

### T2-NUM — numbers provenance
Every number needs provenance. Invented or unverifiable numbers = BLOCK.

Violations:
- "73% of companies have no AI training program." (no such source)
- "Audits typically find 40+ gaps."

Fix: attach the source in-text or in the source block; if none exists, the number goes.

### T2-ANEC — anecdote detector
First-person experiential claims ("I keep hearing", "we see in engagements", "a client
told me") must trace to something real the author actually said or did, per the
config's record of what is citable. Otherwise BLOCK as fabricated.

Violations:
- "The conversation I keep hearing is…" (no such conversations exist)
- "We see this in every engagement." (also T0-SWEEP)

Fix: tell only what actually happened, at the precision the record supports — otherwise
cut.

## T3 — brand & product (config-driven)

### T3-NAME — naming canon
Exact product/company spellings per config.

Violations: "Acme Sec" where the canon is "AcmeSec"; a product in lowercase where the
canon is CamelCase.

Fix: mechanical replace per canon.

### T3-CLAIM — banned claims
The config's may-never-be-claimed list (e.g. "the only", "EU-backed", efficacy claims
without recorded evidence, unreleased-product details).

Violations: "the only EU tool that…"; "cuts incidents in half" with no recorded
evidence.

Fix: delete, or restate inside the allowed claim boundary.

### T3-PRICE — pricing policy
Per config (e.g. no public prices; pricing routes to a conversation).

Violations: a from-price in a public post under a no-public-prices policy; a price
visible in an attached screenshot (see IMG-LEAK).

Fix: remove the figure; use the config's routing ("pricing is scoped per engagement").

### T3-EDITION — edition & cross-product boundaries
OSS vs commercial feature boundaries; claims about product A made with product B's
capabilities — per the config's edition rules.

Violations: an OSS announcement claiming a commercial-only feature; crediting product
B's benchmark to product A.

Fix: align to the edition matrix in the SSOT; split the claim per product.

## IMG — image gates

Run when the post ships with any image. Read the actual file — a caption or alt-text is
not the image.

### IMG-SLOP — slop imagery
AI-generated filler and stock clichés: glossy 3D robots, glowing brains, hoodie
hackers, isometric "digital transformation" cities, handshakes, padlocks on circuit
boards, garbled AI text artifacts in the render.

Fix: a real artifact (actual screenshot, real chart, real photo) — or no image. No
image is a compliant output.

### IMG-TEXT — text inside the image obeys every text gate
Chart titles, axis labels, figures, screenshot copy, banner slogans all run T0–T3.
A chart with an unsourced number is a T2-NUM finding; a banner reading "Not a tool.
A capability." is a T0-NEG finding. Images do not launder claims.

### IMG-LEAK — sanitization
Internal hostnames/URLs, tokens, PII, customer names, internal metrics, unreleased UI,
prices where policy bans them — anywhere in the frame, including browser tabs, terminal
prompts, and notification popups. Any leak = BLOCK.

Fix: recapture from a sanitized environment; masking is a last resort.

### IMG-BRAND — visual canon
Naming canon and visual identity inside the image; never present a mockup as a shipped
screen (also T2-INT).

### IMG-FIT — the image must hand the reader something
A real chart, a real config, a real screen. Decorative feed-attention imagery (abstract
gradient cards repeating the post title) is a finding, per the config's per-surface
image policy.
