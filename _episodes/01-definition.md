---
layout: episode
title: Definitions
teaching: 30
exercises: 0
questions:
  - How can we minimize the number of bugs in a project?
  - How can we make sure that the code style is followed by all developers?
objectives:
  - Understand the usefulness of code reviews in teamwork
keypoints:
  - Minimize bugs and error in new code
---



## What is a code review?
Before explaining what a code review is, let's remind ourselves about the basic version control system (e.g git) concepts - branches and pull requests (PR).

A project consisting of several developers will need to collaborate when creating new features and doing bug fixing. As a standard, it is common to develop changes in their own branches. A branch is a separate environment used to develop a certain feature without affecting any other part of the codebase than needed in the actual program.

When a feature is complete, the author can ask for a PR, where the developed changes are merged back into the main/master branch. During the development, every feature has been isolated. In the end, all the separate changes are added to the main codebase.

A code review is a process that is performed during the PR, where other developers will check the logic and quality of the code. One will typically  comment on, discuss changes and solutions of the code suggested by the original author.


---

> ## Exercise/discussion: Why should you require code review in your projects?
>
> - For which reasons do you see that giving and receiving code reviews are useful for a team?  Write the points you think about in the [HackMD](https://hackmd.io/jKJFUp3IS5OnwBi6-3vr-w).
>
> > ## Some arguments
> >
> > ###  1. Identification of bugs
> >  Most likely, the longer a bug exists in a code, the harder it is to detect and terminate it. In time, more and more application parts can rely on defective code, making it more expensive to fix.
> > A code review will not catch all bugs, but an extra pair of careful eyes can see what others don’t. Developers’ experience can vary a lot, one of them could have done a lot of work in previous projects related to, for example, dates manipulation, another one will be experienced in animations or performance. That’s a widespread situation when a developer already solved a problem once and just by looking at the code will know that this or that line will cause trouble in the future.
> > ###  2.  Improvement of the overall code quality
> > It’s human nature that we try more when the effects of our work are evaluated by someone else. No one wants to be recognized as a sloppy nor untalented employee or student!
> > > #### How does it improve code quality?
> > > Reviewers will review not only implementation (which, if correct, also enhances the codebase), but how much code is readable (“I don’t understand the code, could it be simplified”) or the architecture (“I will need this piece of logic”). Reviewers can also mention that some code is duplication (“This is already implemented here”) or check code against domain knowledge, which can be more extensive if the reviewer is working longer in the project.
> >
> > ### 3. Further education of the team
Doing and receiving code reviews from both senior and junior team members is an effective way to learn something new. Two efficient ways to learn code are: by coding and reading/seeing other examples. On top of that, you will learn from your's and other's mistakes. So if a developer receives feedback on his/her code, he/she learns from the reviewer's experience and failures. Quick feedback is very effective, and the developer doesn’t have to see the code fails on production to determine that the code was damaged. The reviewer is learning by reading. Every programmer has a unique experience, and the way problems are solved will be different. Sometimes even great programmers will have a very narrow point of view (“If you have a hammer, everything looks like a nail”), which can be problematic, but also widened by exposing to some other problem solutions.
> > ###  4. Keeping the team on the same page
> > In agile projects, there are daily scrum meetings (standups), and one of its profits is explaining to the team what was done by everyone. However, these reports focus mostly on high level, business problems. Browsing Pull Requests can give developers similar insight about features developed, but reading the code is even a step further. During Code Review, the reviewer should get familiar with business requirements (it’s already a huge thing to focus on others work) and later will learn what new modules were introduced or removed by others. Even a quick look at the code without deep dive into implementation details can be beneficial for the reviewer. If developer A is aware of new work by developer B, he/she can use it without duplication.
> > ### 5. Onboarding of new developers
> > Hiring a new developer is a considerable cost – the recruitment process is only the beginning. Before a new developer will become productive and actually “earn” his/her salary, weeks or months will pass. The bigger and more complicated the project, the more time it will take a new developer to understand the codebase and business behind it. Code review is a great solution to speed up the developer's onboarding. A new employee should read the current code, ask questions, and get familiar with how the team solves problems and manages the project. Also, when a new programmer starts creating features, quick feedback from the rest of the team will reduce the time required to dive into the project.
> > ### 6.  Assure standardization of code rules and style
> > It’s better to have “some” style guide followed by everyone, then each developer having his/her own “perfect” style guide. Code without standardized rules and code style is messy, hard to read, and problematic. Each developer’s settings will overwrite another’s, causing polluted code changes and inconsistency. Code review is the discussion, so if any developer requires some change (eg, “Don’t use tabs, use four spaces”), the request should be discussed by the team. If a team agrees on one or another way how to do things, they just created a standard to follow. The longer project lives, the more standards appear, and code becomes more readable – it feels like it was written by one person, not ten. A highly standardized codebase also makes the process onboarding of new developers easier.
> {: .solution}
{: .challenge}

## The goal of a code review
There are several benefits of performing code reviews in a team. Typically, the purpose you can look for will be improving general code quality and reducing the number of bugs by sharing the knowledge of the author and reviewers. Also, developers will educate each other on how to write better code and understand business problems.


## How to do a code review?
A code review is a discussion between developers. In addition to the original code author one need at least one, usually several team members. In a team or existing project, the person who opens a PR will typically assign/request another team member to do the review. If the code review is done through GitHub, these persons will be automatically notified.

A code review platform allows developers to see a comparison between the original code and changes proposed by the code author. Both general comments about the code, or specific feedback on each line of the code can be commented on. Typically a code review will end with one of the three following outcomes:

- Accepted: the code is fine and the reviewer agrees to merge changes.
- Rejected: the reviewer denies merging of the current state of the code. She/he should propose changes in the proposed code for the PR to be accepted.
- Comment:  a reviewer adds remarks but doesn’t make the decision about merging. It can be useful when PR is work-in-progress or developer doesn’t feel competent enough to vouch for checked code.
The code review process is a discussion, so sometimes requested changes are applied by the author, but sometimes the code author doesn’t agree and discuss the problem with the reviewer. This cuts both ways – sometimes it is a practical education process which ends with a higher code standard, sometimes it’s a long and unproductive discussion (or even a flame!).
