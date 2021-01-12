---
layout: episode
title: using the GitHub web interface
teaching: 15
exercises: 40
questions:
  - How can we give feedback through GitHub?
objectives:
  - Repeat how to collaborate using a centralized workflow.
  - Use functionalities of the web interface of GitHub
keypoints:
  - Code review and GitHub
  - "`origin` refers to where you cloned from (but you can relocate it)."

---

## Code review exercise

In this exercise we will practice code reviews and the collaborative centralized workflow in small
groups.  We'll discuss a number of
typical pitfalls.


> ## Exercise preparation
>
> **The helper (administrator)** generates a new repository
>   from the template [template-centralized-workflow-exercise](https://github.com/coderefinery/template-centralized-workflow-exercise) add
>   called `code-review-exercise` (There is no need to tick *"Include all branches"* for this exercise)
> - Then **everyone in your group** needs their GitHub account to be added as collaborator to the exercise repository:
>   - Participants give their GitHub usernames to their administrator (in their respective group, in online workshops you can use the Zoom chat for private communication within the breakout room).
>   - Administrator gives the other group members the newly created GitHub repository URL.
>   - Administrator adds participants as collaborators to their project (Settings → Manage Access → Invite a collaborator).
>   - Group members need to accept the invitation. GitHub emails you an invitation link, but if you don't receive it
>     you can go to your GitHub notifications in the top right corner. The administrator can also "copy invite link"
>     and share it within the group.
{: .prereq}

> ## Watching and unwatching repositories
>
> - Now that you are a collaborator, you get notified about new issues and pull
>   requests via email.
> - If you do not wish this, you can "unwatch" a repository (top of the project page).
> - However, we recommend watching repositories you are interested in. You can learn things from experts just by
>   watching the activity that come through.
{: .callout}

> ## Exercise description
>
> - Helper prepares an exercise repository (see above) - this will take 10 minutes or so.
> - The exercise group works in small steps 1-8 (15-20 minutes). The point is to do a code review through GitHub.
> - Before we start with the exercise, instructor mentions all steps and explains what happens during a `git clone`.
{: .challenge}


### 1. Fork your administrator's group repository

- Fork the repository on GitHub

 This is how it looks after we fork:

*central*: ![]({{ site.baseurl }}/img/forking/github-remote-01.svg)

*fork*: ![]({{ site.baseurl }}/img/forking/github-remote-01.svg)



> > ## Recap of forks
> >
> > - A fork is basically a (bare) clone.
> > - The upstream repo and the fork are in principle independent repositories.
> > - When forking we copy all commits, all branches.
> >
> > After we clone the fork we have three in principle independent repositories:
> >
> > *central*: ![]({{ site.baseurl }}/img/forking/github-remote-01.svg)
> >
> > *fork*: ![]({{ site.baseurl }}/img/forking/github-remote-01.svg)
> >
> > *local*: ![]({{ site.baseurl }}/img/forking/github-local-01.svg)
> {: .solution}
{: .challenge}

### 2. Clone your administrator's group repository

- Type the following command in a terminal
```
$ git clone https://https://github.com/sunnivin/module-based-type-along modular-based-type-along centralized-workflow-exercise
```

Where you replace `sunnivin` by the namespace of the repository administrator.


### 3. Step into the newly created directory

```
$ cd centralized-workflow-exercise
```

Try to find out where this repository was cloned from using `git remote -v`.


### 4. Create a branch `yourname-somefeature` pointing at your commit

Create a branch from the current `master`:

```
$ git branch yourname-somefeature
$ git checkout yourname-somefeature
```

The `yourname-` prefix has no special meaning here (not like `origin/`): it is just part of a
branch name to indicate who made it.


### 5. Update the `imporvements.py` file to use libraries

- Think for yourself a little about what you would do to if you where to use the `numpy` library instead of your own function. If you do not know you can copy the following code inside the file

``` python
import pandas as pd
from matplotlib import pyplot as plt


def plot_data(data, mean, xlabel, ylabel, file_name):
    plt.plot(data, "r-")
    plt.xlabel(xlabel)
    plt.ylabel(ylabel)
    plt.axhline(y=mean, color="b", linestyle="--")
    plt.savefig(file_name)
    plt.clf()


def compute_mean(data):
    mean = sum(data) / len(data)
    return mean


def read_data(file_name, nrows, column):
    data = pd.read_csv(file_name, nrows=nrows)
    return data[column]


for num_measurements in [25, 100, 500]:

    temperatures = read_data(
        file_name="data/temperatures.csv",
        nrows=num_measurements,
        column="Air temperature (degC)",
    )

    mean = compute_mean(temperatures)

    plot_data(
        data=temperatures,
        mean=mean,
        xlabel="measurements",
        ylabel="air temperature (deg C)",
        file_name=str(num_measurements)+'.png',
    )
```



### 5. Stage and commit the change

```
$ git add improvements.py
$ git commit
```


### 6. Push your change as a new branch

```
$ git push origin -u yourname-somefeature
```


### 7. Submit a pull request

Submit a pull request from your branch towards the `master` branch in the repository of the administrator through the web interface of GitHub.

Assign a member of your team to review your changes. Wait until you are assigned to review the changes of someone else in your team.

### 8. Review the pull request

Look through the pull request, and decide if you would like to:
- Comment
- Approve
- Request changes

And submit the review. If you have no comments you can write LGTM (looks good to me), a polite way to say that you accept.

**Do not accept the pull-request!** Since you are several people performing the same exercise you will see a lot of conflicts if everyone actually merge the code into the `main` branch. The point with the exercise is to explore the review function of GitHub.


> ## Exercise/discussion: Why did we create a feature branch `yourname-somefeature`?
>
> This exercise is done in groups of 4-5 persons and can be done through a discussion only.
>
> Pushing directly to the main branch is perfectly fine for simple personal projects -
> the pull-request workflows covered here are for larger projects or for collaborative development.
> Guidelines for simpler workflows are given in the
> [how much git is necessary?](https://coderefinery.github.io/git-intro/14-level/) episode of the git-intro lesson.
>
> In collaborative development, whenever we update our repository we create a new branch
> and create a pull-request. Let's now imagine that everyone in your group makes a new change (create a new file)
> but without creating a new branch.
>
> 1. You all create a new file in the master branch, stage and commit your change locally.
> 2. Try to push the change to the upstream repository:
>
> ```
> $ git push origin master
> ```
> You probably see something like this:
>
> ```shell
> $ git push
> To https://github.com/user/repo.git
>  ! [rejected]        master -> master (non-fast-forward)
> error: failed to push some refs to 'https://github.com/user/repo.git'
> To prevent you from losing history, non-fast-forward updates were rejected
> Merge the remote changes (e.g. 'git pull') before pushing again.  See the
> 'Note about fast-forwards' section of 'git push --help' for details.
> ```
>
> - The push only worked for one participant.
> - Discuss why push for everybody else in this group was rejected?
>
> > ## Solution
> >
> > The push for everyone except one person fails because they are missing one
> > commit in their local repository that exists on the remote. They will first
> > need to pull the remote changes before pushing their own, which will usually
> > result in a merge commit.
> {: .solution}
{: .challenge}



> ## Discussion
>
> ### Naming
>
> - In GitLab or BitBucket these are named **merge requests**, not **pull requests**.
> - Which one do you feel is more appropriate and in which
>   context? (The name **pull request** may make more sense in the forking workflow: next episode).
> - It can be useful to think of them as **change proposals**.
>
> ### Pull requests are from branch to branch
>
> - They originate from a source branch and are directed towards a branch.
> - Not from commit to branch.
> - Pull requests create new commits on the target branch.
> - They do not create new branches.
>
> ### Pull requests can be used for code review
>
> - Pull requests are like change proposals.
> - We recommend that pull requests are reviewed by someone else in your group.
> - In our example everyone has write access to the "central" repository.
>
> ### Code review and protected branches
>
> - A good setting is to make the `master` or `main` branch **protected** and all changes to it have to go
>   through code review.
> - Centralized workflow with protected branches is a good setup for many projects.
>
{: .discussion}



<!-- --- -->
<!-- layout: episode -->
<!-- title: Give a code review -->
<!-- teaching: 10 -->
<!-- exercises: 50 -->
<!-- questions: -->
<!--   - Learn techniques for a generalized code development -->
<!--   - What are the pros and cons of choosing a general code design? -->
<!-- objectives: -->
<!--   - Do a modular based code development following a template -->
<!--   - Get comfortable with the forking workflow -->
<!-- keypoints: -->
<!--   - Experience difficulties in developing one-size-fit-all strategy -->
<!--   - Repeat basic git-commands -->
<!--   - Reflect on a typical development workflow in a small project -->
<!-- --- -->

<!-- ## Modular exercise with GitHub and Python -->
<!-- In this exercise, you will incrementally improve a python script for plotting some data together. It is a type-along/demo where we discuss and experience aspects of (un)modular code development. We will focus on the “why”, not on the “how”. -->

<!-- ### Data -->
<!-- The file temperatures.csv contains hourly air temperature measurements for the time range November 1, 2019 12:00 AM - November 30, 2019 11:59 PM for the observation station “Vantaa Helsinki-Vantaan lentoasema”. -->

<!-- Data obtained from https://en.ilmatieteenlaitos.fi/download-observations#!/ on 2019-12-09. -->

<!-- ### Initial goal -->
<!-- Our initial goal for this exercise is to plot a series of temperatures for 25 measurements and to compute and plot the arithmetic mean. We imagine that we assemble a working script from various StackOverflow recommendations and arrive at this answer: -->



<!-- ### **Step F**: improve to more stateless functions -->
<!-- After digesting the material in this workshop you realize that you can do one last effort of improving your script by making your functions more stateless (aiming for pure functions here!) -->

<!-- - Update the `improvement.py` file by copying the following code: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->


<!-- def plot_data(data, mean, xlabel, ylabel, file_name): -->
<!--     plt.plot(data, "r-") -->
<!--     plt.xlabel(xlabel) -->
<!--     plt.ylabel(ylabel) -->
<!--     plt.axhline(y=mean, color="b", linestyle="--") -->
<!--     plt.savefig(file_name) -->
<!--     plt.clf() -->


<!-- def compute_mean(data): -->
<!--     mean = sum(data) / len(data) -->
<!--     return mean -->


<!-- def read_data(file_name, nrows, column): -->
<!--     data = pd.read_csv(file_name, nrows=nrows) -->
<!--     return data[column] -->


<!-- for num_measurements in [25, 100, 500]: -->

<!--     temperatures = read_data( -->
<!--         file_name="data/temperatures.csv", -->
<!--         nrows=num_measurements, -->
<!--         column="Air temperature (degC)", -->
<!--     ) -->

<!--     mean = compute_mean(temperatures) -->

<!--     plot_data( -->
<!--         data=temperatures, -->
<!--         mean=mean, -->
<!--         xlabel="measurements", -->
<!--         ylabel="air temperature (deg C)", -->
<!--         file_name=str(num_measurements)+'.png', -->
<!--     ) -->
<!-- ``` -->




<!-- ### Our task -->

<!-- Our collaborators ask us to continue the code development to generalize the coding steps. Once we get this working for 25 measurements, our task changes to also plot the first 100 and the first 500 measurements in two additional plots. -->

<!-- This example is in Python but we will try to see “through” the code and focus on the bigger picture and hopefully manage to imagine other languages in their place. For the Python experts: we will not see the most elegant Python. -->



<!-- --- -->

<!-- > ## Exercise preparation -->
<!-- > -->
<!-- > **Helpers in breakout-rooms**: -->
<!-- > - Create an exercise repository by -->
<!-- >   [generating from a template](https://help.github.com/en/articles/creating-a-repository-from-a-template) -->
<!-- >   using this template: <https://github.com/sunnivin/module-based-type-along> -->
<!-- > - In this case, we **do not add collaborators** to the repository (this is the point of this example). -->
<!-- > - Share the link to the newly created repository in the shared document with your group. -->
<!-- > -->
<!-- > **Learners in breakout-rooms**: -->
<!-- > - Fork the helper's newly created repository and clone the fork so you can work on your global copy. -->
<!-- {: .prereq} -->

<!-- > ## Exercise: modular type along with GitHub -->
<!-- > -->
<!-- > We will collaboratively develop a module based python code -->
<!-- > -->
<!-- > Objectives: -->
<!-- > - Repeat GitHub workflows (fork, commit, etc.) -->
<!-- > - Learn the advantages of modular based coding. -->
<!-- > -->
<!-- > Exercise: -->
<!-- > - Helper prepares an exercise repository (see above; this will take 5-10 minutes). -->
<!-- > - **The exercise group works on steps A-F** (50 minutes). -->
<!-- > - After step F you can return to the main room. Please ask questions. -->
<!-- {: .challenge} -->



<!-- ### **Step A**: Fork and clone -->


<!-- Wait for the helper to share the repository for this exercise in the group chat. -->
<!-- - Fork the helper's repository and  create a local clone. -->

<!-- - cd into the folder where the local repository is and create the branch `module-based-development`. Through all this exercise the variable $HOME is referring to the top folder of the repository. -->

<!-- - Run the initial python script from the $HOME folder: -->
<!-- ``` shell -->
<!-- $ python src/initial.py -->
<!-- ``` -->

<!-- - Verify that the file `25.png` is created in $HOME. -->


<!-- ### **Step B**: improve the plot -->
<!-- Your supervisor ask you to improve the plot by adding labels to the plot. -->

<!-- - Create a file `src/improvement.py` and add it to the repository. -->

<!-- - Add labels to the plot by adding the following lines to `improvement.py`: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->


<!-- plt.xlabel('measurements') -->
<!-- plt.ylabel('air temperature (deg C)') -->


<!-- num_measurements = 25 -->

<!-- # read data from file -->
<!-- data = pd.read_csv('data/temperatures.csv', nrows=num_measurements) -->
<!-- temperatures = data['Air temperature (degC)'] -->

<!-- # compute statistics -->
<!-- mean = sum(temperatures)/num_measurements -->

<!-- # plot results -->
<!-- plt.plot(temperatures, 'r-') -->
<!-- plt.axhline(y=mean, color='b', linestyle='--') -->
<!-- plt.savefig('25.png') -->
<!-- plt.clf() -->
<!-- ``` -->
<!-- - Run the improved python script from the top folder in the repository: -->
<!-- ``` shell -->
<!-- $ python src/improvement.py -->
<!-- ``` -->
<!-- - Verify that the axis are added in the file `25.png`. -->

<!-- - Stage and commit the changes in `improvement.py`. -->


<!-- ### **Step C**: increase the number of plotted measurements -->
<!-- Your supervisor now tells you to make similar kinds of plots for 100 and 500 measurements as well. Since you know that code duplication should be avoided you decide to change the number of plots made of the measurements with a loop. -->

<!-- - Update `improvement.py` by copying in the following code.  The plots will now be generated with a for-loop over the variable `num_measurements`: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->

<!-- plt.xlabel('measurements') -->
<!-- plt.ylabel('air temperature (deg C)') -->

<!-- for num_measurements in [25, 100, 500]: -->

<!--     # read data from file -->
<!--     data = pd.read_csv('data/temperatures.csv', nrows=num_measurements) -->
<!--     temperatures = data['Air temperature (degC)'] -->

<!--     # compute statistics -->
<!--     mean = sum(temperatures)/num_measurements -->

<!--     # plot results -->
<!--     plt.plot(temperatures, 'r-') -->
<!--     plt.axhline(y=mean, color='b', linestyle='--') -->
<!--     plt.savefig(str(num_measurements)+'.png') -->
<!--     plt.clf() -->
<!-- ``` -->
<!-- - Run `improvement.py` again and verify that the files `25.png`, `100.png` and `500.png` are created. Why are the axis labels only present for the file `25.png`? -->

<!-- - Stage and commit the changes in `improvement.py`. -->


<!-- ### **Step D**: abstracting the plotting part by introducing a function -->
<!-- A colleague advises you to abstract the plotting part into a function to divide the work into modules. -->

<!-- - Update the `improvement.py` file by copying the following code: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->

<!-- def plot_temperatures(temperatures): -->
<!--     plt.plot(temperatures, 'r-') -->
<!--     plt.axhline(y=mean, color='b', linestyle='--') -->
<!--     plt.xlabel('measurements') -->
<!--     plt.ylabel('air temperature (deg C)') -->
<!--     plt.savefig(str(num_measurements)+'.png') -->
<!--     plt.clf() -->


<!-- for num_measurements in [25, 100, 500]: -->

<!--     # read data from file -->
<!--     data = pd.read_csv('data/temperatures.csv', nrows=num_measurements) -->
<!--     temperatures = data['Air temperature (degC)'] -->

<!--     # compute statistics -->
<!--     mean = sum(temperatures)/num_measurements -->

<!--     # plot results -->
<!-- #   plt.plot(temperatures, 'r-') -->
<!-- #   plt.axhline(y=mean, color='b', linestyle='--') -->
<!-- #   plt.savefig(f'{num_measurements}.png') -->
<!-- #   plt.clf() -->
<!--     plot_temperatures(temperatures) -->
<!-- ``` -->
<!-- - **Wait for the other members of the break-out room and discuss this point**: -->
<!--   - What would we expect before running this code?  (Hint: how are the variables defined?) -->
<!--   - Do you see any problems with this solution? (Hint: what would happen if the code is copy-pasted into another file?) -->


<!-- - Run the modified `improvement.py` script. -->

<!-- - Stage and commit the changes in `improvement.py`. -->


<!-- ### **Step E**: small improvements -->
<!-- After looking at the script you realize that you can functionalize all the parts of your script and use a for-loop. -->

<!-- - Update the `improvement.py` file by copying the following code: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->


<!-- def plot_data(data, xlabel, ylabel): -->
<!--     plt.plot(data, 'r-') -->
<!--     plt.xlabel(xlabel) -->
<!--     plt.ylabel(ylabel) -->
<!--     plt.axhline(y=mean, color='b', linestyle='--') -->
<!--     plt.savefig(str(num_measurements)+'.png') -->
<!--     plt.clf() -->


<!-- def compute_statistics(data): -->
<!--     mean = sum(data)/num_measurements -->
<!--     return mean -->


<!-- def read_data(file_name, column): -->
<!--     data = pd.read_csv(file_name, nrows=num_measurements) -->
<!--     return data[column] -->


<!-- for num_measurements in [25, 100, 500]: -->

<!--     temperatures = read_data(file_name='data/temperatures.csv', column='Air temperature (degC)') -->

<!--     mean = compute_statistics(temperatures) -->

<!--     plot_data(data=temperatures, xlabel='measurements', ylabel='air temperature (deg C)') -->
<!-- ``` -->
<!-- - **Wait for the other members of the break-out room and discuss this point**: -->
<!--   - What will now happen if the functions are copy-pasted into another project/script? (Hint: how is for instance `num_measurements` declared?) -->

<!-- - Run the modified `improvement.py` script. -->

<!-- - Stage and commit the changes in `improvement.py`. -->



<!-- ### **Step F**: improve to more stateless functions -->
<!-- After digesting the material in this workshop you realize that you can do one last effort of improving your script by making your functions more stateless (aiming for pure functions here!) -->

<!-- - Update the `improvement.py` file by copying the following code: -->

<!-- ``` python -->
<!-- import pandas as pd -->
<!-- from matplotlib import pyplot as plt -->


<!-- def plot_data(data, mean, xlabel, ylabel, file_name): -->
<!--     plt.plot(data, "r-") -->
<!--     plt.xlabel(xlabel) -->
<!--     plt.ylabel(ylabel) -->
<!--     plt.axhline(y=mean, color="b", linestyle="--") -->
<!--     plt.savefig(file_name) -->
<!--     plt.clf() -->


<!-- def compute_mean(data): -->
<!--     mean = sum(data) / len(data) -->
<!--     return mean -->


<!-- def read_data(file_name, nrows, column): -->
<!--     data = pd.read_csv(file_name, nrows=nrows) -->
<!--     return data[column] -->


<!-- for num_measurements in [25, 100, 500]: -->

<!--     temperatures = read_data( -->
<!--         file_name="data/temperatures.csv", -->
<!--         nrows=num_measurements, -->
<!--         column="Air temperature (degC)", -->
<!--     ) -->

<!--     mean = compute_mean(temperatures) -->

<!--     plot_data( -->
<!--         data=temperatures, -->
<!--         mean=mean, -->
<!--         xlabel="measurements", -->
<!--         ylabel="air temperature (deg C)", -->
<!--         file_name=str(num_measurements)+'.png', -->
<!--     ) -->
<!-- ``` -->

<!-- - Run the modified `improvement.py` script. -->

<!-- - Stage and commit the changes in `improvement.py`. -->

<!-- - Display your GitHub history and reflect around the comments you have written in  your log. Would you be able to follow the ideas of your history log if you were just reading the commit messages? -->
