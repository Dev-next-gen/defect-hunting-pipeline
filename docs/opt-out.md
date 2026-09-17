# Opting out

If you maintain a project and you do not want contributions from this pipeline, you should be
able to say so once, in a place you already control, and have it hold without negotiating with
me. This page is the promise, written down so it can be held against me.

**Status at the time of writing: promised, not built.** The exclusion list exists and is
enforced, but it is maintained by hand, by me, which means today you still have to ask a person.
That is the gap this describes and what is being closed.

## What you will be able to do

One condition, and it is the only one: the request comes from a maintainer of the project, meaning
someone with write access to it or named in its own governance. On that point I do not bend. A
project's contribution policy belongs to the people who carry the project, not to whoever passes
through its tracker, and letting a third party close a project's door would be a decision taken
over the maintainers' heads. A request from anyone else is read, and it excludes nothing.

Beyond that, any one of these, with no reason required and no reply expected:

1. **Say it on any pull request or issue of mine.** One line, anywhere in a comment:

   ```
   @Dev-next-gen opt-out
   ```

   This one is a command, not a message, and it is handled without me reading it. What makes it
   valid is not the wording and not the tone, it is that GitHub reports the comment's author as
   holding write access on the project. That is attached to every comment on the platform, so the
   check costs nothing and cannot be argued with: from an owner, a member of the owning
   organisation or a collaborator, the exclusion applies. From anyone else the same words do
   nothing at all, and nothing is posted in reply.

   You get exactly one line back, saying it is recorded and what it covers, because a command
   whose effect you cannot see is not a mechanism, it is a hope. That line is the last thing the
   program ever writes on your project. If you carry the project without holding write access,
   use one of the two routes below and point me at where the project says so.

2. **Put it in your repository.** A line anywhere in `CONTRIBUTING.md`, `AGENTS.md`,
   `.github/CONTRIBUTING.md` or a file named `.github/no-automated-contributions`:

   ```
   no-automated-contributions
   ```

   This is the form I would rather you use, because it costs you nothing, it applies to every
   tool that bothers to read it and not only to mine, and it does not require me to have seen
   your message.

3. **Write to me.** The address on my commits works. So does an issue on this repository.

## What it means once it is in force

- The project is not scanned again.
- No pull request is opened on it again, including one already prepared and not yet sent.
- Past the one line acknowledging it, no reply is posted on any thread again, including a reply
  to a review that asks a direct question. Silence can look rude in that situation, and I accept looking rude over answering
  where I have been told not to.
- Pull requests already open are yours to dispose of. Say the word and I close them; say nothing
  and they stay open for you to close, and nothing further is pushed to them.
- It does not expire, and I do not come back to ask whether you have changed your mind.

## Why the timing matters

On 17 September 2026 I told a project publicly that I would send nothing further, and seven
minutes later the program answered a review on one of its pull requests. I had decided on the
exclusion and written it down, but the running program had not been made to read it. The decision
and the enforcement were two different things, and only one of them had happened.

So the commitment here is not only that the exclusion exists. It is that it takes effect at the
moment it is recorded, not at the next restart, and that it is checked at every point where the
program can reach a project: before scanning it, before opening a pull request on it, and before
writing a word on one of its threads. Three checks, because one is where this kind of promise
usually breaks.

## Current exclusions

Kept public, with the reason next to each, so that "excluded" read a year from now does not
suggest the code was bad. In both cases below it was not; the objection was to receiving
machine-written contributions at all, and that objection is sufficient on its own.

| Project | Since | Why |
|---|---|---|
| freeCodeCamp | September 2026 | Requires a triaged issue before any pull request, and locks pull requests it closes. |
| celery | 17 September 2026 | Three pull requests merged, then a refusal on the grounds that the work is AI-generated. Removed the same evening. |

See [`reception.md`](reception.md) for what was actually said in each case.
