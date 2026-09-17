# Journal

What this system becomes, dated. Each entry says what changed, the fact that prompted it,
and what was expected of the change — so we can come back later and say whether it worked.

This journal does not describe how the system is built. It describes what it does, what it
refuses to do, and what was learned doing it.

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
