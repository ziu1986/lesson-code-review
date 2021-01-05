---
layout: episode
title: Definitions
teaching: 20
exercises: 0
questions:
  - How can we minimize the number of bungs in a project?
  - How can we make sure that the code style is followed by all developers?
objectives:
  - Understand the usefulness of code reviews in teamwork
keypoints:
  - Minimize buggs and error in new code
---



## What is a code review?
Before explaining what a code review is, let's remind ourselves about the basic version control system (e.g git) concepts - branches and pull requests (PR).

A project consisting of several developers will need to collaborate when creating new features and doing bug fixing. As a standard, it is common to develop changes in their own branches. A branch is a separate environment used to develop a certain feature without affecting any other part of the codebase than needed in the actual program.

When a feature is complete, the author can ask for a PR, where the developed changes are merged back into the master branch. During the development, every feature has been isolated. In the end, all the separate changes are added to the main codebase.

A code review is a process that is performed during the PR, where other developers will check the logic and quality of the code. One will typically  comment on, discuss changes and solutions of the code suggested by the original author.


---

> ## Exercise/discussion: Why should you require code review in your projects?
>
> - For which reasons do you see that giving and receiving code reviews are useful for a team?  Write the points you think about in the [HackMD](https://hackmd.io/jKJFUp3IS5OnwBi6-3vr-w).
>
> > ## Some arguments
> >
> > ###  1. Early identification of bugs
> >  Most likely, the longer a bug exists in a code, the harder it is to detect and terminate it. In time, more and more application parts can rely on defective code, making it more expensive to fix.
> > A code review will not catch all bugs, but an extra pair of careful eyes can see what others don’t. Developers’ experience can vary a lot, one of them could have done a lot of work in previous projects related to, for example, dates manipulation, another one will be experienced in animations or performance. That’s a widespread situation when a developer already solved a problem once and just by looking at the code will know that this or that line will cause trouble in the future.
> > ###  2.  Improve the overall code quality
> > It’s human nature that we try more when the effects of our work are evaluated by someone else. No one wants to be recognized as a sloppy nor untalented employee or student!  If we consider ourselves smart and most likely are open to prove it to others, don’t we?
> > > #### How does it improve code quality?
> > > Reviewers will review not only implementation (which, if correct, also enhances the codebase), but how much code is readable (“I don’t understand the code, it should be simplified”) or the architecture (“I will need this piece of logic, but I can’t use it because it’s badly designed”). Reviewers can also mention that some code is duplication (“This is already implemented here, don’t write it again”) or check code against domain knowledge, which can be more extensive if the reviewer is working longer in the project.
> >
> > ### 3. Serious education
Doing and receiving code reviews from both senior and junior team members is an effective way to learn something new. There are two ways to learn code the most efficient way: by coding, and by reading the code. On top of that, you will learn from your's and other's mistakes. So if a developer receives feedback on his/her code, he/she learns from the reviewer's experience and failures. Quick feedback is very effective, and the developer doesn’t have to see the code fails on production to determine that the code was damaged. The reviewer is learning by reading. Every programmer has a unique experience, and the way problems are solved will be different. Sometimes even great programmers will have a very narrow point of view (“If you have a hammer, everything looks like a nail”), which can be problematic, but also widened by exposing to some other problem solutions.
> > ###  4. Staying on the same page
> > In agile projects, there are daily scrum meetings (standups), and one of its profits is explaining to the team what was done by everyone. However, these reports focus mostly on high level, business problems. Browsing Pull Requests can give developers similar insight about features developed, but reading the code is even a step further. During Code Review, the reviewer should get familiar with business requirements (it’s already a huge thing to focus on others work) and later will learn what new modules were introduced or removed by others. Even a quick look at the code without deep dive into implementation details can be beneficial for the reviewer. If developer A is aware of new work by developer B, he/she can use it without duplication.
> > ### 5. Onboarding of new developers
> > Hiring a new developer is a considerable cost – the recruitment process is only the beginning. Before a new developer will become productive and actually “earn” his/her salary, weeks or months will pass. The bigger and more complicated the project, the more time it will take a new developer to understand the codebase and business behind it. Code review is a great solution to speed up the developer's onboarding. A new employee should read the current code, ask questions, and get familiar with how the team solves problems and manages the project. Also, when a new programmer starts creating features, quick feedback from the rest of the team will reduce the time required to dive into the project.
> > ### 6.  Assure standardization of code rules and style
> > It’s better to have “some” style guide followed by everyone, then each developer having his/her own “perfect” style guide. Code without standardized rules and code style is messy, hard to read, and problematic. Each developer’s settings will overwrite another’s, causing polluted code changes and inconsistency. Code review is the discussion, so if any developer requires some change (eg, “Don’t use tabs, use four spaces”), the request should be discussed by the team. If a team agrees on one or another way how to do things, they just created a standard to follow. The longer project lives, the more standards appear, and code becomes more readable – it feels like it was written by one person, not ten. A highly standardized code base also make the process of onboarding of new developers easier.
> {: .solution}
{: .challenge}

## The goal of a code review
There are several benefits of performing code reviews in a team. Typically, the purpose you can look for will be improving general code quality and reducing the number of bugs by sharing the knowledge of the author and reviewers. Also, developers will educate each other on how to write better code and understand business problems.

### Time cost
Code reviews can indeed take a lot of time. Keep in mind, that code review is just like agile development – it might feel like we add extra time, but it pays off later with better quality! A rule of thumb is to keep the suggested changes short (not more than 500 lines of code), so the person performing the review to be effective in the process.


This process should be added on top of a project’s time estimation. Just like the time spent on the development itself, it’s tough (for every developer) to estimate how much time the review process will take. The time spent on a code review will grow with the task complexity, just like the feature implementation. However, this time can be optimized (see the next chapter of this lesson).
