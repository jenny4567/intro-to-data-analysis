# Clean and filter data with pandas

_**This is a Makers Bite.** Bites are designed to train specific skills or
tools. They contain an intro, a demonstration video, some exercises with an
example solution video, and a challenge without a solution video for you to test
your learning. [Read more about how to use Makers
Bites.](https://github.com/makersacademy/course/blob/main/labels/bites.md)_


## Introduction

In this chapter we will begin to replace, amend and in some cases remove elements of our data set that are in need of changing. Most often this is due to missing data, as we discussed in the previous chapter, but in some cases this might be due to incorrect recordings, duplication or misinterpretations.

## Learning Objectives

By the end of this chapter you should be able to:

- explain why cleaning / filtering is needed
- identify how to clean the data (do we exclude data, do we fill in missing data, etc)
- and clean the data using common cleaning operations, such as:
  - replacing or dropping missing data (NAs or NaNs)
  - filtering out or dropping some rows
  - removing duplicates

#### *DALC - 03 DATA PREPARATION.*
 - [Click here for more Data Analytics Life Cycle detail.](../pills/data_analytics_life_cycle.md#3---data-preparation)
___
## Missing Data Part 2

In the previous chapter we looked at why we sometimes discover missing data. What you choose to do in these cases depends largely on what question you are attempting to answer.

In the case of plotting, for example, the ages of passengers who survived vs those who perished in the Titanic dataset - a missing age value will skew your results quite significantly. Therefore you may feel it is appropriate to find the mean (average) age of the gender of the passengers who survived/did not survive - and replace the missing value.

In other cases, where you would feel it is inappropriate to replace a value, like for example whether or not a passenger on the Titanic did or did not survive - you may opt for dropping the entire row. 

Both options are valid, and it is up to you to decide on what the best course of action is, dependent on your data, and the question you are attempting to answer.

Luckily, Pandas can help at all stages along the way.

Let's make some fake temperature data for 3 weeks.

``` python
import pandas as pd
import numpy as np

days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

# We are using a random number generator similar to the #random library in python
# This is a Numpy Random Number Generator that can produce numbers ina  certain shape
# In this example 5 working days worth, over 3 weeks times 6 for some chilly weather (in Celsius)!

temperature_df = pd.DataFrame((np.random.randn(5, 3)*6), index=days,columns=['week one', 'week two', 'week three'])

print(temperature_df) 
```

*N.B. The values will change every time this cell is run in a Jupyter notebook, as we are calling a random generator - be warned!*

This is fine as a set up. But what if our local meteorological station didn't record after Friday... ! 

``` python
# What about the weekend?

days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']

temperature_df = temperature_df.reindex(days)

print(temperature_df)
```

Now we are left with missing values for Saturday and Sunday. Let's check that with pandas:

``` python
temperature_df.isnull()
# Checks for null values

temperature_df.notnull()
# Checks for non-null (apparent) values
```

So what do we do? We could fill those missing values with a Scalar value (a single data-point) like the Integer 0:

``` python
temperature_df.fillna(0)
```

Or with another, non-Integer Scalar like a string:
``` python
temperature_df.fillna("missing")
```

But this might throw off our results, and might not be the best way of replacing our missing values.

We could pad, or 'front fill' the data, so it takes the values from the previous entry.

``` python
temperature_df.fillna(method='pad')
```

Or we could 'back fill' the missing data, drawing from the entry that comes after. (This won't work for our table as there is nothing after Sunday!)

``` python
temperature_df.fillna(method='bfill')
```

Or we could simply drop the rows entirely!

``` python
temperature_df.dropna()
```

Perhaps in this instance, the most appropriate thing to do might be to fill the missing values with the average temperature for that week:

``` python

for week in temperature_df:
    week_mean = temperature_df[week].mean()
    temperature_df[week] = temperature_df[week].fillna(week_mean)

temperature_df
```
___

### Duplicate Values

We might encounter a scenario whereby we have duplicate data that we want removing. Not to be confused with Categorical data, which is where the values for multiple entries may have the same values justifiable - for example the Country column of our World Cup players (each team member might have "Argentina" for that field) - duplicate values can be hard to detect by eye, and might lead to problems in your results. This might be due to human error, computational error, or other means - but whatever the cause, we will look at how to deal with duplicate values.

Let's look at the userbase and reviews of these music streaming services where the userbase is real, and the reviews are entirely made up:

``` python
review_service_dict = {
    "service" : ["spotify", "tidal", "apple music", "amazon music", "spotify"],
    "user_base" : [465000000, 6700000, 88000000, 82000000, 465000000],
    "review" : [9.4, 7, 8.4, 6.3, 9.4]
}

service_frame = pd.DataFrame(review_service_dict)

service_frame.drop_duplicates()
```

We can see from the subsequent table that the duplicate 'Spotify' entries were omitted.
___

## Demonstration

*Coming soon*

[Demonstration Video](#demonstration)
___
## Exercise

Let's look at the World Happiness Data once again, and if we load up the 2017 data, you might notice that there are some values missing. We can quickly check this with the #isnull() method.

``` python
# Is there any missing data?
hap17.isnull().values.any()

# Output =>
True


# Let's figure out which columns are missing data
for column in hap17:
    print(f"Column Name: {column}")
    print(f"Is missing data: {hap17[column].isnull().any()} \n")
```

Once we have ascertained which column is missing crucial data, but before we can fill in those missing data points, we need to find which Countries are missing data.

``` python
missing_countries = hap17[['Country', 'Happiness.Score']].loc[hap17['Happiness.Score'].isnull()]

print(missing_countries)
```

Now complete the solution to replacing those missing pieces of data:

``` python
average_dict = {}

for country in missing_countries['Country']:
    print(country)
    country_mean = [hap15['Happiness Score'].loc[hap15['Country']==country],
        hap16['Happiness Score']# ???,
        hap18['Score'] # ???,
        # ???]
    
    average_dict[# ???] = ???
    
average_dict

# Replace the missing values with the ones you have found

hap17['Happiness.Score'] = hap17['Happiness.Score'].fillna( #??? )
```
<details>
    <summary> This could be a potential solution</summary>
    <a href="./exercise_solutions/05_exercise_solution.ipynb">
    Exercise Example Solution</a>
</details>
___

## Challenge

Navigate to the Cereals dataset [here](../data/extra-challenge/cereals/cereal.csv) and import it into a DataFrame using Pandas.

Your challenge is to plot the calories of each cereal against their sugar content. 

You will notice there are missing values. Choose the most appropriate method to filling, or removing those values so as not to skew your results.

We will use this cleaned data for visualising in the next Chapter!

## Submitting Your Work

**No need to submit just yet, retain this notebook and your exploration for use in the next chapter's challenge!**



[Next Challenge](06_visualise_data_with_pandas_bite.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F05_clean_and_filter_data_with_pandas_bite.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F05_clean_and_filter_data_with_pandas_bite.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F05_clean_and_filter_data_with_pandas_bite.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F05_clean_and_filter_data_with_pandas_bite.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pandas_bites%2F05_clean_and_filter_data_with_pandas_bite.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
