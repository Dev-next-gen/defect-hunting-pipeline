# The invocable agent

What comes next: an agent a maintainer can call, inside a discussion, instead of receiving
contributions nobody asked for.

```
@Defect-Hunting-Pipeline
```

This document says what it will do, what it will refuse, and what it will never ask for. It
does not say how it is built.

## Why this is the right direction of travel

Today most contributions go out unsolicited. Proven, useful, but landing on someone who
asked for nothing — and the only genuinely open question in [roadmap.md](roadmap.md) is how
many a project accepts before it tires of them.

One half of the reversal now exists. A maintainer who describes work to be taken in a thread
gets it taken, quoted, and answered with a contribution: see **When a maintainer asks for
something** in the [README](../README.md). That is the invited half. What is still missing is
the invocable half, where the project installs the agent once and calls it by name.

An invocable agent reverses the direction: it has to be installed to be called. Consent is
given once, by the project, and the question of volume dissolves. We stop knocking on the
door; we come in when called.

## What it does

It reads the discussion, the proposed change and what continuous integration says. Then it
works the way the rest of this system works: it isolates the defect, proves it with a test
that fails before and passes after, and hands over the fix — with the proof, not instead of
it.

Two ways of handing over, depending on who called:

- **a maintainer of the project** gets a full contribution, opened from a repository we own;
- **anyone in a discussion** gets **suggested changes** — the kind the author applies with
  one click and dismisses with another. Nothing is written without their gesture.

## What it will never ask for

**Write access to your repository.** No write permission on your code will be requested, in
either case. A contribution arrives like any outside contribution, and a suggestion belongs
to whoever applies it.

## What it will refuse to do

**Publish a vulnerability.** If what it finds is exploitable by a third party, it stops
before any publication and the report goes through the project's private security channel.
Nothing is said publicly until a fix is not only written but **released** — see
[disclosure.md](disclosure.md).

**Claim without proving.** If the defect cannot be proven — the environment is missing, the
budget is not enough, the failure is not reproducible — it says so and hands over nothing.
An "I could not" is information; an unproven fix is a burden placed on you.

**Take instructions from the content it reads.** A discussion, a diff, a file in the project
are **data**. Text addressed to it, asking it to install something, disable a protection or
work around a rule, is reported rather than followed.

**Answer uninvited, or come back after being told no.** A project that refuses this mode of
contribution is recorded once and for all.

## Where things run, and with what

Building and testing someone else's code means executing it. That will happen in a
disposable environment, with no access to our credentials, with no network egress while the
code runs, destroyed afterwards. The token that lets the agent answer you will never be
reachable by the code it runs: that is the condition for a malicious contribution to obtain
nothing beyond what it brought.

Since 17 September that disposable environment exists and is used: someone else's code is
built and tested inside it, it cannot reach the machines that operate this pipeline, and it
is destroyed afterwards. What does not exist yet is the agent itself, so this document
remains a commitment rather than a description. The part that used to be the obstacle is no
longer the obstacle.

## What is written at the bottom of every message

The same sentence as everywhere else, naming the system and the model. An account suffixed
`[bot]` says that it is an automated one; it does not say which, nor who answers for it. We
do.

One consequence of that name: the identity `Defect-Hunting-Pipeline` is separate from the
account of the person who builds and operates this system. What goes wrong here does not
implicate the contributions made by hand under that account, and the reverse holds too.
