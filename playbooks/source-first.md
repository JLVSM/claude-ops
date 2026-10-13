# Source-first — go to the origin before recording a claim

**Status:** playbook (a pattern that works), with real cases from my own sessions. Not a protocol yet; it extends Rule #0 (`no-fabrication`) and `triangulate-references` to second-hand content.

**Trigger:** I am about to record or repeat a claim I got from a thread, video, newsletter, summary or aggregator: a person's quote, a statistic, "X said/built/proved Y", a repo, a price, a licence, a capability.

## The ladder
| Division | What it is | Use |
|---|---|---|
| **1** | The origin: the paper, the repo and its LICENSE/DISCLAIMER, the official docs, the pricing page, the transcript or video of the talk, the filing, the dataset, a measurement I ran myself | Facts live here |
| **2** | Someone with access analysing the origin and linking it | A lead; confirm at 1 |
| **3** | Commentary, threads, "top 10", reposts of reposts | Never a fact; at most a signal that something exists |

**Rule:** every named author, theory, repo, number or quote gets traced to division 1 before it is written down as fact. Tag it **P** (read at the origin), **S** (two independent division-2 sources agree) or **U** (unverified: say so in the entry). A claim without a tag does not go into the record.

## How to trace, by claim type
| Claim about… | Go to |
|---|---|
| A repo (stars, licence, activity) | `gh api repos/<owner>/<name>` and its LICENSE / DISCLAIMER file, not the tweet |
| A product's price or limits | the pricing page, dated |
| A tool's behaviour or a setting | the official docs page (`<docs>/llms.txt` lists them), and the changelog for freshness |
| "<Person> said / did X" | the talk, post or paper itself; if none is found, record **U** |
| A paper's result | arXiv/DOI abstract, then the paper |
| A number | the dataset or the page it comes from; if unsourced, **U** |
| Anything that matters for a decision | run it: a measurement of my own beats any citation |

## Incentive audit (one minute, before trusting the framing)
What does the poster gain? Lead magnet ("comment X"), affiliate/referral parameters, a course, a token, follower growth. Hype words, "free", "steals", "most dangerous", no link to anything. These do not make a claim false; they tell me the framing is built for reach, so the origin is where the truth is.

## The telephone-game signal
A claim usually gets **stronger** the further it is from its origin. Real case, 2026-10-13: the REA reverse-engineering MCP. At the origin (the repo's `DISCLAIMER.md`) it says it will not help circumvent licences or copy proprietary software. Hop 1: "reverse engineered TradingView, using their premium indicators for free". Hop 2: "rebuild any feature you pay for, for free". Hop 3: "REA steals their code". Three hops, no link to the origin, each louder. The origin contradicted all three.

## Real cases (mine)
- **2026-10-13** — a post said a named developer gave 12 agents 64 papers to build a lab. No primary source exists that I could find. Recorded as **U**, and only the pattern (which stands on its own) was kept.
- **2026-10-13** — an article attributed a quote to a well-known CEO and a pattern to "OpenAI in Codex". Not repeated as fact; left **U**.
- **2026-10-08** — I told the operator an advisor model on an Opus main "would add nothing", from memory. The docs list that pairing as accepted and useful for independent review. Corrected the same day.
- **Sep–Oct 2026** — several times I stated something without reading its origin (a licence "requires a paid tier" when it is free under a revenue cap; software "installed on a host" that was not; a licence that covered only the code). Each was fixed by reading the primary source.

## Tooling
`python3 ~/Claudito/Security/scripts/trazar_fuentes.py <tweet-url>`: follows the quote chain, flags division-3 signals and incentives, checks repos / arXiv / links by machine, and leaves a checklist of what a person still has to trace. It checks only what is checkable by machine; reading the origin is still my job.

## What this does NOT mean
- Not "reject everything second-hand": a good division-2 source is a fast way to find the origin.
- Not "verify without end": trace what a decision depends on; time-box the rest and mark it **U**.
- Not a licence to skip the answer: say what is verified, what is not, and what I would check next.
