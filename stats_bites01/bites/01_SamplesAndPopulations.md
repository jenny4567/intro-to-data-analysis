# Samples and Populations

_**This is a Makers Bite.** Bites are designed to train specific skills or
tools. They contain an intro, a demonstration video, some exercises with an
example solution video, and a challenge without a solution video for you to test
your learning. [Read more about how to use Makers
Bites.](https://github.com/makersacademy/course/blob/main/labels/bites.md)_

## Learning Objectives 
After this part of the course, you will be able to 
- Explain the meaning of "sample" and "population" 
- Identify a "sample" and a "population"
- Start to evaluate methodology

## Introduction
The first statisticians worked for governments who wanted to understand their people. One tool governments can use is a `census`, which aims to gather data about everyone the government rules -- the entire `population`. These are expensive and time consuming. Although online forms potentially make it easier to gather data on the entire population, it is not always practical.

The alternative to measuring the entire population is to measure a subset of it, called a `sample`. This would be a smaller job, but it introduces some doubt as to how well the sample represents the population. For instance: if you want to find out how popular different types of fast food are, but conduct your survey outside a fish and chip shop, then you might introduce `bias` into your data. Ideally: we would like every member of the population we want to study to have the same chance of being selected as part of the sample we measure.

As the techniques of statistics came to be used in wider contexts, the term `population` broadened beyond the meaning: 'a group of people'. If you want to know the average height of daffodils in the UK, then your population is all the daffodils in the UK. It would be a very big job to measure them all, so you would seek to measure some of them from a variety of locations in the UK. That would be your `sample`.

In mathematical terms: the `sample` is a subset of the `population`. This means that every element of the sample is also an element of the population. 

## Exercise 
For this exercise, our population will be the [240 stars selected by NASA](../../data/smaller-datasets/Stars.csv) (also found here - https://www.kaggle.com/datasets/brsdincer/star-type-classification) for their examples of star classification. The aim is to pick a sample of these stars. 

Go to [sample the stars notebook](../notebooks/01_sample_the_stars.ipynb) and follow the instructions. You may find [this page](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sample.html) useful.

<details>
<summary>Reveal suggested answer</summary>
Add the following code to Jupyter notebook file:

```python
# There is a Stars.csv file in the data/smaller-datasets directory
# load that file into a pandas data frame

stars = pd.read_csv("../../data/smaller-datasets/Stars.csv")

# Take a sample of seven stars from the population. And print that sample

print(stars.sample(7))
```

</details>

## Investigation

It's unlikely that the sample will perfectly match the population and that leads to some uncertainty in our conclusions. Unless, however, we can gather and analyse data for the whole population we have to accept this situation and be careful with our conclusions.

One of the factors involved is sample size. Work through this investigation [here](../notebooks/01_population_size_flat.ipynb) to see how the size of a sample can change how certain we are of our conclusions.

## Exercise
A factory produces jars of instant coffee labeled as having 300g of coffee in them. As a quality check: 50 jars are chosen each day and their contents weighed. If this shows that the machines are underfilling/overfilling the jars, then the machines are adjusted. 

Which of the following is true?
- The population is all the jars made at the factory, and the sample is all the jars collected
- The population is all jars of coffee that are labeled 300g, the sample is the jars from this factory
- Each day's total production of jars is a population, and the jars collected that day would be the corresponding sample

<details>
<summary>Reveal suggested answer</summary>
Some of this is down to interpretation. I would choose this:

`Each day's total production of jars is a population, and the jars collected that day would be the corresponding sample.`

The purpose of our sampling is to adjust the machines and keep the 'average' weight of coffee in a jar as close to 300g as we can. As such, I would regard the coffee jars as being split into separate populations.

Somebody else could be running a long-term study of how the contents of the jars varies. And maybe the population they are considering is all the jars produced over a longer period than a day. I don't think that is the described situation.

The middle option would leave me with questions about methodology. There is no reason to suppose that this factory's jars are representative of all 300g jars of coffee.

</details>

For the next exercise, which is quite hard, it may help to focus on the idea that the `sample` should be a subset of the `population`.

## Exercise

An MP wanted to know how popular a policy was among their constituents, and decided to conduct a survey. They visited a shopping centre in one of the cities they represent and asked 28 people their opinion. 

Which of the following is true?
- The population is the MP's constituents, and the sample is those who were shopping that day
- The population is the people who were in the shopping centre at the time and the sample is the 28 people the MP spoke to
- The population is the MP's constituents and the sample is the 28 people the MP spoke to

<details>
<summary>Reveal suggested answer</summary>

`The population is the people who were in the shopping centre at the time and the sample is the 28 people the MP spoke to.` 

The MP's sample will only point to the attitudes of the shoppers, not the MP's constituents. There may be a big overlap but, as described, the MP did not sample the population they wanted to learn about.

Don't confuse the MP's intention with what they actually did. Some of the people in the shopping center, or some of those the MP spoke to, may not have been the MP's constituents.
</details>

## Challenge
A challenge for you to do. These are designed to help you challenge your learning. They don't have example solutions but you can check in with a coach if you are stuck or unsure.

The police want to know how many unlicensed drivers there are in the area they administer. They investigate this by stopping drivers and asking to see their licence. They do this at a variety of times and in different parts of the area they work in.

In this study: what is the population and what is the sample?

<!-- OMITTED -->

## Submitting Your Work

**No need to submit just yet, retain this information, perhaps in the notebook you have been using for use in the next chapter's challenge!**


[Next Challenge](02_DescriptiveStatistics.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F01_SamplesAndPopulations.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F01_SamplesAndPopulations.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F01_SamplesAndPopulations.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F01_SamplesAndPopulations.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=stats_bites01%2Fbites%2F01_SamplesAndPopulations.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
