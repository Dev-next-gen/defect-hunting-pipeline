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

## What has since been measured

On 17 September, on the last 30 merged pull requests: **16 were merged with no human
remark in the thread at all** — review bots and continuous integration only. 14 had at
least one. So in a majority of cases the maintainer is not the reviewer; they are the last
link who decides.

That settles half of the objection above and sharpens the other half. The scarce resource
is not the reading. It is the decision — and a decision rests on trust, not on attention.

## The second axis, found the hard way

The risk formulated below is about rate: past some number of patches, patience runs out. On
17 September a project produced a refusal that has nothing to do with rate and nothing to do
with correctness. The same maintainer merged three fixes and then closed the fourth as
AI-generated, after a contributor objected not to the code but to the comments. Four patches is
not a flood.

So what a project extends is not only patience per patch. It is a judgement about what is on the
other side of the pull request, and that judgement can be withdrawn at any rate, including after
a run of merges. It is also invisible in the acceptance rate, which is why these cases are
recorded one by one rather than averaged: [reception.md](reception.md).

## The question that is actually open

None of this proves the model scales, because of one thing the numbers cannot see: the pipeline
holds itself to **at most two open pull requests per repository**, one before a project has
merged anything from it. No maintainer in that week was ever asked to decide on ten of our
patches at once.

So the honest formulation of the remaining risk is not about attention. It is about credit:

> Every project extends a finite amount of patience to an outside source. Past some rate, the
> acceptance rate falls for reasons that have nothing to do with whether the patches are
> correct.

If that is false, the remaining constraints are mostly legal — the contributor licence
agreements — and the engineering is the easy part. If it is true, then what has to be bought or
earned is **relationship per project**, and no amount of compute substitutes for it.

Either way, the section above already shows that the social constraint does not wait for a high
rate to appear. So the rate hypothesis is worth testing for what it sizes, not because a negative
result would leave only paperwork in the way.

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
