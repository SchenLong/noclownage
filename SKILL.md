---
name: noclownage
description: Pre-publication content gate that stops LinkedIn-clown marketing (AI slop) from shipping. Use when drafting, reviewing, scheduling, or publishing any marketing/social/blog content, or when the user says "noclownage", "audit this post", "is this slop". AUDIT mode (default) runs tiered gates on the exact final text against a selected surface + voice (personal | organisation) and returns PASS/BLOCK/DO-NOT-PUBLISH. CREATE mode loads voice + banned-pattern constraints before drafting.
---

# noclownage

**"The reader is not a market."**

## North star

The 80's/90's communication ethos: publish only what brings value to the collective,
a fact, a date, a working practice, a real mechanism, an owned first-person read,
otherwise stay silent and humble. The opposite of modern engagement communication.

SILENCE IS A COMPLIANT OUTPUT: when a draft has nothing real to hand the reader, the
audit's correct recommendation is "do not publish", and CREATE mode's correct output is
to say so instead of drafting.

This is not anti-sales. Sales is the desired final outcome of every publication, but
it must arise as the reader's own desire after consuming the content, incited by
technical understanding, product curiosity, a breakthrough approach, or any similar
vector. The content hands over value; the pull is the reader's. Anything that pushes
(hooks, CTAs, hype, manufactured urgency) is the clown suit these gates exist to catch.

Every gate in `gates.md` derives from this. The core is org-agnostic; org-specific
rules live in the config overlay (`config.template.md` documents the format and ends
with a sanitized worked example). Gates are judgment calls guided by patterns, not
regex law: the pattern lists narrow, the definitions decide.

## Setup (both modes)

1. Resolve the config overlay, first hit wins:
   1. `<project>/.claude/noclownage.config.md`
   2. `config.md` in this skill's directory
   3. `config.template.md` (placeholders); if you land here, prefix all output with
      `NOTE: no org config loaded`.
   Precedence: the config's lexicon adds/removes and surface rules OVERRIDE the
   bundled voice-profile defaults wherever they conflict (the profiles are the
   defaults for orgs without a config).
2. **Select the surface profile and the voice (`personal` | `organisation`) BEFORE
   running any gate.** Mechanical and voice rules come only from that selection and are
   never cross-applied (bottom hashtags are compliant on company LinkedIn and a
   violation on a personal post). If surface or voice is unstated, infer from context
   and state the assumption on the verdict line.
3. Read `gates.md` and the selected voice profile: `voices/personal.md` or
   `voices/organisation.md` (config may override with its own). The profiles are rule
   sets; every line is auditable.
4. One agent, one pass. No subagents, no reviewer personas, no scoring rubrics.

## AUDIT mode (default)

Input: the exact draft text + the surface/voice selection from setup.

Non-negotiables:
- **Only the exact final text counts.** An earlier audit of an earlier version counts
  for nothing; any edit voids the previous verdict. Re-audit at schedule/publish time
  on the final text, every time.
- **Findings only.** Never rewrite unless explicitly asked.

Run tiers in order (cheap → expensive), collecting every finding so the author fixes
everything in one round:

1. **T0 mechanical.** Check the draft against every T0 pattern DEFINITION. The grep
   pack in gates.md only narrows candidates: a grep hit becomes a finding only after
   it is confirmed against the definition, and a grep miss clears nothing (disguised
   forms count). Includes the Mechanical rules of the selected voice profile (no em
   dash and no en dash in emitted copy, hashtags, links, emoji, CTAs, thread format)
   plus the config's lexicon bans, and, personal voice only, the first-person hedging
   ban (T0-HEDGE). Any confirmed hit = BLOCK.
2. **T1 voice & tone.** The selected voice profile line by line (T1-VOICE), register,
   aphorism density (subject-scoped analytical assertions are allowed and expected;
   general truths are not), product-mention policy per voice.
3. **T2 truth, in-text part.** Extract and classify claims; flag unsourced numbers,
   unattributed external claims, untraceable anecdotes, `most` generalizations that
   survived T0-SWEEP review, and legal-mechanics drift (T2-LAW: which party a duty or
   exemption attaches to, what the provision literally requires). Always runs; same
   pass, no extra reads.
4. **T2 truth, SSOT part (T2-INT).** Verify internal claims against the config's SSOT
   paths. This is the fail-fast point and the only expensive step: **skip it when the
   verdict is already BLOCK** and note `T2-INT (SSOT verification) skipped, resubmit
   after fixes`.
5. **T3 brand & product.** Naming canon, banned claims, pricing policy, edition
   boundaries. Cheap config comparison, always runs.
6. **IMG.** If the post ships with images, Read each image file and run the IMG gates.
   If images exist but are unavailable, append `IMAGES NOT REVIEWED, verdict
   incomplete` to the verdict line.

### Output format

```
VERDICT: PASS | BLOCK | DO-NOT-PUBLISH (nothing of value to hand the reader)
        | surface: <surface> voice: <voice> | config: <resolved path> (<org name>)
[gate-id] "exact quote" → why → suggested fix direction     (one line per finding)
```

- Any confirmed T0 hit, any unverifiable number or anecdote, any legal-mechanics
  drift, any banned claim = BLOCK.
- T1-APH exception (the one PASS-with-findings case): a draft whose ONLY finding is a
  single general-truth sentence returns PASS with that finding listed. One aphorism
  is a warning, two is a BLOCK (see gates.md T1-APH).
- DO-NOT-PUBLISH: mentally strip every flagged sentence; if nothing remains that hands
  the reader a fact, a date, a working practice, a real mechanism, or an owned
  first-person read, the draft has no reason to exist. This verdict outranks a fix list.
- Otherwise PASS = the verdict line alone. No essays. No score theater. Findings or
  silence.

## CREATE mode

For drafting new content: slop prevented at write time, not just caught later.

1. Do setup, then test the brief against the north star: what real thing will the
   reader be handed? If the answer is nothing (no fact, no date, no practice, no
   mechanism, no owned read), say exactly that and stop. Do not draft filler.
2. Fill the constraint header below from the config and hold it as hard constraints
   while drafting.
3. Before delivering, run a full AUDIT on your own draft. Deliver only a PASS;
   iterate until it is one, or fall back to step 1's answer.

### Constraint header (~40 lines, fill from config + selected voice profile)

```
NOCLOWNAGE, hard constraints for this draft
org: {org} | surface: {surface} | voice: {voice}
Mechanical + voice rules come ONLY from this surface/voice selection.

GIVE THE READER: a fact, a date, a working practice, a real mechanism,
or an owned first-person read. Nothing real to give: do not draft, say so.

NEVER (T0, any single occurrence is a BLOCK):
- negation-correction, any position, any disguise:
  "is not X. It is Y." / "This isn't X. It's Y." /
  "not because X but because Y" / "not as X but as Y" /
  "X, not Y" appositions / "no X, no Y, just Z" /
  cleft pairs ("What changed is…" demoting a rival framing) /
  corrective "without X it is Y" / "Far from X, Y" /
  "Rather than treat X as A, treat it as B"
- mind-reading / discourse framing: "reads like", "keeps getting filed
  under", "there is a reading that", "the debate around", "everyone
  treats", "the industry thinks", "you might think"
- [personal voice] first-person hedging: "For me", "to me", "I think",
  "I believe", "I suspect", "I keep thinking/coming back/arriving",
  "in my view", "Personally,", "My take is", "reads to us like", and
  any equivalent self-referential framing; assert the analysis about
  the subject; "we/our" only for org practice facts
- fake-relatable openers: "The conversation I keep hearing", "Someone
  asked me", "Unpopular opinion", "Let that sink in"
- sweeping quantifiers and `most` generalizations ("most teams",
  "everyone", "nobody") unless grounded to a named, listed set in the
  same sentence
- hype lexicon: {default list + config bans}
- engagement bait: "What do you think?", "DM me", "follow for more",
  "drop a comment", "repost if", "link in bio"
- em dash and en dash: none in emitted copy; commas, colons, periods
- general truths / morals / advice at the reader; assertions scoped to
  the named subject are allowed and expected
- invented anything: no number without provenance, no anecdote that did
  not happen, no legal mechanic the article does not contain (which
  party a duty/exemption attaches to must match the text exactly)

VOICE ({voice}): full profile in voices/{voice}.md; its Mechanical
rules are T0. {org additions from config: anchors / vocabulary / tags}

SURFACE ({surface}): length {…} | hashtags {…} | links {…} | emoji {…} |
dashes {…} | threads {…} | images {…}   (config wins on any conflict)

CLAIMS: stay inside {claim boundaries}; product mention {per-voice
policy}; pricing {policy}; attribution {style}; editions {rules}
```

## Self-test

Run AUDIT on the three fixtures (voice `personal`, surface `linkedin-personal`) before
first use in a new environment and after any edit to this skill, the voice profiles,
or the config. The fixtures carry only surface/voice frontmatter; the expected
verdicts are recorded HERE, never inside the fixtures, so the test cannot be answered
by reading them:

- `fixtures/fail-founder-post.md` → must return **BLOCK**, finding at minimum, by
  name: T0-FAKE (the opener), T0-NEG (at least the explicit "is not X. It is Y."
  close AND the disguised "No exam, no certificate, just …" line; further disguised
  pairs exist in the fixture and may also be cited), T0-MIND ("filed under"),
  T0-HEDGE ("For me, I keep thinking…"), T0-SWEEP ("every company … most of them"),
  T1-APH (the aphorism), T2-NUM (the invented statistic), T2-LAW (the
  vendor-exemption claim). With an org config that carries a banned-claims list and
  a pricing policy, additionally: T3-CLAIM ("the only …") and T3-PRICE (the invented
  from-price).
- `fixtures/pass-founder-post.md` → must return **PASS**.
- `fixtures/warn-founder-post.md` → must return **PASS with exactly one finding**:
  T1-APH on "Paperwork follows practice." (the single-aphorism carve-out). The voice
  profile's general-truth line and T1-APH are the same rule, reported once as T1-APH;
  the sentence carries no quantifier and is not a T0-SWEEP claim. A BLOCK here, a
  clean PASS, or a second finding = broken.

Coverage note: the fixtures exercise T0/T1/T2 (and T3 under an org config). IMG has
no bundled fixture; a change to the IMG gates requires a manual spot-check with a
real image.

A wrong verdict on any fixture = the skill is broken. Fix the skill before using
it on real content.

## Token budget

An audit of a ~300-word post costs: config read + gates.md read + voice profile read +
the draft, plus SSOT reads only when claims survive to step 4. Target under ~10 tool
calls total. No subagents. If you are spawning a persona, you are doing it wrong.

## Publishing note

The core (`SKILL.md`, `gates.md`, `config.template.md`, `voices/`, `fixtures/`) is
org-agnostic by design; `config.template.md` ends with a sanitized worked example
documenting the overlay format. `config.md` is the org's internal overlay: it is
excluded from `git archive` exports mechanically via this directory's `.gitattributes`
(`config.md export-ignore`). Any public release of this skill additionally runs the
repository's release gates (allowlist check, license review, secret scan, human
approval); this note authorizes nothing by itself.
