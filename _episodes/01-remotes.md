---
layout: episode
title: Concepts and motivation
teaching: 20
exercises: 0
questions:
  - How can we check the quality of purposed code changes?
  - How can we minimize the amount of bungs in a projcet?
  - How can we make sure that the project standard is followed by all developers?
objectives:
  - Understand the concept of a code review.
keypoints:
  - As you can see, there are plenty of great reasons why development teams should introduce and follow Code Reviews in your company. But still there are questions – does this investment in time return? Should I still practice code review, even if it takes a lot of time, and my code probably will not become that bad if I resign?
  - We can measure ROI by the ratio between benefits in quality divided by time. I might be abstract, but one thing is obvious – the less time overhead code review requires, the better.
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
Before explaining what a code review is, let's remind our self about the basic version control system (e.g git) concepts - branches and pull requests (PR). A project consisting of several developers will collaborate in creating new features and bug fixing. As a standard it is common to develop changes in their own branches. A branch is a separate environment used to develop a certain feature without affecting other part of the code on other branches. When a feature is complete the author can ask for a PR, where the developed changes are merged back into the master branch. During development every feature is isolated and in the end all the separate changes are added to the main codebase.

A code review is the process which is performed during the PR, where other developers will check the logic and quality of the code, comment and discuss changes and solutions with the original author.


---

> ## Exercise/discussion: Why should you require code review in your projects?
>
> - Which reasons do you see that code reviews are useful for a team?
>     -- Write the points you think about in the HackMD
>
> > ## Solution: some arguments
> >
> > ###  1. Early caught bugs
> >  Most likely, the longer a bug exists in your code, the harder it will be detected and terminated. In time, more and more application’s parts can rely on defective code, making it more expensive to fix.
> > A code review will not catch all of them, but an extra pair of careful eyes can see what others don’t. Developers’ experience can vary a lot, one of them could have done a lot of work in previous projects related to, for example, dates manipulation, another one will be experienced in animations or performance. That’s a widespread situation when a developer already solved a problem once and just by looking at the code will know that this or that line will cause trouble in the future.
> > ###  2.  Improved overall code quality
> > It’s human nature that we try more when the effects of our work are evaluated by someone else. No one wants to be recognized as a sloppy nor untalented employee, especially developers! We, engineers, consider ourselves smart and most likely are open to prove it to others, don’t we? If developers can still talk about programming after work, they for sure will take time to share their opinions if they are asked to.
> > > #### How does it improve code quality?
> > > Reviewers will review not only implementation (which, if corrected, also enhances the codebase), but how much code is readable (“I don’t understand the code, it should be simplified”) or the architecture (“I will need this piece of logic, but I can’t use it because it’s badly designed”). Reviewers can also mention that some code is duplication (“This is already implemented here, don’t write it again”) or check code against domain knowledge, which can be more extensive if the reviewer is working longer in the project.
> >
> > ### 3. Serious education
> > Developers love to learn. They change jobs to try new technologies; they pay for workshops, spend weekends on reading, learning, and Hackathons. A well-educated developer is not only a benefit to your company but also – probably – satisfied one. In my opinion, there are two ways to learn code the most efficient way – by coding and by reading the code. On top of that you learn on mistakes, but with the latter – on others’ mistakes. So if a developer receives feedback on his/her code, he/she learns on reviewers experience and often – failures. Quick feedback is very effective, and the developer doesn’t have to see the code fails on production to determine that the code was damaged. On the other side, there is a reviewer who is learning by reading. Every engineer has a unique experience, and the way problems are solved will be different. Sometimes even great programmers will have a very narrow point of view (“If you have a hammer, everything looks like a nail”), which can be problematic, but also widened by exposing to some other problem solutions. Code review is a great learning tool for every programmer, but it can be especially beneficial for junior developers, who need to be assisted – and this is a great way to achieve it. Of course code review will not replace learning budget and conferences, but will indirectly improve developers’ skills.
> > **Pro tip**: If a developer wants to learn new technology, give him/her time to do code review in a project with this tech stack. Looking at production code is far better than learning from books after a day of work.
> > ###  4. Staying on the same page
> > In agile projects, there are daily scrum meetings (standups), and one of its profits is explaining to the team what was done by everyone. However, these reports focus mostly on high level, business problems. Browsing Pull Requests can give developers similar insight about features developed, but reading the code is even a step further. During Code Review, the reviewer should get familiar with business requirements (it’s already a huge thing to focus on others work) and later will learn what new modules were introduced or removed by others. Even a quick look at the code without deep dive into implementation details can be beneficial for the reviewer. If developer A is aware of new work by developer B, he/she can use it without duplication.
> > ### 5. Onboarding new developers
> > Hiring new developers costs a lot – the recruitment process is only a beginning. Before a new developer will become productive and actually “earn” his/her salary, weeks or months will pass. The bigger and more complicated is the project, the longer will be time for a new developer to understand the codebase and business behind it. Code review is a great solution to speed up developers onboarding. A new employee should read the current code, ask questions, and get familiar with how team solves problems and manages the project. Also, when a new engineer starts creating features, quick feedback by the rest of the team will reduce the time required to dive into the project.
> > ### 6.  Standardization of code rules and style
> > It’s better to have “some” style guide followed by everyone, then each developer having his/her own “perfect” style guide. Code without standardized rules and code style is messy, hard to read, and problematic. Each developer’s settings will overwrite another’s, causing polluted code changes and inconsistency. Code review is the discussion, so if any developer requires some change (eg, “Don’t use tabs, use four spaces”), the request should be discussed by the team. If a team agrees on one or another way how to do things, they just created a standard to follow. The longer project lives, the more standards appear, and code becomes more readable – it feels like it was written by one guy, not ten. And more standard is also making onboarding of new developer easier!
> > ### 7. Development of team spirit
> > In an existing project with a given number of members there is also a need for knowing each other personally.
> {: .solution}
{: .challenge}

## How to do a code review?
A code review is a discussion between developers. In addition to the original code author one need at least one, usually several team members should, join. In a team or existing project the person who opens a PR will typically request other team members to do the review. If the code review is done through GitHub these persons will be automatically notified. Of course, one could also add a PR without requesting a specific member to perform the review. A developer with free time could also be a natural choice for a person doing a review.


A Code review platform allows developers to see a comparison between the original code and changes proposed by code author. Both general comments about the code or specific feedback on each line of the code can be commented on. Typically a code review will end with one of the three following outcomes:

- Accepted: the code is fine and the reviewer agrees to merge changes.
- Rejected: the reviewer denies merging of the current state of the code. She/he should propose changes in the proposed code for the PR to be accepted.
- Comment:  a reviewer adds remarks but doesn’t make the decision about merging. It can be useful when PR is work-in-progress or developer doesn’t feel competent enough to vouch for checked code.
The code review process is a discussion, so sometimes requested changes are applied by the author, but sometimes code author doesn’t agree and discuss the problem with the reviewer. But this cuts both ways – sometimes it is a practical education process which ends with higher code standard, sometimes it’s a long and unproductive discussion (or even a flame!).

## How to **not** do a code review?
It is hard to perform feedback in written language.

### The importance of the tone of the review
The tone of code reviews can greatly influence morale within teams. Reviews with a harsh tone contribute to a feeling of a hostile environment with their microaggressions. Opinionated language can turn people defensive, sparking heated discussions. At the same time, a professional and positive tone can contribute to a more inclusive environment. People in these environments are open to constructive feedback and code reviews can instead trigger healthy and lively discussions.

Good code reviews ask open-ended questions instead of making strong or opinionated statements. They offer alternatives and possible workarounds that might work better for the situation without insisting those solutions are the best or only way to proceed. These reviews assume the reviewer might be missing something and ask for clarification instead of correction.

Better code reviews are also empathetic. They know that the person writing the code spent a lot of time and effort on this change. These code reviews are kind and unassuming. They applaud nice solutions and are all-round positive.



## The goal of a code review
There are several benefits of performing code review, but each team can focus on a different matter. Typically, the purpose you can look for will be improving general code quality and reducing the number of bugs by sharing knowledge of author and reviewers. Also, developers will educate each other on how to write better code and understand business problems.

How much time does the code review process take? Can I afford it?
Code reviews can take a lot of time indeed. This process should be added on top of a project’s time estimation. Just like the development itself, it’s tough (for every developer) to estimate how much time it will actually take. Time spent on Code Review will grow with the task complexity, just like the feature implementation. However, you can optimize this overhead, and I will give you some tips later in this article.

Keep in mind, that code review is just like agile development – it might feel like we add extra time, but it pays off later with better quality!



## Summary
As you can see, there are plenty of great reasons why development teams should introduce and follow Code Reviews in your company. But still there are questions – does this investment in time return? Should I still practice code review, even if it takes a lot of time, and my code probably will not become that bad if I resign?

We can measure ROI by the ratio between benefits in quality divided by time. I might be abstract, but one thing is obvious – the less time overhead code review requires, the better.

So let’s find out how to improve this ratio!
