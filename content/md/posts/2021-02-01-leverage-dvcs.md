{:title "Leverage Your DVCS"
 :layout :post
}

## This is not your parent's VCS

Some of us remember when VCS meant CVS, Perforce, SourceSafe, or another classic
like these. Most were rather straightforward to use, and did the basic job they
advertised: track changes to source code. I should say I did not work extensively
with most of these, but I'm going to make a few general comments, opinion-based:

* They were designed around one source of 'truth' or main code repo.
* Branches and merges were not encouraged, and often difficult, if not impossible.
* Logs were glorified changelogs.

Keep in mind computing power was far less than today, so there was a cost incurred
for computing diffs, copying large repos, and storing code.

By now, nearly everyone has come to embrace distributed version control. While `git`
is the tool most of us use, it's not the only one. Some still use `mercurial`, and
`darcs` is still alive (and doesn't get as much credit as it should have).

## DVCS as a power tool

Whichever tool you use, most likely it allows cheap branching, rewriting of history,
and ways to share patches, branches, or forks between repositories, which could each
be copies of an original repo. In the case of `git`, which I've been using the longest,
I've noticed that most of my colleagues know just enough to commit their work,
push and pull changes, and view the history log. And that's about it.

While you generally won't hear any complaints about this approach, there's a huge
opportunity being lost to leverage the tool. Have you ever heard a developer
say they still coded with notepad? Sure, it can be done, but if a more advanced tool
exists that makes your job much easier, why not use it, right? Well, `git` and similar
DVCS tools are similar. Once you learn to *really* use them, you will wonder why you
waited so long to do so.

Distributed version control has had a tremendous impact on workflow. And that impact
has evolved over time. Best practices have been built up, torn down, and rebuilt. It
has become one of those tools that has spawned entire schools of thought on how development
should be done (CI/CD, trunk-based development with feature flags, etc).
