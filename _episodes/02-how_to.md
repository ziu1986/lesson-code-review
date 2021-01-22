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


##  Techniques to ensure an efficient code review

If code reviews are performed without a plan they quickly become time-consuming. Here are some code review best practices to ensure maximum efficiency.


### Add the time cost to the project plan
Even though the process of doing a code review can be optimized, including them in your workflow will always require time. Keep in mind, that a code review is just like agile development – it might feel like we add extra time, but it pays off later with better overall quality. A rule of thumb is to keep the suggested changes short (not more than 500 lines of code), so the person reviewing can be effective in the process.

Furthermore, the code reviewing process should be added on top of a project’s time estimation. The time spent on a code review will grow with the task complexity, just like the feature implementation.

- #### Live meetings for significant changes
Sometimes a PR will be huge. To avoid an online ping-pong discussion with hundreds of comments it is a good idea to arrange a live, or even physical meeting, meeting between the author and reviewers.


### Keep a positive language style
It is hard to perform neutral feedback in written language. Especially, if the written language used is not your mother tongue. The tone of the code review can greatly influence the morale of the person being reviewed. Reviews with a harsh tone can easily be interpreted as aggressive comments. Opinionated language can turn people defensive and spark heated discussions. A professional and positive tone can contribute to a more inclusive environment with constructive feedback.

To keep the attitude positive it is better to ask open-ended questions instead of making strong or opinionated statements. By asking for *clarifications* instead of *corrections* one could change from a negative to a positive language style. Also, keep in mind that the author of the purposed code has spent a lot of time and effort on this change.

### Have a plan for disagreement
As in any other discussion, disagreements could raise conflicts between developers. Giving feedback is hard for both reviewer (to do it with empathy) and the author (to accept criticism). If a code style guide and a procedure to resolve the conflict already exist (to avoid an argument about “tabs vs. spaces”) a lot of time can be saved.

- #### Two reviewers are better than one for disagreements
It’s not easy to find a consensus if there are two different opinions on the table and two people who disagree. By introducing a third person one can take a decision (maybe a new solution) and move on.

### Avoid blockers and prioritize the team
Blockers should be found as soon as possible and solved as quickly as possible, so the work can be as smooth as it gets. It is essential to make developers understand that pending code reviews (and overall pull requests) are more important than their ongoing work (of course in a reasonable way, critical fixes are even more critical). A suggestion is to make a habit of checking for pending PR or code reviews in situations where the focus is lost anyway. This could be when someone is: starting to work in the morning, going back from lunch, going back from a coffee break, or going back from a meeting. Checking for new code review requests shouldn’t be too hard – it can be done in several ways. A developer can browse Github for open PRs with an “awaiting review from you” status. Also, each developer will probably get an email with a Code Review assignment. You can easily connect Github to Slack so that each open PR will be posted to the channel.

### Establish code review rules and write them down
The code review process, like any other process, can use some rules, especially in bigger and more complex projects. More developers in the team mean diverse experiences and practices. It is good but sometimes can slow down the effectiveness of work.

So, each team should establish some set of rules and write them down. There are two significant benefits of making this happen:

- Don’t waste time explaining every time the same things. A new developer in the team needs to be educated in the existing rules. It’s  frustrating to the new person if he/she is corrected many times when it is not necessary. He/she could instead read  how things are done in the team.
- In case of conflicts or misunderstandings, there is a single, living source of truth that can be referenced.

Some suggestions for code review rules:
- Only the comment author can resolve a comment – if the code was corrected, or after a discussion, if the author decides to fix it.
- Don’t mention the same problem many times. Don’t bloat the code, say it once and ask the author to fix it everywhere.
- If there are pending, non-resolved comments, the assignee is a code author who should fix this or comment back.
- If there are discussions commented on by the code author, the assignee is the reviewer, who should continue a discussion or resolve comments and approve.
- Use the GitHub labels to mark what actions should be next – e.g. “ready for review” “ready for the QA” etc.


### Ensure good pull requests
By ensuring developers spend a little extra time to create a good quality PR request, a team can decrease many hours of reviewing work. An inseparable part of code review is a PR. The review is done on changes someone request to “pull” to the main branch. If the quality PR is good, a code review should be easy and fast. If PR is bad – the code review process quickly becomes exhausting, long, and “no one will have time to do it.”

The main rule to have a good PR is to keep it short. For two hundred lines of code, it is easy to understand the purpose and overview of the changes, for two thousand lines it is not. The cognitive load increase exponentially, relative to the number of changes done in the request. Short PRs can be checked during a coffee break – a long PR can cost many hours. The quality of the code review quality will also decrease because the reviewer will be eventually too tired and confused.

### Automate the reviewing task as much as possible
A PR could trigger a continuous integration (CI) pipeline with tests and builds. This step runs a few minutes and catches a lot of problems that might be detected by the reviewer. Well written tests should cover a lot of quality problems, but without set CI, someone can merge it even if tests fail. The CI pipeline tool can even be integrated into Github and block the possibility to merge until all checks pass. Don’t waste developers’ time to check code that will not even build.

### Favor the right person for the right problem
There is probably not much sense in asking a frontend developer to check the backend code. If the team is big enough to choose from reviewers with different areas of expertise, it’s an excellent way to improve code quality. Some developers will better understand domain knowledge; some of them will specialize in narrow tech problems. Modern GitHub services make the process of assigning/suggesting a relevant reviewer.
