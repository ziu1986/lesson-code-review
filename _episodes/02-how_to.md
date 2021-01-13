---
layout: episode
title: Best practices
teaching: 15
exercises: 0
questions:
  - How can we collaborate with others within one repository?
objectives:
  - Understand how to collaborate using a centralized workflow.
  - Understand the difference between local branch, origin/branch, and remote branch.
keypoints:
  - Centralized workflow is often used for remote collaborative work.
  - "`origin` refers to where you cloned from (but you can relocate it)."
  - "`origin/mybranch` is a read-only pointer to branch `mybranch` on `origin`."
  - "These read-only pointers only move when you `git fetch`/`git pull` or `git push`."
---


##  Techniques to ensure maximum efficiency


Code reviews can be long, that is true, but just like any other process can be optimized. Here are some code review best practices that can be implemented in your company.


### How to do a code review?
A code review is a discussion between developers. In addition to the original code author one need at least one, usually several team members. In a team or existing project the person who opens a PR will typically request which other team members that should do the review. If the code review is done through GitHub, these persons will be automatically notified. Of course, one could also ask for a PR without requesting a specific member to perform the review. A developer with free time could also be a natural choice for a person doing a review.

A code review platform allows developers to see a comparison between the original code and changes proposed by code author. Both general comments about the code or specific feedback on each line of the code can be commented on. Typically a code review will end with one of the three following outcomes:

- Accepted: the code is fine and the reviewer agrees to merge changes.
- Rejected: the reviewer denies merging of the current state of the code. She/he should propose changes in the proposed code for the PR to be accepted.
- Comment:  a reviewer adds remarks but doesn’t make the decision about merging. It can be useful when PR is work-in-progress or developer doesn’t feel competent enough to vouch for checked code.
The code review process is a discussion, so sometimes requested changes are applied by the author, but sometimes code author doesn’t agree and discuss the problem with the reviewer. But this cuts both ways – sometimes it is a practical education process which ends with higher code standard, sometimes it’s a long and unproductive discussion (or even a flame!).




### Language style
It is hard to perform neutral feedback in a written language. Especially, if the written language is not your mother tounge. The tone of code reviews can greatly influence morale within teams. Reviews with a harsh tone contribute to a feeling of a hostile environment with their microaggressions. Opinionated language can turn people defensive, sparking heated discussions. At the same time, a professional and positive tone can contribute to a more inclusive environment. People in these environments are open to constructive feedback and code reviews can instead trigger healthy and lively discussions.

Good code reviews ask open-ended questions instead of making strong or opinionated statements. They offer alternatives and possible workarounds that might work better for the situation without insisting those solutions are the best or only way to proceed. These reviews assume the reviewer might be missing something and ask for *clarification* instead of *correction*.

Better code reviews are also empathetic. They know that the person writing the code spent a lot of time and effort on this change. These code reviews are kind and unassuming. They applaud nice solutions and are all-round positive.




### Two reviewers are better than one
It’s not easy to find a consensus if there are two different opinions on the table and two people who have to agree on one of them. Despite how strict computer science can be, there are a ton of problems which solutions based on very non-scientific premises and guesses. Both sides can argue and even fight to prove one’s right. Not many developers have in mind business problems (time!), so they can waste a lot of resources on pointless discussions.

Another problem could be the personal character of team members. Sometimes people get frustrated because they can’t push opinion against someone with more communication skills.

To solve this problem, it only takes to introduce a third developer (typically second reviewer), who will tip the balance and eventually agree only with one of the parties (or propose another solution).

If you have the resources, I recommend having two reviewers by default, but if you lack developers time, add extra reviewer if there is a conflict to solve.

Worth to mention that some problems better fit specific issues. Typical developers pair can be more effective when summoning expert from a particular domain to audit the code.

So – try to have two reviewers or at least one backup reviewer.

### Make the Code Review a priority
Code review is a blocker for merging a feature, so if a developer requires some piece of code to be available for the new feature, it could be a problem. Required changes can be manually merged into the new feature before the start, but it can lead to code conflicts, on the other hand, the developer will wait to do nothing until changes are made.

As you know, blockers should be found as soon as possible and solved as quick as possible, so work is smooth as it gets.

So it is essential to make developers understand that pending code reviews (and overall pull requests) are actually more important than their own ongoing work (of course in a reasonable way, critical fixes are even more critical). It’s not an easy topic, because developers seem to care about their focus state a lot, but it can be communicated like this: make code review first thing developer do when:

Starting work in the morning
Going back from lunch
Going back from Fussball/PlayStation/darts break
Going back from meeting
So, if developers lose their focus anyway, make a habit first to check if there are no pending review by their peers.

Checking for new code review requests shouldn’t be too hard – it can be done in several ways. A developer can browse Github for open PRs with “Awaiting review from you” status. Also, each developer will probably get an email with a Code Review assignment. You can easily connect Github to Slack so that each open PR will be posted to the channel.

So – try to explain developers the importance of code review. Experiment with some rules to decrease code review waiting time.

### Establish Code Review rules and write them down
Code Review process, like any other process, can use some rules, especially in bigger and more complex projects. More developers in the team mean diverse experience and practices. It is good but sometimes can slow down the effectiveness of work.

So, each team should establish some set of rules and write them down (don’t miss this point!). I don’t think there is much benefit of standardizing process in a whole company, but the team works together on a daily basis. There are two significant benefits of making this happen:

New developer on the board requires education about existing rules. Don’t waste time on explaining every time the same things. It’s also frustrating to the new guy that he/she is corrected many times, instead of first reading how things are done in the team.
In case of conflicts or misunderstandings, there is a single, living source of truth which can be referenced.
Here are some code review best practices that I always include in my work, which can help you improve the code review process.

Only comment author can resolve comment – if code was corrected or after discussion author decides to fix it.
Don’t mention the same problem many times. Don’t bloat the code, say it once and ask to fix everywhere.
If there are pending, not resolved comments, the assignee is a code author who should fix or comment back.
If there are discussions commented by the code author, the assignee is reviewer, who should continue a discussion or resolve comments and approve.
Use labels to mark what actions should be next – e.g. “ready for review” “ready for the QA” etc.
The popular problem is when the code author thinks he/she is waiting for review, and the reviewer feels he/she is waiting for fixes/comments back.

So, establish some rules, write them down, and improve them over time.

### Ensure that Pull Requests are good
An inseparable part of code review is a pull request. The review is done on changes someone request to “pull” to the main branch.

If the PR is good, a code review should be easy and fast. If PR is bad – code review will be exhausting, long, and “no one will have time to do it.”

The main rule of good Pull Request is to keep it short. Two hundred lines of code are easy to understand and to find problems. Two thousand lines are not. The cognitive load increase is exponential relative to the number of changes done in the request.

Short PR can be checked during a coffee break – long PR will cost literally many hours, and code review quality will decrease because the reviewer will be eventually too tired and confused to keep quality for a long time.

An extra pro tip is to make PRs well labeled. An author should ensure request is linked to a ticket system (Jira etc.), and there is reasonable description/readme for reviewers.

So, ensure developers spend some little extra time to create a good quality pull request, which will return in many hours of reviewing work.

Introduce Code Review audits between teams
In large organizations with many teams and projects, there are, for sure, a lot of approaches on how to manage development teamwork. This is a great approach to improve!

More experienced team (e.g., with senior engineers) can naturally develop good practices based on their experience, even without any management help. This is an excellent opportunity to extend their workflow to other teams.

On the other hand, you can observe a team with aggressive comments, long waiting time, and a broken process. The faster you know it and fix it, the better. Don’t trust that things will escalate soon enough.

Think about performing periodic audits of selected teams to observe the condition of the code review process (just like your audit management, scrum meetings, etc.!). Some teams will have problems, and some will be outstanding. Use this knowledge to share the experience of developers and fix possible issues on the early stage.

So, think about assigning CTO or other senior-level engineer or technical manager to perform audits of daily development processes.

### Automate as much as possible
Developers prefer automating over manual and repetitive tasks. Code review might stand between code and human, but still, a lot can be delegated to the machine.

### Set CI pipelines
First of all, PR should trigger a CI pipeline with tests and builds. This step runs a few minutes and catches a lot of problems that might be detected by the reviewer. Well written tests should cover a lot of quality problems, but without set CI, someone can merge it even if tests fail.

Connect your CI pipeline tool to Github and block possibility to merge until all checks pass. Don’t waste developers’ time to check code which will not even build.

### Set code style formatters and linters
A lot of time wasted on code review is a ton of pointless comments related to tabs vs. spaces and how developers prefer code to be written (not what problems does it solve). Of course code consistency is important, but it shouldn’t bloat the code review process.

There are tools made to automate these jobs, like Prettier or ESLint for javascript ecosystem or Robocop for Ruby. They are responsible for applying and reporting about “code style guide” and practices I mentioned before. The more rules set, the more consistent, will be code. Developers can vote for changing existing rules or create new ones, but automated tasks will ensure that ongoing work is following existing ruleset.

I recommend setting code formatter automated on Git pre-commit hook (which will run automatically) and linters on Git pre-push hook (which will cancel push it doesn’t pass). Also, linter should run on the CI pipeline. When these checks pass, there is much less to check by reviewer, who can focus on problem-solving.

Deploy branch to test environment
If you have a decent time assigned to DevOps work, I recommend you to set automatic deployment of open Pull Requests. Typically if a developer wants to check if the code work, he/she has to download and build it locally. It takes time, and sometimes it’s also a problem – if the QA department or product owner wants to check new feature before the merge.

Preparing automatic deployments of PRs will cost time to set up, but will let the team quickly check ongoing work, also by non-technical people.

Extra pro-tips from Ideamotive Team
Commit often and publish work-in-progress PRs
There is a bad practice when some developers wait for days until they show some work. Encourage them to commit often and push frequently. It will not only save the work in case of losing code locally (theft, broken device), but it will make the team more productive. Opening “Work-in-progress” branch will allow others to check the overall concept of changes over monitoring the implementation. This is especially important for junior developers when a reviewer can say after a few lines of code that this is just a wrong direction. It’s better to remove 50 lines of code than 500 or (5000).

Favor reviewers who know the problem
Probably there is not much sense in asking frontend developer to check backend code. If the team is big enough to choose from reviewers, it’s an excellent way to improve code quality. Some developers will better understand domain knowledge; some of them will specialize in some narrow tech problems. They will better fit review where they can give a lot of valuable feedback.

Modern git services make this easier by detecting and suggesting relevant reviewers based on historical changes or code owners.

Set live meeting in case of significant changes
If Pull Request is huge (shouldn’t be, but it happens), it can cost a lot of time to ping-pong online discussion with hundreds of comments. In this case, it could be better to set up a desk meeting where the code author explains other changes.


## How to reduce conflicts during code review?
Code review, just like any discussion, could cause conflicts between developers. Also, it’s based on giving feedback, which is very hard for both reviewer (to do it with empathy) and author (to accept criticism).

Of course, the possibility of conflicts depends a lot on the individual character of developers, but if it happens, there are few rules, how to reduce it in the future.

Write down as much as possible
Conflicts can emerge when there are two different decisions, and parties don’t want to give up the idea.

However, a lot of decisions have been made already – but they are lost in time. I mentioned code style guide before – this is an excellent example because no one will argue about “tabs vs. spaces” if this has been officially decided and written in the project documentation.

There are different ways how to create documentation like this. I like tools like Notion to develop and maintain wiki-like pages with e.g., decisions made by business or rules established by developers.

Doc like this can be referenced during reviews to avoid unnecessary conflicts.
