# Week 12: Plotting with Python

This week, we'll be moving on to plotting (graphing). We'll look at how to build graphical summaries of data using the library `plotnine`.

Python has powerful built-in plotting capabilities such as `matplotlib`, but for this episode, we will be using the `plotnine` library, which facilitates the creation of highly informative plots of structured data based on the R implementation of ggplot2 and The Grammar of Graphics by Leland Wilkinson. The `plotnine` library is built on top of `matplotlib`.

We will also use the `Pandas` library to handle our data file.

# Libraries setup

Just as with the other libraries, `plotnine` needs to be **imported** before we can use it. It's good practice, and makes things later much easier, to not just load an entire package (`import plotnine`), but to use an abbreviation: `import plotnine as p9`. Now, we can just type `p9` instead of `plotnine`!

Let's also import Pandas with a shorter name: `import pandas as pd`

Today we will use the **surveys.csv** data set (on Moodle). Drop that file into your repl in the working directory. This is a subset of the data from the long-term monitoring and experimental manipulation of a Chihuahuan Desert ecosystem (Arizona, USA) study by Ernst et al.

# Import the data

We can use Pandas's `read_csv` function to pull the file directly into a **DataFrame**:

```
surveys = pd.read_csv("surveys.csv")
```

A **DataFrame** is a 2-dimensional data structure that can store data of different types (including characters, integers, floating point values, etc.) in columns. It's similar to a spreadsheet. A dataframe always has an index (0-based). An index refers to the position of an element in the data structure.

Let's take a look at our data: `print(surveys)`

We can see that there were 30,676 rows parsed. Each row has 9 columns. The first column is the index of the dataframe. The index is used to identify the position of the data, but it's not an actual column of the DataFrame. It looks like the read_csv function in Pandas read our file properly.

What kind of things does **surveys** contain? Dataframes have an attribute called `dtypes` that answers this:

```
print(surveys.dtypes)
```

All values in a column have the same **type**. For example, months have type int64 (integer). Cells in the month column can't have fractional values, but the weight and hindfoot_length columns can, because they have type float64 (float). The object type doesn't have a very helpful name, but in this case it represents strings (such as "M" and "F" in the case of sex).

# Calculating summary statistics

Next, let's perform some quick summary statistics to learn more about the data that we're working with. We might want to know how many animals were collected in each site, or how many of each species were caught. We can perform summary stats quickly using groups. But first we need to figure out what we want to group by. We can just look at the output from the previous function to see the column names.

Now, let's get a list of all the species. `pd.unique` tells us all the unique values in a column:

```
print(pd.unique(surveys["species_id"]))
```

We often want to calculate summary statistics grouped by subsets or attributes within fields of our data. For example, we might want to calculate the average weight of all individuals per sex.

We can calculate basic statistics for _all records_ in a single column using the syntax below. The Pandas function `describe` will return descriptive stats including: mean, median, max, min, std and count for a particular column in the data. Pandas's `describe` function will only return summary values for columns containing numeric data.

```
surveys["weight"].describe()
#Use print to see output
```

We can also extract one specific metric if we wish:

```
surveys["weight"].min()
surveys["weight"].max()
surveys["weight"].mean()
surveys["weight"].count()
```

But if we want to summarize by one or more variables, for example sex, we can use Pandas's `.groupby` method. Once we've created a groupby dataframe, we can quickly calculate summary statistics by a group of our choice.

```
grouped_data = surveys.groupby("sex")

#Summary stats
grouped_data.describe()
```

# Plotting with `plotnine`

Now let's visualize our data! `plotnine` supports the creation of complex plots from data in a dataframe. It uses default settings, which helps in creating publication quality plots with a minimal amount of settings and tweaking.

`plotnine` graphics are built step by step by adding new elements on top of each other using the `+` operator. Putting the individual steps together in parentheses () provides Python-compatible syntax.

## Building a `plotnine` graphic

To build a plotnine graphic we need to do several things. The first is to **bind the plot to a specific dataframe** using the `data` argument:

```
p9.ggplot(data = surveys)
```

But within this same statement, we also need to describe how various **variables in the data are mapped to visual properties** (`aes` = **aesthetics**) of the plot, using `mapping`. The most important `aes` mappings are: `x`, `y`, `alpha`, `color`, `fill`, `linetype`, `shape`, `size`, and `stroke`.

```
p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length"))
```

But still no specific data is plotted. We have to define what kind of geometry will be used for the plot. The most straightforward is probably using **points**. Point is one of the `geoms` options, the **graphical representation of the data** in the plot. Other options: lines, bars, histograms, etc.

To add a `geom` to the plot, use `+` operator:

```
#This is all one line
p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length"))
              + p9.geom_point()
```

The `+` is particularly useful because it allows you to modify existing `plotnine` objects. This means you can easily set up plot templates and explore different types of plots. The above plot can also be generated with code like this:

```
# Create
surveys_plot = p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length"))

# Draw the plot
surveys_plot = surveys_plot + p9.geom_point()
```

For some reason, it seems Repl won't let us view these plots interactively with `.geom` like we'd be able to do if running Python on our own computers natively. But it should work if you `print` a plot object. You'll probably have to hard-stop Python (hit Stop button) when you finish looking at the plot.

```
print(surveys_plot)
```

## Saving the plot to file

You can also view the plot by saving it to a file. This is similar to how we saved phylogenetic trees to files last week. We'll use the `.save` method.

You can also set various file attributes if you need something other than the defaults, such as image resolution or dimensions. More information about the `.save()` method can be found [in the manual](https://plotnine.readthedocs.io/en/stable/generated/plotnine.ggplot.html).

When you run `.save()`, it might show a couple of "UserWarnings", but these appear to not really be warnings, but rather "notices" about what Python is doing - e.g., UserWarning might appear to let you know the image dimensions (if you don't specify dimensions) and that Python guessed the file format from the filename extension. This is all normal.

```
surveys_plot = p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length"))
                          + p9.geom_point()

surveys_plot.save("surveys_plot.jpg", width=11, height=8.5, units="in")
```

## Other types of plots

_Another example:_ we can use the `plot_id` column in the dataset to create a **bar plot** that shows the number of records for each survey plot (the number of records collected for each plot of land that was surveyed in the study):

```
surveys_barplot = p9.ggplot(data = surveys, mapping = p9.aes(x = "plot_id"))
                             + p9.geom_bar()
```

## Adding and changing features

Building plots with `plotnine` is typically an iterative process. We start by defining the dataset we’ll use, lay the axes, and choose a `geom`. Thus, the data, `aes` and `geom` are the basic elements of any graph.

```
surveys_plot = p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length"))
surveys_plot = surveys_plot + p9.geom_point()
```

From there, we can add features and change settings as desired. Some common features:
- `alpha` - transparency (0-1, where 1 is completely opaque)

    ```
    surveys_plot + p9.geom_point(alpha = 0.1)
    ```

- `color` - add colors for all of the points

    ```
    surveys_plot + p9.geom_point(alpha = 0.1, color = "blue")
    ```

- We can also color each species in the plot differently by changing the global `aes` settings to map the `species_id` column to the `color` aesthetic:

    ```
    surveys_plot = p9.ggplot(data = surveys, mapping = p9.aes(x = "weight", y = "hindfoot_length", color = "species_id"))
                              + p9.geom_point(alpha = 0.7)
    ```

Apart from the adaptations of the arguments and settings of the data, `aes` and `geom` elements, additional elements can be added as well, using the `+` operator.

For example, change the **axis labels** using the `.xlab` method

```
surveys_plot_new = surveys_plot + p9.geom_point(alpha = 0.2) + p9.xlab("Weight (g)") + p9.ylab("Hindfoot length (mm)")
```
