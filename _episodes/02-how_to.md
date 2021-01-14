---
layout: episode
title: Best practices
teaching: 30
exercises: 0
questions:
  - How can feedback on code be given effectively?
objectives:
  - Understand standardized techniques to optimize a code review
  - Reflect upon how these techniques could be deployed in your day-to-day working environment
keypoints:
  - See efficient techniques for giving effective code reviews
---


##  Techniques to ensure maximum efficiency


Code reviews can be long, but just like any other process can be optimized. Here are some code review best practices that can be implemented in your company.


### Add the time cost to the project plan
Code reviews can potentially take a lot of time. Keep in mind, that code review is just like agile development – it might feel like we add extra time, but it pays off later with better quality! A rule of thumb is to keep the suggested changes short (not more than 500 lines of code), so the person performing the review to be effective in the process.

The code reviewing process should be added on top of a project’s time estimation. Just like the time spent on the development itself, it’s tough (for every developer) to estimate how much time the review process will take. The time spent on a code review will grow with the task complexity, just like the feature implementation.

#### Set a live meeting in case of significant changes
If a PR is huge (shouldn’t be, but it happens), it can cost a lot of time to ping-pong online discussion with hundreds of comments. In this case, it could be better to set up a desk meeting where the code author explains other changes.


### Consider a positive language style
It is hard to perform neutral feedback in written language. Especially, if the written language is not your mother tongue. The tone of the code review can greatly influence the morale of the person being reviewed. Reviews with a harsh tone can contribute to a feeling of a hostile environment with  microaggressions. Opinionated language can turn people defensive and spark a heated discussion. A professional and positive tone can contribute to a more inclusive environment. People in these environments are open to constructive feedback and code reviews can instead trigger healthy and lively discussions.

Good code reviews ask open-ended questions instead of making strong or opinionated statements. They offer alternatives and possible workarounds that might work better for the situation without insisting those solutions are the best or only way to proceed. These reviews assume the reviewer might be missing something and ask for *clarification* instead of *correction*.

Better code reviews are also empathetic. They know that the person writing the code spent a lot of time and effort on this change. These code reviews are kind and unassuming. They applaud nice solutions and are all-around positive.



### Have a plan for disagreement
A code review, just like any discussion, could cause conflicts between developers. Also, it’s based on giving feedback, which is very hard for both reviewer (to do it with empathy) and the author (to accept criticism).

One source of conflict is when there are two different decisions, and parties don’t want to give up the idea. However, a lot of decisions have been made already – but they are lost in time. The code style guide has been mentioned before – this is an excellent example because no one will argue about “tabs vs. spaces” if this has been officially decided and written in the project documentation.


#### Two reviewers are better than one for disagreements
It’s not easy to find a consensus if there are two different opinions on the table and two people who have to agree on one of them. Despite how strict computer science can be, there are a ton of problems which solutions based on very non-scientific premises and guesses. Both sides can argue and even fight to prove one’s right. Not many developers have in mind business problems (time!), so they can waste a lot of resources on pointless discussions.

Another problem could be the personal character of team members. Sometimes people get frustrated because they can’t push opinion against someone with more communication skills.

To solve this problem, it only takes to introduce a third developer (typically a second reviewer), who will tip the balance and eventually agree only with one of the parties (or propose another solution).

### Make code review a priority in the team
Code review is a blocker for merging a feature, so if a developer requires some piece of code to be available for the new feature, it could be a problem. Required changes can be manually merged into the new feature before the start, but it can lead to code conflicts, on the other hand, the developer will wait to do nothing until changes are made.

As you know, blockers should be found as soon as possible and solved as quickly as possible, so the work is as smooth as it gets. It is essential to make developers understand that pending code reviews (and overall pull requests) are actually more important than their own ongoing work (of course in a reasonable way, critical fixes are even more critical). A suggestion is to make a habit of checking for pending PR or code reviews in situations where the focus is lost anyway. This could be when someone is: starting to work in the morning, going back from lunch, going back from a coffee break, or going back from a meeting.

Checking for new code review requests shouldn’t be too hard – it can be done in several ways. A developer can browse Github for open PRs with an “awaiting review from you” status. Also, each developer will probably get an email with a Code Review assignment. You can easily connect Github to Slack so that each open PR will be posted to the channel.

### Establish code review rules and write them down
The code review process, like any other process, can use some rules, especially in bigger and more complex projects. More developers in the team mean diverse experiences and practices. It is good but sometimes can slow down the effectiveness of work.

So, each team should establish some set of rules and write them down (don’t miss this point!). There are two significant benefits of making this happen:

New developer on the board requires education about existing rules. Don’t waste time explaining every time the same things. It’s also frustrating to the new guy that he/she is corrected many times, instead of first reading how things are done in the team. In case of conflicts or misunderstandings, there is a single, living source of truth that can be referenced.
Some code review best practices:
- Only comment author can resolve comment – if the code was corrected or after a discussion the author decides to fix it.
- Don’t mention the same problem many times. Don’t bloat the code, say it once and ask to fix it everywhere.
- If there are pending, not resolved comments, the assignee is a code author who should fix or comment back.
- If there are discussions commented on by the code author, the assignee is the reviewer, who should continue a discussion or resolve comments and approve.
- Use the GitHub labels to mark what actions should be next – e.g. “ready for review” “ready for the QA” etc.


### Ensure that the pull requests are good
An inseparable part of code review is a pull request. The review is done on changes someone request to “pull” to the main branch. If the PR is good, a code review should be easy and fast. If PR is bad – code review will be exhausting, long, and “no one will have time to do it.”

The main rule of good PR is to keep it short. Two hundred lines of code are easy to understand and to find problems. Two thousand lines are not. The cognitive load increase is exponential relative to the number of changes done in the request. Short PR can be checked during a coffee break – a long PR will cost literally many hours, and code review quality will decrease because the reviewer will be eventually too tired and confused to keep quality for a long time.

By ensuring developers to spend a little extra time to create a good quality PR request, will return in many hours of reviewing work.

### Automate as much as possible
Developers prefer automating over manual and repetitive tasks. Code review might stand between code and human, but still, a lot can be delegated to the machine.

### Set continuous integration pipelines
First of all, PR should trigger a continuous integration (CI) pipeline with tests and builds. This step runs a few minutes and catches a lot of problems that might be detected by the reviewer. Well written tests should cover a lot of quality problems, but without set CI, someone can merge it even if tests fail.

Connect the CI pipeline tool to Github and block the possibility to merge until all checks pass. Don’t waste developers’ time to check code that will not even build.

### Favor a reviewer who knows the problem
Probably there is not much sense in asking a frontend developer to check the backend code. If the team is big enough to choose from reviewers, it’s an excellent way to improve code quality. Some developers will better understand domain knowledge; some of them will specialize in some narrow tech problems. They will better fit reviews where they can give a lot of valuable feedback.

Modern git services make this easier by detecting and suggesting relevant reviewers based on historical changes or code owners.
