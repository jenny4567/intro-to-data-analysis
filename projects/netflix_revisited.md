# How Should netflix spend 5 billion dollars? - Revisited

You've already conducted [an initial exploratory data analysis of some Netflix data](netflix.md) and had a first run at presenting some findings from it.
In this project, you'll be revisiting and refining your conclusions using two additional datasets.


## Learning objectives

For this project, your learning objectives are:

- Work effectively with large datasets stored in the Cloud
- Apply predictive statistics based on a sample of historical data
- Present data analysis findings effectively

<!-- OMITTED -->

## The data

### Clickstream dataset

For this project, you will combine the datasets you've explored previously with a new dataset containing Netflix clickstream data.
Clickstream data refers to the information collected about a user while they browse through a website or use a web browser.
In this case, the dataset contains 42 months of user activity on Netflix websites between 2016 and 2019 by opted-in, anonymised users.

The main pieces of data collected were the following:

- The URL they visited on the Netflix website
- The time and date
- Their country of origin
- Details of their browser
- A randomly generated ID for each user, which resets after a pre-defined period of time

> ⚠️ **Note** Unlike the other datasets you used for this module, this data is
> private and proprietary! Do not share it with anyone outside Makers.
> 
> In order to get the credentials for this data from your coach(es), fill in
> [this
> form](https://docs.google.com/forms/d/e/1FAIpQLSdjeJSFLZ1A8HT3vAzOjz7MHimTgFSd3RlEoV2HN1QBUzL0-A/viewform)
> by signing (typing your full name), adding today's date and submitting the
> form.

You can find more detailed information about the origins and characteristics of this dataset [here](https://vodclickstream.com/the-data/).

### Mapping Netflix IDs to TV shows, movies and categories

The URLs in the clickstream dataset contain integer IDs that represent the movies, TV shows and genre categories in Netflix's catalogue.
For example, a click on a link to watch Titanic will show up as a URL that looks something like https://www.netflix.com/watch/1181461, where `1181461` is the ID Netflix has assigned the Titanic movie.

Other common URL patterns you will find in the dataset are:

| Example URL                               |    ID    | What it represents                                                                             |
|-------------------------------------------|:--------:|------------------------------------------------------------------------------------------------|
| https://www.netflix.com/watch/80051137    | 80051137 | The user started watching the TV show or movie represented by the ID 80051137 (Fuller House).  |
| https://www.netflix.com/browse/genre/5763 |   5763   | The user browsed the catalogue for titles in the genre category represented by ID 5763 (Dramas).        |
| https://www.netflix.com/gb/title/80093138 | 80093138 | The user opened the overview page for the title represented by ID 80093138 (Now You See Me 2). |
| https://www.netflix.com/search/grinch     |    N/A   | The user searched the Netflix catalogue for titles matching "grinch".                          |


To map IDs to TV shows and movies, use the Netflix Titles dataset ([data/standard/netflix-titles.csv](../data/netflix/netflix-titles.csv)), which you have already explored previously.

> **Note**: Due to data quality issues and the frequent changes that Netflix makes to its catalogue, not all IDs in the Clickstream dataset will have a matching entry in one of the above datasets.

To help you map genre IDs to category names, here is the list of the  main Netflix genre categories and their IDs:

- Action & Adventure (1365)
- Anime (7424)
- Children & Family (783)
- Classic (31574)
- Comedies (6548)
- Documentaries (6839)
- Dramas (5763)
- Horror (8711)
- Music (1701)
- Romantic (8883)
- Sci-fi & Fantasy (1492)
- Sports (4370)
- Thrillers (8933)
- TV Shows (83)

There are many more IDs for more granular categories. For the full list, [refer to the bottom of this page for a searchable list](https://www.whats-on-netflix.com/news/the-netflix-id-bible-every-category-on-netflix/).

## The goal

Using the clickstream dataset and the other datasets available to you, prepare a new 5-minute presentation to Danielle with your top recommendations for what Netflix should do.
Consider how you might statistically analyse user behaviour to back up your previous recommendations or generate new ones using based on this new data.

## Submissions

There is a single submission for this for this project, made up of three parts:

1. The Jupyter notebook you wrote to perform your analysis.
2. Your presentation slides.
3. Your presentation itself.


## Start here

### Get access to the data

<!-- OMITTED -->

As this dataset is very large (close to 100GB), it's stored in a Cloud Storage service called Amazon S3.
S3 is an offering of Amazon Web Services (AWS), one of the most popular cloud service providers in the industry.

Once you have acknowledged the data processing agreement, your coach will give you the AWS credentials you need to access the dataset.
[Follow the instructions in this guide to set up these credentials so you can access AWS](../pills/accessing_aws.md)

<!-- OMITTED -->


To check that you have all the permissions you need to access the dataset, run the following `aws` command to list the files belonging to the dataset in S3:

```
aws s3 ls s3://data-eng-datasets-404544469985/vod_clickstream
```

You should see output that looks something like this (the date and time shown below will be different):

```
aws s3 ls s3://data-eng-datasets-404544469985/vod_clickstream/
                           PRE full/
                           PRE sample/
2023-02-21 11:40:06          0
```

This confirms that your AWS credentials have been set up correctly and you have all the right permissions.
If you run into trouble, reach out to your coach.

### Load the clickstream data into pandas

Due the fact that the clickstream dataset is stored in the Cloud rather than
locally, loading it into Pandas will involve a few more steps than what you've
seen so far. It's also very large, which means it won't be possible to load the
entire dataset into Pandas. These are a common challenge of working with data at
scale and there are different ways of approaching them.

In this module, you're going to use one of the most common and simple techniques for working around this: sampling, i.e. selecting a (hopefully somewhat representative) subset of the whole dataset to work with.

To get started, you'll need to install two new packages in the Python virtual environment you've been using for working with Pandas: `s3fs` and `pyarrow`.

`s3fs` allows pandas to retrieve data from S3. `pyarrow` allows us to read [Parquet files](https://parquet.apache.org/), which is the data format in which the dataset is stored.

```
source data_venv_name/bin/activate
pip install s3fs pyarrow
```

Next, [head to this Jupyter notebook to learn about how to work effectively with this dataset](../notebooks/netflix_clickstream.ipynb).

<!-- OMITTED -->



## Submitting Your Work

Feel free to upload your slides, notebook, and any supporting material. You can zip them up into a `.zip` folder and upload that too, if you have lots of files.

Use [this form](https://airtable.com/shr6mk28x0fy3OrxN?prefill_Item=data_eng_netflix02) to submit your code and screen recording


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix_revisited.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix_revisited.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix_revisited.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix_revisited.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix_revisited.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
