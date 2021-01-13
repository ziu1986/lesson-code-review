---
layout: episode
title: more steps to reach a standard
teaching: 20
exercises: 0
questions:
  - Why should you follow a generalized workflow?
objectives:
  - Understand standard code organization of the project folder
  - See one standard organization
keypoints:
  - See how a repository can be changed to follow a standard

---

## Code review demo

In this episode you will see a repository that is organized in a more standard structure than we did in the last exercise (episode 4). This part of the session is organized in the main zoom-room, but if you are interested you are more than welcome to perform the steps done by the instructor.


### 1. Improve the plotting function to follow LaTeX standard

- If you were to publish the plots generated from the Python code we used in episode 4 they would probably not be approved. There are no labels in the plot, and if you were writing that paper in LaTeX most journals will require that you keep the LaTeX-font and styles in your plot.



>
> > ## One solution: Change to LaTeX-style and add labels
> >
> > ``` python
> > import pandas as pd
> > from matplotlib import pyplot as plt
> > import numpy as np
> >
> > #--- Set plot settings to match LaTeX<3
> > def latex_plot():
> >     plt.rcParams['figure.figsize'] = (16, 16)
> >     plt.rcParams['font.size'] = 45
> >     plt.rcParams['font.family'] = 'serif'
> >     plt.rcParams['axes.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['axes.titlesize'] = plt.rcParams['font.size']
> >     plt.rcParams['legend.fontsize'] = plt.rcParams['font.size']
> >     plt.rcParams['xtick.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['ytick.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['xtick.major.size'] = 3
> >     plt.rcParams['xtick.minor.size'] = 3
> >     plt.rcParams['xtick.major.width'] = 1
> >     plt.rcParams['xtick.minor.width'] = 1
> >     plt.rcParams['ytick.major.size'] = 3
> >     plt.rcParams['ytick.minor.size'] = 3
> >     plt.rcParams['ytick.major.width'] = 1
> >     plt.rcParams['ytick.minor.width'] = 1
> >     plt.rcParams['legend.frameon'] = False
> >     plt.rcParams['axes.linewidth'] = 1.5
> >
> >     # --- Use latex-style on text in plots
> >     plt.rcParams['text.usetex'] = True
> >
> >     # --- Custumize the length of the labels
> >     plt.rcParams["legend.labelspacing"] = 0.2
> >     plt.rcParams["legend.handlelength"] = 1.0
> >     plt.rcParams["legend.borderaxespad"] = 0.01
> >
> >     # --- Ignore warnings for generated plot
> >     plt.rcParams.update({'figure.max_open_warning': 0})
> >
> >     plt.linewidth=17.0
> >     font_size_plot = 20
> >
> >     return font_size_plot
> >
> > def plot_data(data, data_label, mean, mean_label, median, median_label, xlabel, ylabel, file_name):
> >    plt.plot(data, "r-", label=data_label)
> >    plt.xlabel(xlabel)
> >    plt.ylabel(ylabel)
> >    plt.axhline(y=mean, color="b", linestyle="--", label=mean_label)
> >    plt.axhline(y=median, color="g", linestyle=":", label=median_label)
> >    plt.legend()
> >    plt.savefig(file_name)
> >    plt.clf()
> >
> >
> > def read_data(file_name, nrows, column):
> >    data = pd.read_csv(file_name, nrows=nrows)
> >    return data[column]
> >
> > # --- Add LaTeX-style plotting
> > latex_plot()
> >
> > # -- Set plot labels
> > data_label    = "Temp"
> > mean_label    = "Mean"
> > median_label  = "Median"
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
> >        data_label=data_label,
> >        mean=mean,
> >        mean_label=mean_label,
> >        median=median,
> >        median_label=median_label,
> >        xlabel="Measurements",
> >        ylabel="Air temperature ($^\circ$C)",
> >        file_name=str(num_measurements)+'.png',
> >    )
> > ```
> {: .solution}
{: .challenge}




### 2. Improve the organization of where the output of the calculation is placed

- It is considered bad practice to mix the placement output and code files in the same folder. Improve the structure of the repository by adding a new `output` folder under $HOME.
  ```
  $ mkdir output
  ```
- Update the path to where the plots are saved.

>
> > ## One solution: update the output-path
> >
> > ``` python
> > import pandas as pd
> > from matplotlib import pyplot as plt
> > import numpy as np
> >
> > #--- Set plot settings to match LaTeX<3
> > def latex_plot():
> >     plt.rcParams['figure.figsize'] = (16, 16)
> >     plt.rcParams['font.size'] = 45
> >     plt.rcParams['font.family'] = 'serif'
> >     plt.rcParams['axes.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['axes.titlesize'] = plt.rcParams['font.size']
> >     plt.rcParams['legend.fontsize'] = plt.rcParams['font.size']
> >     plt.rcParams['xtick.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['ytick.labelsize'] = plt.rcParams['font.size']
> >     plt.rcParams['xtick.major.size'] = 3
> >     plt.rcParams['xtick.minor.size'] = 3
> >     plt.rcParams['xtick.major.width'] = 1
> >     plt.rcParams['xtick.minor.width'] = 1
> >     plt.rcParams['ytick.major.size'] = 3
> >     plt.rcParams['ytick.minor.size'] = 3
> >     plt.rcParams['ytick.major.width'] = 1
> >     plt.rcParams['ytick.minor.width'] = 1
> >     plt.rcParams['legend.frameon'] = False
> >     plt.rcParams['axes.linewidth'] = 1.5
> >
> >     # --- Use latex-style on text in plots
> >     plt.rcParams['text.usetex'] = True
> >
> >     # --- Custumize the length of the labels
> >     plt.rcParams["legend.labelspacing"] = 0.2
> >     plt.rcParams["legend.handlelength"] = 1.0
> >     plt.rcParams["legend.borderaxespad"] = 0.01
> >
> >     # --- Ignore warnings for generated plot
> >     plt.rcParams.update({'figure.max_open_warning': 0})
> >
> >     plt.linewidth=17.0
> >     font_size_plot = 20
> >
> >     return font_size_plot
> >
> > def plot_data(data, data_label, mean, mean_label, median, median_label, xlabel, ylabel, file_name):
> >    plt.plot(data, "r-", label=data_label)
> >    plt.xlabel(xlabel)
> >    plt.ylabel(ylabel)
> >    plt.axhline(y=mean, color="b", linestyle="--", label=mean_label)
> >    plt.axhline(y=median, color="g", linestyle="--", label=median_label)
> >    plt.legend()
> >    plt.savefig(file_name)
> >    plt.clf()
> >
> >
> > def read_data(file_name, nrows, column):
> >    data = pd.read_csv(file_name, nrows=nrows)
> >    return data[column]
> >
> > # --- Add LaTeX-style plotting
> > latex_plot()
> >
> > # -- Set plot lables
> > data_label    = "Temp"
> > mean_label    = "Mean"
> > median_label  = "Median"
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
> >        data_label=data_label,
> >        mean=mean,
> >        mean_label=mean_label,
> >        median=median,
> >        median_label=median_label,
> >        xlabel="Measurements",
> >        ylabel="Air temperature ($^\circ$C)",
> >        file_name='output/'+str(num_measurements)+'_median.png',
> >    )
> > ```
> {: .solution}
{: .challenge}


### Example repository

A solution for a repository containing both the suggested change sets is given [here](https://github.com/sunnivin/exercise-code-review-better-organization).
