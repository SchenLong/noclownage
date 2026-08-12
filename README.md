# noclownage

**"The reader is not a market."**

A pre-publication content gate for AI agents. Point it at a draft before it ships and
it tells you PASS, BLOCK, or DO-NOT-PUBLISH. No LinkedIn hooks. No "It's not X, it's Y."
No em dashes hiding a run-on sentence pretending to be an insight. No thread where a
paragraph would do.

If your agent just wrote "Unpopular opinion:" unprompted, you need this.

## The problem this solves

LLMs default to engagement-bait cadence because that is what the training data rewards.
Left alone, they will hand you a fake-relatable opener, a manufactured contrarian
"take," a made-up statistic, and a CTA begging for comments, every single time. That is
the clown suit. This skill catches it before it goes out under your name.

## What it actually checks

Six tiers, cheap to expensive, every finding collected in one pass:

- **T0 mechanical**: negation-correction rhetoric ("not X, it's Y"), mind-reading
  framing, first-person hedging, sweeping generalizations, hype lexicon, engagement
  bait, em/en dashes. Any hit is a BLOCK.
- **T1 voice**: does it sound like the org or the person it claims to, not a LinkedIn
  ghostwriter.
- **T2 truth**: unsourced numbers, unattributed claims, invented anecdotes, legal or
  factual drift from what the source actually says.
- **T3 brand**: naming canon, banned claims, pricing policy, edition boundaries.
- **IMG**: screenshots and images get read and checked too, not rubber-stamped.

The north star behind all of it: publish only what hands the reader something real, a
fact, a date, a working mechanism, an owned first-person read. Nothing real to give?
The correct output is silence, and the skill will tell you that instead of drafting
filler to fill a content calendar.

## Install

Drop the `noclownage/` directory into your agent's skill path. It works standalone with
`config.template.md` as a placeholder config, or point it at your own org overlay for
brand-specific rules (see that file for the format).

```
your-project/
  .claude/skills/noclownage/   (or wherever your runtime looks for skills)
    SKILL.md
    gates.md
    config.template.md
    voices/
    fixtures/
```

## Modes

- **AUDIT** (default): give it exact final text plus a surface and voice. It returns
  findings, never a rewrite, on the *exact* text you're about to publish. Edit one word
  after the audit and the verdict is void, run it again.
- **CREATE**: for drafting. It holds the same constraints while writing and audits its
  own output before handing it back. You never see the slop draft, only the pass.

## Self-test

Three fixtures ship in `fixtures/`, one designed to BLOCK, one to PASS clean, one to
PASS with exactly one finding (the single-aphorism carve-out). Run the skill against
all three before first use and after any edit. A wrong verdict on any of them means the
skill itself is broken, fix it before trusting it on real content. Expected verdicts
live in `SKILL.md`, not in the fixtures, so you can't cheat by reading the answer key.

## What this is not

Not a grammar checker. Not a tone softener. Not a scoring rubric with a number out of
100. One agent, one pass, findings or silence. If you're spawning reviewer personas to
run this, you're doing it wrong, see the Token budget section in `SKILL.md`.

## License

No license file yet, this is a fresh export. Treat it as source-available until one is
added.
