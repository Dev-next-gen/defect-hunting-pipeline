# Defect Hunting pipeline

*(The search is not deterministic. The gate is.)*

It reads open-source codebases it does not own, isolates real defects, proves each one with a
reproduction that fails before the patch and passes after, and opens the fix upstream under the
rules of the project receiving it.

The finding is the work of a language model, so it is not repeatable: run it again tomorrow on
the same repository and it will not surface the same defects. What is repeatable is the gate
every candidate has to pass — a test that fails on the unpatched tree, passes on the patched
one, in the project's own environment, and that anyone can re-run to the same result. That
distinction is the whole design. Nothing downstream of it is trusted because a model said so.

It is built and operated by one person, [Leo Camus](https://github.com/Dev-next-gen), on
hardware he owns. Every figure below is measured, and every one of them can be checked against
public GitHub data by anyone who wants to.

## Seven days

10–16 September 2026, one week of continuous operation.

| | |
|---|---|
| Agent runs | **357** over 151 hours |
| Pull requests opened, proven, written up | **181** across **102** repositories |
| Merged | **83**, in **44** projects nobody here maintains |
| Closed without merging | **7** |
| Acceptance among decided pull requests | **92.2 %** |
| Cost | **$909** total, **$10.95** per merged fix |
| Runs that find nothing | **29 %** — they are included in the cost above |

Checkable: [merged](https://github.com/pulls?q=is%3Amerged+author%3ADev-next-gen) ·
[closed without merging](https://github.com/pulls?q=is%3Apr+is%3Aclosed+is%3Aunmerged+author%3ADev-next-gen).
Those searches cover the whole account, so they include work that predates the pipeline.

The hardest review it has passed is the JavaScript engine **v8/v8**: two changelists through
Gerrit, CLA and committer review, into the ECMA-262 implementation behind Chrome and Node.js.
The fix it would point to first is **[NASA F´ #5972](https://github.com/nasa/fprime/pull/5972)**,
where a framer dropped its status signal on a failed buffer allocation and stalled the downlink
chain instead of reporting the error.

## Two rules decide what is allowed to leave

1. **Nothing ships without a reproduction that fails before the patch and passes after.**
   Not a plausible argument, not a static-analysis hit, not a linter opinion. A failing test
   that turns green, run in the project's own environment.
2. **Nothing ships until the receiving project's contribution rules are satisfied.**
   Their rules beat ours, always, without asking. If a project forbids naming an AI tool, the
   disclosure line comes off. If it requires a trailer, a template section, a signed agreement
   or an accepted issue first, that comes first — or nothing goes out at all.

Every pull request says where it came from, in one sentence, in the body:

> Found by a defect-hunting pipeline I build and run
> ([Dev-next-gen](https://github.com/Dev-next-gen)), using Claude Code with Anthropic's
> Claude Opus 5.

That line is not optional, and it is not marketing. A maintainer deciding how much of their
attention to spend is entitled to know what they are reading.

And a maintainer who would rather receive none of it is entitled to that too. One line is enough,
no reason is needed, and it does not expire: [opting out](docs/opt-out.md). How projects have
actually reacted so far, the merges and the two refusals, with what was said in each case, is in
[reception](docs/reception.md).

## What comes next

An agent a maintainer can call into a discussion, instead of receiving contributions nobody
asked for: **[`@Defect-Hunting-Pipeline`](docs/agent.md)**. It has to be installed to be
called, so consent is given once, by the project. It will never ask for write access to
your repository, and it refuses to publish a vulnerability, to claim without proof, and to
take instructions from the content it reads.

## The rest

- [Journal](JOURNAL.md) — what this system becomes, dated, with the fact that prompted each
  change and what was expected of it.
- [Thesis](docs/thesis.md) — why the bottleneck everyone expects is not the one that shows
  up, and what we now measure about it.
- [Evidence](docs/evidence.md) — the cases behind the claims, with links.
- [Reception](docs/reception.md) — how projects receive this, the refusals included, with the
  quotes.
- [Opting out](docs/opt-out.md) — how a maintainer excludes a project, and what is not built
  yet.
- [Disclosure](docs/disclosure.md) — what happens when a finding should not be published.
- [Agent](docs/agent.md) — the invocable agent: what it does, what it refuses, what it will
  never ask for.
- [Roadmap](docs/roadmap.md) — what would have to be true for this to run at a different
  size.

## What this repository is not

This repository describes what the system produces, the rules it obeys, and the evidence for
its claims. It does not describe how it is built. There is no source, no architecture, no
prompts and no operational detail here, and there will not be.
