# Journal

What this system becomes, dated. Each entry says what changed, the fact that prompted it,
and what was expected of the change — so we can come back later and say whether it worked.

This journal does not describe how the system is built. It describes what it does, what it
refuses to do, and what was learned doing it.

---

## 2026-09-18

**A correction to this journal's own accuracy pass.** Earlier today this entry recorded that a
quote attributed to a maintainer, *“Seven releases from your pipeline this week, each with a test
that fails on the old code”*, could not be found and had therefore been written by us. That
verification was wrong. The quote is verbatim from `samuelgursky` on `davinci-resolve-mcp` #246,
and the reason the search missed it is that it read only the first 260 characters of each comment
while the sentence sits at the end. The quote is restored in
[`reception.md`](docs/reception.md).

What the full read then showed is better than the single quote. The maintainer keeps his own
count, in the last line of every message: *four releases from your pipeline today* on #240, *Six
releases from your pipeline in two days now* on #242, *Seven* on #246, *Eight* on #247, and
*Nine releases from your pipeline this week* on #248, merged and released tonight as v4.7.10. On
that last one he merged `main` into the branch in a scratch worktree, ran the full suite, then
brute-forced the arithmetic both ways for every frame in two hours at 29.97 and 59.94, 648,000
conversions, before agreeing with the patch.

The lesson is one this project already wrote down and then broke: **two readings before calling
something a defect.** A truncated read is not a read, and “not found” from an incomplete search
is not a finding. Removing a true quote to look rigorous is worse than the error it was meant to
fix.


**An invitation is now enough to start the work.** Until today, a maintainer who described
something worth fixing got nothing out of it unless a person read the thread and pressed a
button. That happened twice on 17 September and both contributions were merged within the
hour, `0xJacky/nginx-ui` #1933 and `SirAllap/agentglass` #597, faster than anything ever sent
unasked. So the button is gone: on a project that has already merged something from here,
someone with write access who describes work to be taken has it taken, and the pull request
that follows quotes the request that caused it. The terms are in the
[README](README.md#when-a-maintainer-asks-for-something).

**The quote has to be verbatim, and that guard is the one worth keeping.** What a request is
understood to be is only accepted if the words it claims to rest on can be found, unchanged,
in what the person actually wrote. Otherwise nothing starts. Without that, a reformulation
would end up in a public pull request putting words in a maintainer's mouth, and the
usefulness of the fix would not repair it.

**Two failures found by testing it against real threads instead of invented ones**, and both
were mine. The first was ordinary: a line that recorded what had been started could raise on
a missing record and take the whole refresh down with it. The second mattered more. On the
very thread the feature was built for, it fired on the maintainer's *first* message, the one
asking for a change inside the pull request under review. That work already belonged to the
answer in that thread, so the mechanism would have duplicated it. The fix draws the line
explicitly: a request about the pull request in front of you stays there, and only a request
that reaches outside it can start something new. Rerun against the same thread, it then picked
the right message, which was the one that actually produced #1933.


**The refusals are now published, with the quotes.** Until today this repository held only the
merges, which made it an advertisement. [`docs/reception.md`](docs/reception.md) puts both poles
on the same page: the maintainers who re-ran the measurements themselves and asked for more, and
the two projects that closed the door. It exists because of one result that is more interesting
than either pole taken alone. In both camps the code was validated. What separates them is what
a maintainer accepts in the human relationship around the patch, not the patch.

The clearest case is a project where the same maintainer merged three contributions on 13 and 16
September and then closed a fourth on 17 September with *"closing as AI generated shits"*, after
another contributor objected that *"You are using AI for almost everything even for a comment"*.
Three merges, then a refusal, from the same person, without one technical objection in between.
Nothing about the work had changed. They had looked at the conversation and found a machine on
the other side of it. That is a finding about this pipeline, so it is written down rather than
left out.

**An opt-out, promised publicly twice, is now specified.**
[`docs/opt-out.md`](docs/opt-out.md) says how a maintainer will be able to exclude a project in
one line, either on any thread of mine or in a file the project already controls, with no reason
required and no reply expected. It also says plainly that the mechanism is not built yet and that
today the list is still maintained by hand, because a promise on a page nobody can act on is
worth less than an admission.

**What prompted the page is a failure, and it is recorded in it.** On 17 September I wrote
publicly to a project that it would receive nothing further, and seven minutes later the program
answered a review on one of its pull requests. The exclusion had been decided and written down;
the running program had never been made to read it. The decision and the enforcement were two
separate events and only one had happened.

So the commitment is not that an exclusion exists. It is that it takes effect when it is
recorded, not at the next restart, and that it is checked at all three points where the program
can reach a project: before scanning it, before opening a contribution on it, and before writing
a word on one of its threads. Three checks, because one is exactly where this kind of promise
breaks. What we expect of it: that the next time a maintainer asks us to leave, the gap between
the sentence and the behaviour is zero, and that nobody has to ask twice.

**A thread where the author answers in person no longer gets an automated reply.** Not a
politeness rule, a consequence of the above. When a message is signed by a person, the
conversation belongs to that person, and the only thing the program may still do there is act on
a request to change code.

---

## 2026-09-17

**Something finally measured: the human reviewer's place.** Of the last 30 merged pull
requests, **16 were merged without a single human writing a word in the thread** — review
bots and CI only. 14 had at least one human remark. That is the number
[`docs/thesis.md`](docs/thesis.md) left open, and it settles half of it: in most cases the
maintainer is not the reviewer, he is the last link who decides. Which moves the question
from *his attention* to *his trust*.

**A red CI is almost never our fault, and now that is measured.** The ten pull requests
GitHub listed as needing action were reviewed one by one: four were stale in that list
(checks green, or a remark already addressed), three were noise from a tool the project
runs itself, three were waiting on an administrative gesture — a label, a licence
agreement. **None of them needed a code change.**

**New rule: "flaky" is a conclusion, not a fallback.** An argument showing that a patch
cannot touch a failing test is an argument, not a proof. From now on, before writing that
a failure is unrelated, we check whether the same test fails elsewhere, and we try to
re-run it unchanged or reproduce it — and **we say so when we could do neither**.

Applied the same day on a BGP fix: the failing test was re-run at the contribution's exact
commit and then at its base commit, with the container image built by the project's own
script. Green both times. The maintainer got the result instead of the question, and the
limit of that proof — a loaded runner does not have the same timing — was stated in the
message.

**A proven finding must never be left without an exit.** An email-validation defect on a
public identity service sat unsent for two days, not out of caution but out of
misclassification: a sentence in the internal note stating that *nothing left the machine
— no push, no fork, no pull request* had been read as a confidentiality instruction. The
detector now only recognises imperative forms, and the lock it used to set can be released.

**A "friendly project" label.** A maintainer merged a fix and then wrote, thirty seconds
later: *"Give me all the AI findings you have."* There is now a label, set **by hand** and
never inferred, that records a project whose maintainer asked for more. Its only effect is
to allow slightly more contributions open at once — two to four. It is also the first
measurement of the trust-budget hypothesis in [`docs/roadmap.md`](docs/roadmap.md), made
with the consent of the person concerned rather than behind his back.

**A send window.** It is now possible to cap how many contributions go out per hour. A
project receiving four in twenty minutes endures them; the same four spread out can be
read. The setting exists because the rate went up, and restraint should not depend on
someone being vigilant at two in the morning.

**What comes next**: an agent a maintainer can call himself, inside a discussion. See
[`docs/agent.md`](docs/agent.md).

---

## 2026-09-16

**This repository published for the first time.** One measured week, 10 to 16 September:
181 contributions opened across 102 projects, 83 merged, 7 refused.

**Maintainer reviews are no longer hidden behind automated reports.** A coverage or
deployment report posted after a human remark took its place in how we read the thread: the
remark was never handled. Fixed, and confirmed on a real case where a reviewer's request
had been lost.

**Method: go to the cause, not the symptom.** When a crash, a wrong value or an
out-of-bounds access is found, the question is no longer *where it breaks* but *who
produced the invalid value without rejecting it*. Severity is scored at the cause.

It came from a case where the proposed fix guarded the place that crashed, while the
project's own security engineer fixed it upstream, where an inconsistent header was being
accepted. The lesson was taken the same day.

**A project may refuse this mode of contribution, and that is final.** When a maintainer
says so, the project goes on a list and nothing is ever sent there again, automatically or
by hand.
