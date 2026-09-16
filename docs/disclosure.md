# Disclosure

Some of what a defect hunter finds should not become a pull request.

## The rule

When a finding looks like a security defect — anything reachable by an untrusted party, or
anything that crashes, corrupts or discloses — it does not go to the public tracker. It goes to
the project's private security channel, in whatever form that project asks for, and it stays
there.

That is not a courtesy. It is the difference between reporting a defect and publishing an
attack. A public issue on an unfixed vulnerability hands the exploit to everyone who reads the
tracker, and the people who read trackers for that purpose are faster than the people who
deploy patches.

## Silence lasts longer than the report

The part that is easy to get wrong: **a project publishing its own fix does not release us to
talk about it.**

A patch visible in a public repository is not a patch that is running anywhere. Between the
commit and the deployment there is code review, a release build, and then the far longer
interval in which operators actually upgrade — weeks, for anything running as a daemon on a
server where automatic updates are off. That interval is the exploitable one, and the
commit message is often a complete description of how to reach the bug.

So the rule is: nothing is said publicly about a security finding until the fix is merged
**and** carried by a released version. Not when the report is acknowledged, not when the
project opens its own pull request, not when the maintainers thank you in public. Those are all
moments where it is tempting to point at the work, and pointing at it, to a new audience,
during an unpatched window, is a way of making the problem worse while taking credit for it.

This applies here too. There is a finding of exactly this kind that is not described in this
repository, and this paragraph is the only trace of it. It will be written up when the fix
ships, not before.

## What gets said in public, always

Every pull request that leaves the pipeline ends with the same sentence:

> Found by a defect-hunting pipeline I build and run
> ([Dev-next-gen](https://github.com/Dev-next-gen)), using Claude Code with Anthropic's
> Claude Opus 5.

Unless the receiving project forbids naming an AI tool, in which case it comes off and their
own required form is used instead. Their rules win.

The reason the sentence exists is narrow and worth stating plainly. A maintainer reading a
diagnosis in a thread may reasonably assume a person is thinking in front of them, and decide
how much of their own scrutiny to spend on that basis. They are entitled to know what they are
reading before they make that call. The one place the sentence is not required is a purely
mechanical acknowledgement — pushed in `abc1234` — and only when it already appears earlier in
the same thread.

There is a second signature, `(@Dev-next-gen)` written as a mention rather than a link. It
means a human wrote that particular message personally. When it appears in a thread, the
conversation belongs to him and the automation stays out of it.
