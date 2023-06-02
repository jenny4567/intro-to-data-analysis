# Load and join data with Pandas

_**This is a Makers Bite.** Bites are designed to train specific skills or
tools. They contain an intro, a demonstration video, some exercises with an
example solution video, and a challenge without a solution video for you to test
your learning. [Read more about how to use Makers
Bites.](https://github.com/makersacademy/course/blob/main/labels/bites.md)_

<!-- OMITTED -->

Learn to load datasets from files and join them using Pandas.


## Learning Objectives

In this chapter we will be continuing our goal of learning the Pandas library, and how to best implement it.

By the end of this chapter you will:

- Have a familiar understanding of data loading and viewing with Pandas
- Know some basic Pandas commands
- Deepen your understanding of data exploration

You should be able to:
- Describe what a Pandas DataFrame is
- Describe what a Pandas Series is
- Load data into a DataFrame from CSV
- Load two sets of data and join two DataFrames

___

## Introduction

In this chapter we will be looking at how to use the Pandas library to load, join and manipulate our data.

Pandas is a core library used by Data Scientists & Engineers around the world, it is completely
open-source and Pandas DataFrames are used in a variety of different Data Engineering situations very often.

 #### *DALC - 02 DATA UNDERSTANDING.*
 - [Click here for more Data Analytics Life Cycle detail.](../pills/data_analytics_life_cycle.md#2---data-understanding)

### Pandas Series

A Series in Pandas is an object that acts and looks a bit like an array. It is very similar to a python list we might be used to, except that it has labels attached to each item in the series (or array).

For example, we might be very familiar with this sort of list:

``` python
list_one = [1, 3, 5, 3.5, 2, 6, 2]
```

But the handy thing with a Pandas Series array is that it allows us to pass in a set of labels for each item in the list/array.

``` python
import pandas as pd

coffee_per_day = [1, 5, 8, 5, 4, 3, 2]
days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]

series_one = pd.Series(coffee_per_day, index=days)

series_one
```

Try this code above out in a cell in Jupyter.

Then add the `.head()` method to series_one, run again - what do you see?

Swap `.head()` for `.tail()` - what changes?

 - N.B. The length of the values *(pd.Series first argument)* and the length of labels *(pd.Series second argument)* must be the same - otherwise a ValueError will show. 

Rather helpfully - we can instantiate a Pandas Series straight from a Python Dictionary:

``` python
import pandas as pd

workout_dictionary = {
    "Monday" : "Core & Cardio",
    "Tuesday" : "Arms & Back", 
    "Wednesday" : "Rest Day", 
    "Thursday" : "Legs & Shoulders", 
    "Friday" : "Chest & Cardio", 
    "Saturday" : "Rest Day", 
    "Sunday" : "Calisthenics"
}

workout_series = pd.Series(workout_dictionary)

workout_series
```

You could however set a default value for your days too:

``` python
import pandas as pd

days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]

restful_life = pd.Series("Rest!", days)

restful_life
```

___

### Pandas DataFrame

DataFrames in Pandas are another Pandas specific Object with some interesting features.

We use DataFrames quite often when working with Datasets, sometimes in conjunction with Series, but often on their own. Let's take a look at them.

Where earlier we used lists or arrays to initialise a Series, with a DataFrame we can use a dictionary. Copy & run this cell in your Jupyter Notebook:

``` python
import pandas as pd

# Over 18 holes of disc golf, Amira, Steve and I have been keeping our scores

dict_scorecard = {
"Will" : [5, 4, 3, 3, 4, 4, 2, 3, 4, 4, 7, 4, 3, 3, 4, 3, 2, 3],
"Amira" : [3, 4, 2, 3, 4, 4, 5, 3, 5, 2, 5, 2, 4, 5, 4, 3, 4, 3],
"Steve" : [3, 4, 3, 4, 5, 3, 2, 5, 2, 5, 3, 5, 4, 4, 3, 2, 5, 3]
}

# I want to load these scores into a DataFrame to see them better

score_frame = pd.DataFrame(dict_scorecard)

score_frame
```

Much easier to read and compare than a dictionary. Notice that the keys from the dictionary ("Will", "Amira" and "Steve") have become the columns in the DataFrame.

``` python 
# Great! But there's no hole 0. And there is a hole 18...

score_frame = pd.DataFrame(dict_scorecard, index=[i for i in range(1,19)])

# So that the rows are labelled 1 to 18, instead of 0 to 17

score_frame.tail()
```

Remember those Series objects? We can use them to create DataFrames too:

``` python
import pandas as pd

# workout chart
workout_dictionary = {
    "Monday" : "Core & Cardio",
    "Tuesday" : "Arms & Back", 
    "Wednesday" : "Rest Day", 
    "Thursday" : "Legs & Shoulders", 
    "Friday" : "Chest & Cardio", 
    "Saturday" : "Rest Day", 
    "Sunday" : "Calisthenics"
}

workout_series = pd.Series(workout_dictionary)

# coffee chart
coffee_per_day = [1, 5, 8, 5, 4, 3, 2]
days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]

series_one = pd.Series(coffee_per_day, index=days)

# putting them together
coffees_vs_workout = {
    "coffee" : series_one,
    "workout" : workout_series 
}

pd.DataFrame(coffees_vs_workout)
```

___

### Loading CSV Data with Pandas

*"IT IS A CAPITAL MISTAKE TO THEORISE BEFORE ONE HAS DATA. INSENSIBLY ONE BEGINS TO TWIST FACTS TO SUIT THEORIES, INSTEAD OF THEORIES TO SUIT FACTS." ― SIR ARTHUR CONAN DOYLE, SHERLOCK HOLMES*

We need to be able to load some data. Thankfully pandas has a really handy in-built `.csv` reader. *(It also reads plain text files too!)*

Let's go ahead and use that very simple World Cup Winners data:

``` python
# Your path to the data may differ if you've stored the data in another folder in your project directory.

file = pd.read_csv("../data/extra-challenge/world_cup/WorldCups.csv")

winners_frame = pd.DataFrame(file)

winners_frame
```
We can look at the shape of our data 
with the `.shape` attribute. What information does this give us? What can you notice other than how large the DataFrame is:

``` python
winners_frame.shape
```

Let's take a look at how many goals were scored over the course of each year's competition:

``` python
file = pd.read_csv("../data/extra-challenge/world_cup/WorldCups.csv")

winners_frame = pd.DataFrame(file)

winners_frame["GoalsScored"]
```

We could do some pretty simple maths to work out the average amount of goals scored over the course of the FIFA World Cups History. Or, we could use the in-built pandas methods to do it for us!

``` python
file = pd.read_csv("../data/extra-challenge/world_cup/WorldCups.csv")

winners_frame = pd.DataFrame(file)

winners_frame["GoalsScored"].mean()

# Also options for min & max
winners_frame["GoalsScored"].min()
winners_frame["GoalsScored"].max()
```

That's a lot of info. Say we just wanted to look at 'Year', 'Country', and 'Winners', we could do something like this:

``` python
three_cols = winners_frame.columns[0:3]
winners_frame[three_cols]
```

We can group multiple sections of data inside the DataFrame together and plot some cool things with it.

Import `matplotlib.pyplot as plt` and we can use our ‘group’ variable we made to view our data! We can add multiple arguments to customise the graph.

``` python
group = winners_frame.groupby('Year')[['GoalsScored']].sum()

group.plot(kind='barh', figsize=(20, 15))
plt.title('Goals Scored by Year', fontdict={'fontsize': 30, 'weight': 'bold'}, pad=30)
plt.show()
```

___

### Joining DataFrames

Sometimes when working with data sets we have to work with more than one file, or more than one table. We might have to make some predictive analysis across separate pieces of data, or there might be more than one table of data points that are related in some way.

Much in a similar way to relational databases (if you have come across those in Software Development - don't worry if you haven't) we can JOIN two or more DataFrames together, in order to see more information, or to relate pieces of data together!

Let's start by joining two very simple tables of data. We'll go back to our
simple disc golf score sheet, and join another month's round of play to it.

``` python
import pandas as pd

# Over 18 holes of disc golf in March, Amira, Steve and I have been keeping our scores

march_dict_scorecard = {
"Will" : [8, 4, 3, 3, 4, 4, 2, 3, 4, 4, 7, 4, 3, 3, 4, 3, 2, 3],
"Amira" : [3, 2, 2, 3, 4, 7, 5, 3, 5, 2, 5, 2, 4, 5, 4, 3, 4, 3],
"Steve" : [2, 4, 2, 4, 5, 3, 2, 5, 2, 5, 3, 5, 4, 4, 3, 2, 6, 3]
}

# I want to load these scores into a DataFrame to see them better

march_score_frame = pd.DataFrame(march_dict_scorecard, index=range(1, 19))

print(march_score_frame)


# Over 18 holes of disc golf in April, Amira, Steve and I have been keeping our scores

april_dict_scorecard = {
"Will" : [3, 4, 2, 3, 4, 4, 2, 2, 3, 4, 4, 6, 3, 2, 4, 3, 3, 3],
"Amira" : [3, 4, 2, 3, 4, 3, 5, 3, 5, 2, 4, 2, 4, 5, 4, 3, 4, 3],
"Steve" : [3, 2, 3, 4, 5, 3, 2, 5, 2, 5, 2, 6, 4, 4, 3, 2, 4, 3]
}

# I want to load these scores into a DataFrame to see them better

hole_index = pd.Index(range(1, 19), name='Course Hole')

april_score_frame = pd.DataFrame(april_dict_scorecard, index=hole_index)
march_score_frame = pd.DataFrame(march_dict_scorecard, index=hole_index)

march_score_frame.join(april_score_frame, lsuffix=" (March)", rsuffix=" (April)")
```

You should see a larger table now, that includes both the April and March scores:

| Hole | Will (March) | Amira (March) | Steve (March) | Will (April) | Amira (April) | Steve (April) |
|------|----|---|---|---|---|---|---|
| **1**	| 8	| 3	| 2	| 3	| 3	| 2 |
| **2**	| 4	| 2	| 4	| 4	| 4	| 2 |
| **3**	| 3	| 2	| 2	| 2	| 2	| 3 |
| **4**	| 3	| 3	| 4	| 3	| 3	| 4 |
| **5**	| 4	| 4	| 5	| 4	| 6	| 5 |
| **6**	| 4	| 7	| 3	| 4	| 3	| 3 |
| **7**	| 2	| 5	| 2	| 2	| 5	| 2 |
| **8**	| 3	| 3	| 5	| 2	| 3	| 5 |
| **9**	| 4	| 5	| 2	| 3	| 5	| 2 |
| **10** | 4 | 2 | 5 | 4 | 6 | 5 |
| **11** | 7 | 5 | 3 | 4 | 4 | 2 |
| **12** | 4 | 2 | 5 | 6 | 2 | 6 |
| **13** | 3 | 4 | 4 | 3 | 4 | 4 |
| **14** | 3 | 5 | 4 | 2 | 5 | 4 |
| **15** | 4 | 4 | 3 | 5 | 4 | 3 |
| **16** | 3 | 3 | 2 | 3 | 2 | 2 |
| **17** | 2 | 4 | 6 | 7 | 4 | 4 |
| **18** | 3 | 3 | 3 | 3 | 2 | 3 |

___

We are going to take a look at another set of data now, The World Happiness Index!

Navigate to [this folder](../data/extra-challenge/happiness_data/) to take a look at the World Happiness Indices from 2015 to 2019.

 - What do you notice about the data?
 - How do the five different tables (files) differ?
 - What might the consequences be when joining this data?

Once you've had a look at the five files, we are going to load the first two into separate DataFrames.

The reason we are loading the first two, as the eagle-eyed amongst you may have noticed, is that they are fairly similar. In the next chapter we will get onto data cleaning and preparation, and be able to take a look at the differing data sets.

For now:

``` python
hap15 = pd.read_csv("./happiness_data/2015.csv")

print(hap15.head())

print(hap15.info())
```

And do the same for the next year:

``` python
hap16 = pd.read_csv("./happiness_data/2016.csv")

print(hap16.head())

print(hap16.info())
```

We can see that the two tables are very similar and won't need much preparation or cleaning in order to compare them. Let's go ahead and do that now.

``` python 
joined_table = hap15.join(hap16, how="outer", lsuffix="_2015", rsuffix="_2016")

print(f"The leading 5 happiness countries in 2015 were \n {joined_table['Country_2015'].head()}. \n Whereas in 2016 they were \n {joined_table['Country_2016'].head()}.")
```
___

We can execute a "One to Many" join by using the #merge() function and giving the column name to the `on=` parameter.

Let's explore how to do that with the 2016 and 2015 World Happiness Index tables:

``` python
hap_merged = pd.merge(hap16, hap15, on="Country", suffixes=[" 2016", " 2015"])

hap_merged.head()
```

This has created a "One to Many" type join across the two tables. Where "Country" has multiple related fields. This only works because "Country" is the same across both tables.

Which other columns are the same across both tables?

We can create a "Many to Many" relationship by using a list as an argument for the `on=` parameter:

``` python
hap_merged = pd.merge(hap16, hap15, on=["Country", "Region"], suffixes=[" 2016", " 2015"])

hap_merged.head()
```
___
## Demonstration

*Coming soon*

[Demonstration Video](#demonstration)
___

## Exercise

We have had a go at joining two tables with The World Happiness Index for 2015, and 2016. Your task now is to join the tables for The World Happiness Index for 2018, and 2019.

Set yourself 15 minutes for this task.

 - Join the data from The World Happiness Index for 2018 and 2019.
 - Visit the Pandas documentation for more info on different joins [here](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html)
 - What is the difference between the DataFrame method #concat [more info here](https://pandas.pydata.org/docs/reference/api/pandas.concat.html), and the #merge method [documentation link here](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html#pandas.DataFrame.merge)


<details>
    <summary> This could be a potential solution</summary>
    <a href="./exercise_solutions/03_exercise_solution.ipynb">
    Exercise Example Solution</a>
</details>


___
## Challenge

Navigate to the Cereals dataset [here](../data/extra-challenge/cereals/cereal.csv) and import it into a DataFrame using Pandas.

 #### *DALC - 02 DATA UNDERSTANDING.*
 - [Click here for more Data Analytics Life Cycle detail.](../pills/data_analytics_life_cycle.md#2---data-understanding)

Make your own brand of cereal and join it to the pre-existing cereal DataFrame.

You can input your own values for its nutritional value, or for an extra challenge, you can use the mean (average) from a selection inside the provided cereals table.

Make two more brands of cereal, and load them into their own DataFrame. 

Join them to your initial cereal DataFrame.

For an extra challenge, let us imagine that the cereal data was recorded before the infamous 'Sugar Tax' that was brought into law in 2018.

Copy the original cereal data, but reduce the sugar percentage by 20%. Store this in a separate DataFrame.

Join the two tables on the "Brand" and "Manufacturer" column to compare your data.

## Submitting Your Work

**No need to submit just yet, retain this notebook and your exploration for use in the next chapter's challenge!**



[Next Challenge](04_examine_data_with_pandas_bite.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F03_load_and_join_data_with_pandas_bite.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F03_load_and_join_data_with_pandas_bite.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F03_load_and_join_data_with_pandas_bite.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F03_load_and_join_data_with_pandas_bite.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F03_load_and_join_data_with_pandas_bite.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
