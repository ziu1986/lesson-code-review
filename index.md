---
layout: lesson
permalink: /
---

# Collaborative feedback: code reviews

We have learned how to make a git repository for a single person and share it with several people. What about feedback?

* Sharing by email or manually: isn't fun and doesn't scale, projects
  are limited to the time and cognition of one person.
* One person's repository on the web: allows one person to keep track
  of more projects, gain visibility, feedback, and recognition.
* Centralized: everyone can directly update the same repository.  Good
  for small groups.
* Distributed: anyone can suggest changes, even without advance
  permission.  Maintainers approve what they agree with.

Being able to share more easily (going down the list here)
is *transformative* because it allows projects to scale to a new
level.  This can't be done without proper tools.

In this lesson we will learn how to keep repositories in sync and how to work
with remote repositories on GitHub and other services. We will discover
and exercise the centralized as well as the forking workflows, and finally
look into how to automate tasks using Git hooks.

> ## Prerequisites
>
> 1. Basic understanding of Git.
> 2. You need a [GitHub](https://github.com) account.
> 3. You need a project which where it has been performed some work. For instance the modular code development.
>
> We will do this exercise on [GitHub](https://github.com) but also
> [GitLab](https://gitlab.com) and [Bitbucket](https://bitbucket.org) allow
> similar workflows and basically everything that we will discuss is transferable. With
> this material and these exercises we do not endorse the company
> [GitHub](https://github.com). We have chosen to demonstrate a number of
> concepts using examples with [GitHub](https://github.com) because it is
> currently the most popular web platform for hosting Git repositories and the chance is high
> that you will interact with [GitHub](https://github.com)-based repositories even if you
> choose to host your Git repository on another platform.
>
> We also encourage course participants to use our new [Nordic research software repository platform](https://source.coderefinery.org),
> for more information see [https://coderefinery.org/repository/](http://coderefinery.org/repository/).
{: .prereq}
