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


### 4. Create a branch `somefeature`

Create a branch from the current `main`:

```
$ git checkout -b somefeature
```


### 5. Update the `imporvements.py` file to use a library

- You receive a comment from your colleague that it exist a library for python called `numpy`. This library already has implemented functionalities for calculating the mean of an array. Since you know that it is a good idea to use existing code you decide to change the `compute_mean` function with the library function.

- **Think for yourself**. What you would do to if you where to use the `numpy` library instead of your own function. If you do not know you can copy the following code inside the file



> > ## One solution with `numpy`
> >
> > ``` python
> > import pandas as pd
> > from matplotlib import pyplot as plt
> > import numpy as np
> >
> > def plot_data(data, mean, xlabel, ylabel, file_name):
> >    plt.plot(data, "r-")
> >    plt.xlabel(xlabel)
> >    plt.ylabel(ylabel)
> >    plt.axhline(y=mean, color="b", linestyle="--")
> >    plt.savefig(file_name)
> >    plt.clf()
> >
> >
> > def read_data(file_name, nrows, column):
> >    data = pd.read_csv(file_name, nrows=nrows)
> >    return data[column]
> >
> > for num_measurements in [25, 100, 500]:
> >
> >    temperatures = read_data(
> >        file_name="data/temperatures.csv",
> >        nrows=num_measurements,
> >        column="Air temperature (degC)",
> >    )
> >
> >    mean = np.mean(temperatures)
> >
> >    plot_data(
> >        data=temperatures,
> >        mean=mean,
> >        xlabel="measurements",
> >        ylabel="air temperature (deg C)",
> >        file_name=str(num_measurements)+'.png',
> >    )
> > ```
> {: .solution}
{: .challenge}




### 5. Stage and commit the change

```
$ git add improvements.py
$ git commit
```


### 6. Push your change as a new branch

```
$ git push origin -u somefeature
```


### 7. Submit a pull request

Submit a pull request from your branch towards the `master` branch in the repository of the administrator through the web interface of GitHub.

Assign a member of your team to review the change you suggested. Wait in this step until you are assigned to review the changes of someone else in your team.

### 8. Review the pull request

Look through the pull request, and decide if you would like to:
- Comment
- Approve
- Request changes

And submit the review. If you have no comments you can write LGTM (looks good to me), a polite way to say that you accept the purposed changes.

**Do not accept the pull-request!** Since you are several people performing the same exercise you will see a lot of conflicts if everyone actually merge the code into the `main` branch. The point with the exercise is to explore the review function of GitHub.


> ## (Optional) Exercise/discussion: Add the median of the measurements to the plots?
>
> This exercise is optional and you can do it if you have time to repeat the steps you did previously by yourself.
>
> Go through the steps 1-8 again without following the detailed instructions. This time you add the median of the data to the plot, by using the numpy library.
> > ## One solution with `numpy`
> >
> > ``` python
> > import pandas as pd
> > from matplotlib import pyplot as plt
> > import numpy as np
> >
> > def plot_data(data, mean, median, xlabel, ylabel, file_name):
> >    plt.plot(data, "r-")
> >    plt.xlabel(xlabel)
> >    plt.ylabel(ylabel)
> >    plt.axhline(y=mean, color="b", linestyle="--")
> >    plt.axhline(y=median, color="g", linestyle="--")
> >    plt.savefig(file_name)
> >    plt.clf()
> >
> >
> > def read_data(file_name, nrows, column):
> >    data = pd.read_csv(file_name, nrows=nrows)
> >    return data[column]
> >
> > for num_measurements in [25, 100, 500]:
> >
> >    temperatures = read_data(
> >        file_name="data/temperatures.csv",
> >        nrows=num_measurements,
> >        column="Air temperature (degC)",
> >    )
> >
> >    mean   = np.mean(temperatures)
> >    median = np.median(temperatures)
> >
> >    plot_data(
> >        data=temperatures,
> >        mean=mean,
> >        median=median,
> >        xlabel="measurements",
> >        ylabel="air temperature (deg C)",
> >        file_name=str(num_measurements)+'_median.png',
> >    )
> > ```
> {: .solution}
{: .challenge}
