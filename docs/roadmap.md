# Roadmap

This is not a feature list. It is the set of things that would have to be true for this to run
at a different size, in the order in which they can be found out.

## 1. Measure the trust budget

The pipeline currently holds itself to at most two open pull requests per repository, one
before a project has merged anything from it. That cap is why no maintainer has ever had to
decide on ten patches at once, and therefore why the acceptance rate cannot yet be trusted as
evidence that the model scales.

The experiment: take two projects that have already merged several fixes and whose maintainers
are responsive, raise the cap to five or six for one week, keep the proof requirement exactly
as strict, and watch for the acceptance rate, the time to a decision, the number of human
remarks, and any sign of fatigue — shorter replies, merges without comment, a batch closure.

The result is a number: the rank at which acceptance starts to fall, or the fact that it does
not fall.

## 2. Measure how much of the review is already automated

Of the pull requests that merged, what fraction had **no human review at all** before a person
pressed merge? That single percentage decides whether the maintainer is a reviewer or a rubber
stamp, and therefore whether the thesis holds or is an artefact of small numbers.

## 3. Replace the fixed cap with an earned one

If step 1 says the budget is real, the cap should come from each project's own history —
merges obtained, time to decision, remarks per patch — rather than being the same number
everywhere. Nothing here should be built before step 1 returns a result.

## 4. The wall that is legal, not social

- **Contributor licence agreements.** These do not get waived by a platform partnership. A CLA
  binds the contributor to the foundation that owns the project — Apache, the Linux Foundation,
  Elastic and so on. A code host is a host; it has no standing to excuse anyone from signing.
  The only route that works is a legal entity that signs once per foundation, on behalf of the
  work. That is the strongest argument for putting a structure around this at all.
- **Multi-tenant operation.** An ordinary commercial conversation to have, not a research
  problem.
- **Single-account reputation.** As long as everything originates from one identity, one bad
  incident on one project contaminates every other. This has to be addressed before volume
  increases, not after.

## 5. Decide what is actually being sold

Once 1 and 2 return numbers: throughput, or restraint. Throughput is pull requests per day.
Restraint is the acceptance rate, the absence of false findings, and a security channel that
routes the dangerous findings away from the public tracker instead of toward it.

The second one has already produced more value than the first, at close to zero cost. That is
the current bet, and the numbers in [thesis.md](thesis.md) are what it rests on.
