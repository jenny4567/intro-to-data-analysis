# Calculating Mean, Median and Mode

_**This is a Makers Bite.** Bites are designed to train specific skills or
tools. They contain an intro, a demonstration video, some exercises with an
example solution video, and a challenge without a solution video for you to test
your learning. [Read more about how to use Makers
Bites.](https://github.com/makersacademy/course/blob/main/labels/bites.md)_

## Learning Objectives

By the end of this chapter, you should be able to:

- Calculate the mean, median and mode
- Explain some of their uses and limitations

___

## Introduction
In the previous chapter, we were able to summarise the information in the temperature column of our `stars` collection by giving the `range`.

This chapter introduces three more summaries: 

- [Mean](./03_CalculatingMeanMedianAndMode.md#Mean)
- [Median](./03_CalculatingMeanMedianAndMode.md#Median)
- [Mode](./03_CalculatingMeanMedianAndMode.md#Mode)

All three of these are a type of `average`. They can act as a 'stand in' for the whole data. They are often described as measures of the "centre" of a sample -- although this is rarer for the `mode`.

We saw how to use `pandas` to calculate these values [earlier in the course](../../pandas_bites/04_examine_data_with_pandas_bite.md).

 #### *DALC - 02 DATA UNDERSTANDING.*
 - [Click here for more Data Analytics Life Cycle detail.](../../pills/data_analytics_life_cycle.md#2---data-understanding)

___

## Mean

As you may remember from school, the `mean` (more accurately: the `arithmetic mean`) is calculated by "adding them all up and dividing by how many".

## Exercise

Okay, you can use a calculator. But no pandas! Find the mean of these numbers:

```
28, 16, 73, 23, 46, 78
```

<details>
<summary>Reveal suggested answer</summary>

The numbers add up to `264`

```264 / 6 = 44```

So the mean is 44
</details>

## Exercise
Group our `stars` collection by colour, and find the mean temperature of each colour (rounded to 1 decimal place). Sort the results and display in a table. Use `pandas` this time.

The first few lines of the table should look like this:

|	Color |	mean temperature|
|---|---|
| Blue	| 21918.3 |
| Blue-white	| 16660.0 |
| Yellowish White	| 10826.7 |

<details>
<summary>Reveal suggested answer</summary>

```python
import pandas as pd
import numpy as np

stars = pd.read_csv("../../data/smaller-datasets/Stars.csv")
stars.groupby("Color")["Temperature"].mean().reset_index(name="mean temperature").sort_values(by="mean temperature", ascending=False).round(1)
```
</details>

## How does the mean summarise the data?

Earlier, we found that the mean of these numbers:

```
28, 16, 73, 23, 46, 78
```

is `44`

Here is another list of numbers. What is the mean?

```
44, 44, 44, 44, 44, 44
```

All the numbers are the same. So the quick way to add them up would be to do `44 times 6 = 264`, then we divide by 6 to get the mean. But that undoes the multiplication. So we are back to `44`

These two sets of numbers are clearly quite different but their means are identical. So when we think of the mean as a "summary" of a list of numbers we have to remember that we are leaving out a lot of detail. It's true that every summary will do this to an extent, but what we see in this example is quite extreme. It is why the `mean` is often quoted along with another measure: the `standard deviation`, which describes how the data is spread out around the mean. (`Standard deviation` is a topic for another time).

___

## Median

If the numbers in our list are not all the same, then there must be at least one number above the mean and one below the mean. So the mean doesn't sit on the edge of our data. However: it is easy to come up with a list of numbers where the mean isn't in the middle.

```
1, 2, 3, 4, 100

sum = 110
mean = 22
```

We would say "The mean is not a good measure of the centre in this data". The last number in the list is very different to the others, it could called an `outlier`. It has quite a big influence on the mean. (Compare the mean of the first four numbers to the `mean = 22` we get when including the `100`)

There is nothing special about the numbers we used. The `mean` is quite sensitive to outliers.

Luckily, there is another measure of the centre: the `median`. To find the `median`, you "put the numbers in order and find the middle".

## Exercise
First a no `pandas` question. Find the `median` of each of these lists of numbers:

```
7, 36, 24, 48, 26
```
```
38, 21, 27, 23, 19, 34
```

<details>
<summary>Reveal suggested answer</summary>

When put in order, the numbers are:

```
7, 24, 26, 36, 48
```

And the middle number is `26`

The other list is a bit harder, since it has an even number of numbers.

```
19, 21, 23, 27, 34, 38
```

There are two numbers in the middle. Half way between them is `25` so that is the median. (You can calculate that middle as the `mean` of 23 and 27: `23 + 27 = 50` then `50/2 = 25`)
</details>

## Exercise

Group our `stars` collection by colour, and find the median temperature of each colour (rounded to 1 decimal place). Sort the results and display in a table. Use `pandas` this time. 

<details>
<summary>Reveal suggested answer</summary>

The code is very similar to when we did this for the mean. Just change `mean` to `median`
</details>

## Exercise: Outliers and the median

Remember these numbers, and how `100` has a big influence on the mean?

```
1, 2, 3, 4, 100

sum = 110
mean = 22
median = 3
```

Append more numbers to the list, until you get a `median` greater than `4`.

<details>
<summary>Reveal suggested answer</summary>

It doesn't matter how big the first number you append is.

```
1, 2, 3, 4, 100, infeasably_large_number

sum = infeasably_large_number + 110
mean = big_as_you_like_if_you_can_afford_enough_infeasable_largeness
median = 3.5

Since 3 and 4 are in the middle, and halfway between them is 3.5
```

And now to aim for a value more than `4`

```
1, 2, 3, 4, 100, 100, 100, 100

sum = 410
mean = 51.25
median = 52
```

This is now a list of numbers that is split between large and small. Notice how the `median` and `mean` are closer now. That wouldn't have happened if we had continued with `infeasable largeness` because the effect on the `mean` would have been far bigger than on the `median`.

We could also have gone for numbers smaller than `100` and still shifted the median above `4` (although, I don't think this counts as 'append')

```
1, 2, 3, 4, 5, 5, 5, 100

sum = 125
mean = 15.625
median = 4.5
```

</details>

From this we see that the `median` is a more stable statistic than the `mean`. We can always say with confidence that half of our data has a value below the `median` and half has a value above the `median`. The `mean` is also used as a measure of the centre, but always remember our example with the outlier.

___

## Mode

The `mode` is the "most common", and it can apply to a list of anything -- names, numbers, colours... 

We made a frequency table for our `stars` collection in the previous chapter. From that, we could see that red stars where the most common in that collection. In fact: 112 out the 240 stars were red. 

`Mode` is sometimes used in an adjective form, where we would say: "Red is the modal colour of the stars in our collection".

## Exercise

Find the mode of 

```
pink, green, black, orange, black, purple, brown, red
```

<details>
<summary>Reveal suggested answer</summary>

The mode is `black`, since that appears in the list twice and everything else once.
</details>

Sometimes, there is a "joint first":

```
M, T, W, T, F, S, S

Both 'T' and 'S' are the most common
```

So the initials for the days of the week is `bimodal` -- it has two modes. 

Sometimes, everything has an equal frequency.

```
This list has no mode
1, 1, 2, 2, 3, 3, 4, 4, 5, 5
```

Some conventions would say that you have no mode at all. But what does `pandas` say?

<details>
<summary>Reveal answer</summary>

`pandas` takes `'multi-modalness'` to extremes and lists them all!

```python
import pandas as pd
s = pd.Series([1, 1, 2, 2, 3, 3, 4, 4, 5, 5])
s.mode()
```   
</details>

___

## Challenge
   A challenge for you to do. These are designed to help you challenge your
   learning. They don't have example solutions but you can check in with a coach
   if you are stuck or unsure.

Can you find five numbers where the mean, median, mode and range are all 4?

## Submitting Your Work

**No need to submit just yet, retain this information, perhaps in the notebook you have been using for reference in future challenges**

<!-- OMITTED -->



[Next Challenge](04_Other_Percentiles.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F03_CalculatingMeanMedianAndMode.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F03_CalculatingMeanMedianAndMode.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F03_CalculatingMeanMedianAndMode.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F03_CalculatingMeanMedianAndMode.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F03_CalculatingMeanMedianAndMode.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
