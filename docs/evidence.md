# Evidence

Three threads from one week, chosen because they are the mechanism described in
[thesis.md](thesis.md) actually happening. All of them are public and can be read in full.

## A maintainer, a bot, and a patch that improved between them

**[orval-labs/orval #4123](https://github.com/orval-labs/orval/pull/4123)** — 16 September 2026,
one hour and seventeen minutes from the first objection to the merge.

```
12:17  melloware        three inline remarks on the diff
12:25  melloware        CHANGES_REQUESTED
12:40  Dev-next-gen     an answer to each remark, and a new commit
12:47  coderabbitai     re-reads the change
13:07  Dev-next-gen     a second commit, narrowing the rewrite to the body prop itself
13:11  coderabbitai     acknowledges the fix
13:31  melloware        APPROVED
13:34  melloware        merged
```

Three commits in the end — `3595a9c`, then `03308da`, then `59ce31b`. The patch that landed is
not the patch that was opened, and the difference came out of that exchange. The maintainer
spent about fifteen minutes of real attention on a fix that had been through two rounds of
review before approving it.

## A review with no human in it at all

**[pion/webrtc #3549](https://github.com/pion/webrtc/pull/3549)** — the first and so far only
review is from `copilot-pull-request-reviewer[bot]`, at 14:53, asking that the FU start bit be
required in the key-frame check. Commit `7cb6fa1` answers it, with a reply in the review thread.
No person has read the diff yet, and the patch is already a round better than when it arrived.

## Verification going the other way

**[apache/seatunnel #12327](https://github.com/apache/seatunnel/pull/12327)** — a ClickHouse
integration job failed on 99 rows. The maintainer, `DanielLeens`, called it a test-isolation
flake before anything had confirmed it. Rather than accept the benefit of the doubt, the
pipeline re-ran the same job at the same commit, `1d4e981`, nothing changed in between, and
came back with `Tests run: 140, Failures: 0, Errors: 0` — which settled it.

> Thanks for confirming [...] the part-6 re-run coming back fully green (`Tests run: 140,
> Failures: 0, Errors: 0`) at the exact same commit is exactly the signature of a test-isolation
> flake rather than something your diff introduced, and it settles the "why 99 rows" question
> well enough for this PR's purposes.
> — DanielLeens

This is the case worth dwelling on. The automation did not consume a maintainer's judgement.
It **supplied** a fact that would otherwise have cost the maintainer an hour, about their own
project's CI.

## Where it gets refused

Refusals are not noise, and reading them is more informative than reading the merges. Over the
same week, seven pull requests were closed without merging. The reasons fall into three groups:

- **The behaviour was intended.** The defect was real as a divergence between what the code
  announced and what it did — and the maintainer wanted the behaviour, not the announcement.
  The right fix was the opposite of the one proposed.
- **The process came first.** Some projects require an accepted, triaged issue before any pull
  request. Opening the issue at the same time as the patch does not satisfy that.
- **The contribution was unwelcome as a category.** A project is entitled to decide it does not
  want fixes produced this way, and to say so. When one does, it goes on a list and nothing is
  ever sent there again.

None of those are bugs in the finding. They are what the two rules are for, and the third
category is the only one that is permanent.
