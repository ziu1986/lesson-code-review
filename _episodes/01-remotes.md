---
layout: episode
title: Concepts around code reviews
teaching: 20
exercises: 0
questions:
  - How can we backup repositories?
  - How can we share repositories with others?
  - How can we keep repositories in sync?
  - What are different ways to make a copy of the entire repository?
objectives:
  - Understand the concept of a code review.
keypoints:
  - As you can see, there are plenty of great reasons why development teams should introduce and follow Code Reviews in your company. But still there are questions – does this investment in time return? Should I still practice code review, even if it takes a lot of time, and my code probably will not become that bad if I resign?
  - We can measure ROI by the ratio between benefits in quality divided by time. I might be abstract, but one thing is obvious – the less time overhead code review requires, the better.
  - "`git clone` copies everything: all commits and all branches."
  - Branches on the remote appear as (read-only) local branches with a prefix, e.g. `origin/master`.
  - We synchronize commits between local and remote with `git fetch`/`git pull` and `git push`.
  - Repositories that are shared online often synchronize via pull requests or merge requests.
  - Repositories that are forked or cloned do not automatically synchronize themselves.
---

## Motivation

- You are working in a big project where several persons have contributed at different times in the code development
- Someone has given you access to a repository online, you have developed some new functionalities and would like to contribute to the 'main' code by asking for a pull request or merge with master

- ... and you want to contribute to it.
- It is quite easy to make a copy and send a change back.
- First, we do this a relatively simple way: get repository, make a change
  locally, and send the change directly back.
- Then, we make a "pull request" that allows a review.
- Once we know how code review works, we will be able to propose changes
  to repositories of others and review changes submitted by external
  contributors.

---

## What is a code review?
Before explaining what a code review is, let's remind our self about the basic version control system (e.g git) concepts - branches and pull requests. A project consisting of several developers will collaborate in creating new features and bug fixing. As a standard it is common to develop changes in their own branches. A branch is a separate environment that

Before I can explain what code review is, I have to remind you about basic git (code version control system) concepts - branches and pull requests. If you are familiar with code review concept, you can skip to the next section.

When developers collaborate on creating new features and fixing bugs, they (hopefully) develop their changes on branches. In git, branches are separate “stages” where code is changed without affecting code on other branches (e.g., other developers features).

When a feature is completed, its author creates so-called Pull Request, which is a situation when some changes are requested to be merged to the main branch – so every developer creates features isolated, and in the end, everyone tries to merge them into the main codebase.

Finally, code review is the process performed during living pull request, where other developers check the code, comment changes, and perform discussions with the original author about proposed solutions.




## How To Do Code Review?
Code review is a discussion. It takes two to tango, so at least one developer has to be involved except the code author, but of course, more developers can – and sometimes even should – join.

Typically when code author opens Pull Request, he/she requests reviewers by selecting who should join the discussion – these developers should get notified. Of course, the review can be added without requesting – for example, a developer with free time can help others by adding extra reviews.

Code review platform allows developers to see a comparison between the original code and changes proposed by code author. Each line of code can be commented, as well as general comments can be added to Pull Request. Code review can end with three different outcomes:

- Accepted: when code is fine, and reviewer agrees to merge changes
- Rejected: where reviewer denies merging and requires changes to the proposed code.
- Comment:  where a reviewer adds remarks but doesn’t make the decision about merging. It can be useful when PR is work-in-progress or developer doesn’t feel competent enough to vouch for checked code.
The code review process is a discussion, so sometimes requested changes are applied by the author, but sometimes code author doesn’t agree and discuss the problem with the reviewer. But this cuts both ways – sometimes it is a practical education process which ends with higher code standard, sometimes it’s a long and unproductive discussion (or even a flame!).



## Commits, branches, repositories, forks, clones

- **repository**: The project, contains all data and history (commits, branches, tags).
- **commit**: Snapshot of the project, gets a unique identifier (e.g. `c7f0e8bfc718be04525847fc7ac237f470add76e`).
- **branch**: Independent development line, often we call the main development line `master` or `main`.
- **tag**: A pointer to one commit, to be able to refer to it later. Like a sticky note that you attach to a particular commit (e.g. `phd-printed` or `paper-submitted`).
- **cloning**: Copying the whole repository to your laptop - the first time. It is not necessary to download each file one by one.
- **forking**: Taking a copy of a repository (which is typically not yours) - your
  copy (fork) stays on GitHub and you can make changes to your copy.

<img src="{{ site.baseurl }}/img/overview/fork_PN.png" width="800" style="border:2px solid #000000;"/>

---

## Generating from templates and importing

There are two more ways to create "copies" of repositories into your user space:
- A repository can be marked as **template** and new repositories can be
  **generated** from it, like using a cookie-cutter.
  The newly created repository will start with a new history, only one commit, and not
  inherit the history of the template.

<img src="{{ site.baseurl }}/img/overview/generate_PN.png" width="800" style="border:2px solid #000000;"/>

- You can **import** a repository from another hosting service or web address.
  This will preserve the history of the imported project.

<img src="{{ site.baseurl }}/img/overview/import_PN.png" width="800" style="border:2px solid #000000;"/>

---

> ## Discussion/exercise
>
> - Visit one of the repositories/projects that you have used recently and try to find out
>   how many forks exist and where they are.
> - In which situations it could be useful to start from a "template" repository by generating?
{: .discussion}

---

## Synchronizing changes between repositories

- We need a mechanism to communicate changes between the repositories.
- We will **pull** or **fetch** updates **from** remote repositories (we will soon discuss the difference between pull and fetch).
- We will **push** updates **to** remote repositories.
- We will learn how to suggest changes within repositories on GitHub and across repositories.
- We will learn how to update forks by pulling/fetching changes and pushing them to forks.


## Sources

- [ostrowski.ninja](https://ostrowski.ninja/code-review-practices/)
