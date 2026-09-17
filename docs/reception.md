# Reception

How projects receive this work, kept with the refusals in it. A record that only held the
merges would be an advertisement, and it would hide the most interesting result.

## The finding

Both poles validated the code. What separates them is not the patch, it is what a maintainer
accepts in the human relationship around it.

That sentence is the whole document. Everything below is the evidence for it.

## Accepted

**SirAllap, agentglass.** Two pull requests, both merged in a morning, the second closing a gap
the first had left. The maintainer did something rarer than approving: re-ran the measurements instead
of taking the table on trust, put each defect back one at a time to confirm the new guard caught
it, and checked the two limits the pull request declared about itself. Both held. Then they named
what had made it easy to accept:

> Writing down the holes in what you just handed over is rare, and it is exactly what makes the
> next person able to tell a ceiling that was chosen from one that was missed.

And, about the decision behind the patch:

> You ruled out the easy fix with numbers. [...] the difference between a decision and a
> preference.

Worth keeping, because neither sentence is about the code. Both are about whether the thing on
the other side of the pull request can be trusted to report against itself.

**samuelgursky, davinci-resolve-mcp.** Seven merges in one week, each one cut into a release the
same day: v4.6.4, v4.7.1, v4.7.2, v4.7.3, v4.7.5, v4.7.8, v4.7.9. The answer each time began the same
way, and that sameness is the point:

> Merged as-is and released as v4.7.9.

On one of them, where a fix had slipped past both an earlier contribution of ours and their own
review, they wrote: *"thank you for saying plainly that it slipped past both of us."* A project
that ships within hours is the clearest evidence that a proof arriving with the patch removes
work rather than adding it.

**0xJacky, nginx-ui.** Five pull requests proposed, five merged. The interesting one is the
fourth: the maintainer described a different design they had chosen for the same problem, said
plainly that nothing more was needed in that pull request, and invited a separate one for the two
cases that design did not cover. That follow-up was opened and merged within the hour. An invitation is
worth more than an approval, because it means the next contribution is expected rather than
tolerated.

**hartwork, libexpat.** Approved, then asked for one change: the commit author had to read
`Leo Camus <...>` rather than `leoca <...>`, to match the file headers. The commit was amended,
the tree hash shown to be identical, and the pull request merged.

**leonidaz, Ripple.** Two pull requests, both merged. On the second the maintainer did not wait
for us: they continued the work on the branch themselves, and fixed a regression a review bot
found in their own follow-up commit three minutes after it appeared. A maintainer taking over a
branch is the strongest form of acceptance there is, because it means they no longer treat the
contribution as someone else's.

## Refused

**freeCodeCamp.** Two pull requests, two closed. The project requires a triaged issue before any
pull request, and locks pull requests when it closes them, so the decision cannot even be
discussed afterwards. The repository was removed from the scan list.

**celery.** This is the instructive one, because the code was not the problem. The same
maintainer, `auvipy`, merged three pull requests on 13 and 16 September. On 17 September they
asked a contributor to review a fourth one "humanisticly". The contributor, `MehrazRumman`, answered:

> You are using AI for almost everything even for a comment ! I am not fully agree with this
> approach !

Two hours later `auvipy` closed it:

> closing as AI generated shits

Three merges, then a refusal, from the same person, without a single technical objection in
between. What changed was not the quality of the work. It was that they looked at the
conversation and found a machine on the other side of it.

The repository was removed from the scan list the same evening, and a message was posted
explaining what the pipeline is, why it exists, and that no further pull requests would come.

## What was changed because of this

- Two repositories on a manual exclusion list, each with the reason recorded next to it, so
  that "forbidden" read six months from now does not suggest the code was bad.
- A self-service way for a maintainer to opt out, so nobody has to ask twice. Described in
  [`opt-out.md`](opt-out.md), and not built yet at the time of writing.
- On a pull request where the author answers in person, no automated reply is ever posted. The
  conversation belongs to the person whose name is on it.

## What this is not

It is not a satisfaction survey. The sample is small, self-selected, and the loudest signals
come from the extremes: people who take the trouble to write at length are either pleased or
annoyed. The silent merges, which are the majority, say nothing about either.

It is also not a defence. A maintainer who does not want machine-written pull requests in their
tracker is entitled to that, and the only useful response is to leave.
