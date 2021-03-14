{:title "Leverage Your DVCS"
 :layout :post
}


Yet another article on version control, hopefully with a unique spin.


## This is not your parents' VCS

Some of us remember when VCS meant CVS, Perforce, SourceSafe, or
another classic like these. Most were rather straightforward to use,
and did the job they advertised: track changes to source code. I
should say I did not work extensively with most of these, but I'm
going to make a few general comments, opinion-based:

* They were designed around one source of 'truth' or main code repo.
* Branches and merges were not encouraged, and often difficult, if not
  impossible.
* Logs were glorified changelogs.

Computing power was far less than today, so there was a cost incurred
for computing diffs, copying large repos, and just storing code.

By now, nearly everyone has come to embrace distributed version
control. While `git` is the tool most of us use, it's not the only
one. Some still use `mercurial`, and `darcs` is still alive (and
doesn't get as much recognition as it should).


## A simple comparison

Think about the IDE you use. Perhaps it's an IDE only for one
language. Or it's designed more generically, with plug-ins for various
languages. Yet another possibility is a much more basic tool like an
editor, but with extensions over the years that add IDE-like
functionality. Whatever your choice of IDE, think about the first time
you used auto-complete, integrated debugging, jump-to-references, or
documentation at your fingertips. Some of these tools took a while to
become part of your workflow, but how productive would you be today if
you had to give them up?


## DVCS as a power tool

Back to version control. Whichever tool you use, most likely it allows
cheap branching, rewriting of history, and ways to share patches,
branches, or forks between repositories, which could each be copies of
an original repo. In the case of `git`, which I've been using the
longest, I've noticed that most of my colleagues know just enough to
commit their work, push and pull changes, and view the history log.
And that's about it.

While you generally won't hear any complaints about this approach,
there's a huge opportunity being lost to leverage the tool. Have you
ever heard a developer say they still coded with Notepad? Sure, it can
be done, but if a more advanced tool exists that makes your job much
easier, why not use it, right? Well, `git` and similar DVCS tools are
similar. Once you learn to *really* use them, you will wonder why you
waited so long to do so.

Distributed version control has had a tremendous impact on software.
And that impact has evolved over time. Best practices have been built
up, torn down, and rebuilt. It has spawned entire schools of thought
on how development should be done (CI/CD, trunk-based development with
feature flags, the original 'git flow', etc).

DVCS can have the same impact on your personal workflow. Do not just
view version control as something you do when you finish a bug or
feature before you move on. View it instead as a vital part of your
recordkeeping. Better yet, view it as part of your development
process.


## Commit messages are extended code comments

We've all heard the debate over comments in code. How much is *too*
much? How little is *too* little? Have you ever created a multi-line
comment that you felt needed to be there, but then deleted it because
of concern it was *too* much, that it would be ignored, or worse yet,
would be misleading if it were not maintained along with the code?

In an ideal world (and codebase) the code would speak for itself, and
we would never, EVER allow a kludge solution that requires any kind of
explanation. But that's not how things work in the real world.
Sometimes code does *not* speak for itself, especially if an
ostensibly better implementation comes to mind the moment you view it.
Or, an unusual characteristic of the problem domain, libraries used,
language of implementation, or even hardware itself require an outlier
solution that is not immediately evident when reading the code.
Sometimes there is more to the story than should be in a comment.

Git commit messages are an idea place for such explanations. They will
never suffer bitrot, because by definition they are timestamped,
immutable and forever connected to the related code.

Here's an example. A couple of years ago, we had a bug where a user
got an error when saving comments on a customer account. They were
trying to use an emoji. Let me say that I am *not* an expert in
unicode or character encoding by any means. I know or learn enough to
deal with these issues as they arise. After some detective work, we
learned that the system encoding in theory should have allowed emojis
at both the platform and database levels. But as I experimented, I
found that some emojis worked, and others did not. It seemed this was
related to our database encoding system. There was a cutoff point in
the unicode system beyond which the characters were not accepted by
the database. So, I added validation to allow characters up to that
boundary, and added unit tests for both working and non-working
unicode characters.

After the bug was fixed and the ticket closed, I still had a nagging
feeling something was missing. I really wanted to capture the
explanation of what I had learned and how the unit tests validated
that explanation. But I never found a place that felt right. It didn't
belong in a wiki page and it seemed too much for code comments.
Documenting the unit tests was an idea, but it still seemed too far
from the code. And there was the possibility that some future change
to the platform or the database encoding could make the tests
irrelevant.

Since then, I have realized that `git` log messages are ideal for
this purpose. Let's consider why.

1. They are immutable and timestamped.
2. They can appear next to the code in question.
3. Not all projects have extensive unit tests.

Most of us using `git` treat the `master` branch as immutable history.
Viewing the log shows how the code evolved over time, and *why* it
changed, assuming you practice some discipline with your commit
messages. While the history might show you when a code comment was
introduced, it doesn't tell you if it is still relevant. However, the
commit message itself *is* relevant to exactly that moment in time. If
the code changes, it's very possible the comments will drift out of
date, but the git history *cannot* drift out of date, because it is
bound to that moment in time when it was relevant to the code it
was committed with.

Also, nearly every IDE out there allows you to show git commit
messages right next to the code via `git blame` mode. It's as if you
have expandable comments available at the press of a button or click
of a mouse. They can be as brief or as extensive as needed to convey
the *why* of the code change. So you never have to decide if you
should shorten a code comment out of fear it will be too long to
remain in the source code, nor leave it out completely because there's
no good place to put it.


## Find your own 'zone'

This is just one example how `git` or any DVCS can have a tremendously
positive impact on your workflow. But you need to find what works for
you. Most of these tools have a plethora of commands and options, and
no shortage of online tutorials showing how to use them. The 'onion'
approach is one way to learn these tools. Start with the surface,
until you are comfortable with it, and add deeper commands as you
learn about them, or find a need unmet by your current level of
knowledge. Many `git` users have said if you try to master it all at
once, it's like cutting onions, and ends in tears. Some commands are
confusing, and the options even more so. So start slowly, master what
you need, then add more. You might never need the git reflog. But
you'll very likely find rebase and squash become vital parts of your
workflow. And it all starts with commit log discipline.

The goal isn't just knowing a bunch of `git` commands better than your
colleagues. It's to know them well enough to code and commit without
fear, and to experiment with minimal overhead. The side benefit should
be to use `git` as more than a glorified changelog or just a tenuous
connection between your ticket system and the code itself.

In a future article, we'll talk about some ways to apply these
concepts, hopefully leading to those moments when you'll be very glad
you put the effort into learning and embracing your DCVS' many
capabilities.
