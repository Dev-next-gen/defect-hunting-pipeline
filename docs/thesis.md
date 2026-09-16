# Thesis

## The bottleneck everyone expects

The obvious objection to a pipeline that opens a hundred and eighty pull requests a week is
that it does not scale, because the scarce resource is not compute. It is the attention of the
maintainer who has to read the diff. Flood them and the acceptance rate collapses, whatever the
quality.

That objection is weaker than it looks, for a reason that is visible in the threads rather than
in any theory: **maintainers have already automated the reading.** The projects worth
contributing to run review bots and continuous integration on their own code. CodeRabbit,
Copilot, qodo, greptile, plus whatever CI the project maintains itself. The first reader of an
incoming patch is usually not a person.

What happens next is the part that matters. The bot leaves a substantive remark; the pipeline
answers it with a new commit; the bot re-reads and acknowledges. The patch improves through
that exchange, and the human arrives at a fix that has already been through a round of review
they did not have to perform. Three cases from a single week are in [evidence.md](evidence.md).

## What the measurements say

Over 10–16 September 2026, of 96 pull requests still open at the end of the week, **94 were
seven days old or less** — the age of the pipeline itself. There was no backlog, because
nothing had had time to become one. And the delay before a decision was shrinking, not growing:

| cohort | n | median time to merge |
|---|---|---|
| 09-09 | 5 | 1 day |
| 09-11 | 6 | 1 day |
| 09-13 | 14 | 1 day |
| 09-15 | 13 | 0 days |
| 09-16 | 27 | 0 days |

Twenty-seven merged on the day they were opened. That is not the signature of a saturated
reviewer.

## The question that is actually open

None of this proves the model scales, because of one thing the numbers cannot see: the pipeline
holds itself to **at most two open pull requests per repository**, one before a project has
merged anything from it. No maintainer in that week was ever asked to decide on ten of our
patches at once.

So the honest formulation of the remaining risk is not about attention. It is about credit:

> Every project extends a finite amount of patience to an outside source. Past some rate, the
> acceptance rate falls for reasons that have nothing to do with whether the patches are
> correct.

If that is false, the constraint on this kind of system is legal rather than social — the
contributor licence agreements, mostly — and the engineering is the easy part. If it is true,
then what has to be bought or earned is **relationship per project**, and no amount of compute
substitutes for it.

That is a testable question and it has not been tested yet. The experiment is the first item of
the [roadmap](roadmap.md).

## What follows from being wrong about this

Two commitments hold regardless of the answer, and they are the reason the acceptance rate is
what it is.

**Volume is worthless without precision.** A pipeline that opens twice as many pull requests at
half the acceptance rate has not doubled its output. It has doubled the cost it imposes on
people who did not ask for it, and spent the only thing it cannot rebuild, which is the
willingness of maintainers to open the next one.

**Restraint is the product.** Seven refusals against eighty-three merges is the number worth
quoting, not the eighty-three. The refusals are what the proof requirement is for.
