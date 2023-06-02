# Examine data with pandas

_**This is a Makers Bite.** Bites are designed to train specific skills or
tools. They contain an intro, a demonstration video, some exercises with an
example solution video, and a challenge without a solution video for you to test
your learning. [Read more about how to use Makers
Bites.](https://github.com/makersacademy/course/blob/main/labels/bites.md)_

## Introduction

Now that we have begun to load our data using pandas with our tools in the
previous module, we can now use even more pandas methods to examine the data - and figure out what to do with the tricky situation of missing data points, and
data points that seem incorrect.

 #### *DALC - 02 DATA UNDERSTANDING.*
 - [Click here for more Data Analytics Life Cycle detail.](../pills/data_analytics_life_cycle.md#2---data-understanding)

## Learning Objectives

By the end of this Chapter, you should be able to:

- define inspect/examine data and describe why we need to do this.
- generate summary metrics
- find missing / null values
- print out some rows
- discover data types
___

### Examining Data & Summary Metrics

Let's load in the 2015 data on the World Happiness Index again.

``` python
import pandas as pd

hap15 = pd.read_csv("../data/extra-challenge/happiness_data/2015.csv")

# We can use index location (.iloc) to retrieve the first 5 entries

hap15.iloc[0:5]
```

Now we can use a series of in-built Pandas methods to examine the data. This is what it might look like if we began with #info() and #describe().

Let's run #info() on the whole DataFrame and the first 5 rows:

``` python
print(hap15.info())

print(hap15.iloc[0:5].info())
```

We can see from the #info() method that there are no null type values - this is good, it means there is no missing information that we would need to deal with. 

The #info() method also points out to us what data-type has been used in which Column. Again more helpful information should we need to compare values, or plot visualisations.

As before, let's run #describe() on the whole DataFrame and the first 5 rows:

``` python
print(hap15.describe())

hap15.iloc[0:5].describe()

# We don't need print() on the second line of code as we it will return a more verbose table without print()
```

The #describe() method gives us loads of fantastic information. From the count and the mean, to the 25th, 50th, and 75th percentiles, as well as the standard deviation.

Let's say for example, we wanted to calculate the mean Happiness Score of the top 5 countries in 2015, here's another way we could achieve this:

``` python
# All mean values for all columns over the top 5 rows
hap15.iloc[0:5].mean()

# Just the Happiness Score mean value over the top 5 rows
hap15['Happiness Score'].iloc[0:5].mean()
```

What other summary metrics can we glean from using Pandas? Pandas has in-built methods for calculating many other forms of descriptive statistics.

Such as:
1.	count() - Number of non-null observations
2.	sum()	- Sum of values
3.	mean()	- Mean of Values
4.	median()	- Median of Values
5.	mode()	- Mode of values
6.	std()	- Standard Deviation of the Values
7.	min()	- Minimum Value
8.	max()	- Maximum Value
9.	abs()	- Absolute Value
10.	prod()	- Product of Values
11.	cumsum()	- Cumulative Sum
12.	cumprod()	- Cumulative Product

**N.B. We will be going into Descriptive Statistics in much greater detail in the upcoming Statistics module, in the third chapter on Descriptive Statistics.** 

___

### Locating Rows

As well as using `#iloc()` to find the index location of entries we can use another method simply called `#loc()`. 

There is another piece of data around the World Cup Matches we can dig into. Load the file called `WorldCupMatches.csv`.

Note the path to the file will depend on where you have downloaded them / cloned them.

``` python
file_matches = pd.read_csv('<your-path-to-file>/WorldCupMatches.csv')

whole_data = pd.DataFrame(file_matches)

whole_data.columns
```

This is a rather long file. Let's say we wanted to look *only* the finals. How might we pull out just the rows where the data point is "Final" under the Stage column?

We could go through a rather convoluted way of using index of, and turning each column into a list and getting the index, *OR*, we could use the handy `.loc` method in pandas:

``` python
finals = whole_data.loc[whole_data['Stage'] == 'Final']

finals
```

Let's use some handy `for` loops to find out who won the World Cup at each tournament:

``` python
finals = whole_data.loc[whole_data['Stage'] == 'Final']

home_away = pd.DataFrame([finals['Year'], finals['Home Team Name'], finals['Home Team Goals'], finals['Away Team Name'], finals['Away Team Goals'], finals['MatchID'], finals['Win conditions']])

for i in home_away:
    # print(home_away[i]['Home Team Goals'])
    if home_away[i]['Home Team Goals'] > home_away[i]['Away Team Goals']:
        print(f"In the year {int(home_away[i]['Year'])}, {home_away[i]['Home Team Name']} won the World Cup!")
    elif home_away[i]['Home Team Goals'] < home_away[i]['Away Team Goals']:
        print(f"In the year {int(home_away[i]['Year'])}, {home_away[i]['Away Team Name']} won the World Cup!")
    else:
        print(f"It ended a draw and then {home_away[i]['Win conditions']}...")

```
___

### Missing Data

Often when we are examining our data, we come across missing values. This can be due to a number of reasons. 

It might be that the field simply does not apply in the case of the entry - for example, when we looked at the Players in the World Cup game, not every player scored, or got a red card - therefore not every entry in that table had a value for the 'Event' column.

It might be that the data is genuinely missing. In the case of the rather famous Titanic dataset ([can be explored here](../data/extra-challenge/titanic/titanic.csv)), some of the data is missing because it is simply not known. It failed to be captured at the time, it failed to be captured after the event, or it is lost in one way or another.

We will look at replacing the missing data in the next chapter!
___
## Demonstration

*Coming soon*

[Demonstration Video](#demonstration)
___
## Exercise

Navigate to the Planets dataset [here](../data/smaller-datasets/planets.csv) and import it into a DataFrame using Pandas.

List all the planets which have a greater mass than Earth.

List all the planets which have a Ring System around them.

Find the maximum surface gravity value for a planet in our solar system. Which planet is it?

Find the total mass of all the planets in our solar system. Is this greater than the Sun?

For an extra stretch goal, revisit with matplotlib, and chart the planets distance from the Sun against their Diameter.


<details>
    <summary> This could be a potential solution</summary>
    <a href="./exercise_solutions/04_exercise_solution.ipynb">
    Exercise Example Solution</a>
</details>

___
## Challenge

Navigate to the Cereals dataset [here](../data/extra-challenge/cereals/cereal.csv) and import it into a DataFrame using Pandas.

Your task is to explore the data as you see fit. Group together columns you think might have some relationship. Calories and Sugar? Fat and Weight?

Try and index the data set by Manufacturer, then by Sodium content.

Write in markdown cells any observations you notice between the data.

You will need to get familiar with the `pd.to_numeric()` method. [Docs here](https://pandas.pydata.org/docs/reference/api/pandas.to_numeric.html) 

## Submitting Your Work

Use [this form](https://airtable.com/shr6mk28x0fy3OrxN?prefill_Item=data_eng_pd01) to submit your code and screen recording

Hold onto this notebook, we'll continue to work with it in upcoming chapter challenges.



[Next Challenge](05_clean_and_filter_data_with_pandas_bite.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F04_examine_data_with_pandas_bite.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F04_examine_data_with_pandas_bite.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F04_examine_data_with_pandas_bite.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F04_examine_data_with_pandas_bite.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F04_examine_data_with_pandas_bite.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
