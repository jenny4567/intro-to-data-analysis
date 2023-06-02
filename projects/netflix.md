# How should Netflix spend 5 billion dollars?

## Learning objectives

For this project, your learning objectives are:

- Apply the exploratory data analysis to small datasets
- Combine data from different sources for effective data analysis
- Present data analysis findings effectively

<!-- OMITTED -->

## The scenario

You work as a data analyst for Netflix.
Netflix are like a web-based TV network.
They make and broadcast their own films and TV shows, and older films and TV shows they buy.

Danielle, Netflix's [Head of Original Content](https://www.linkedin.com/in/danielle-woodrow-bb740a171/) – your boss – is working on the strategy for the next five years. She's wondering what kinds of films or TV shows Netflix should make next.

Danielle has a budget of $5bn to develop Original Content in the next year.
Your key question is: **how should she spend it?**

Over the years, various Netflix data teams have compiled a data about the content they have in their catalogue. You can find the data in the `data`(./data) directory. Danielle asks if there are any useful insights in this data, which might inform her strategy for developing original content.

## The data

You have access to all the data files in the `data`(./data) directory but your starting point is the `netflix-titles.csv` data file in the `data/netflix`(./data/netflix), which contains a snapshot of the Netflix catalogue of Movies and TV Shows.

>  **Note**: All of the datasets in this directory are derived from publicly available data.

## Your goal

Prepare a 5-minute presentation to Danielle with your top recommendations for what Netflix should do.

You may find that it would be useful to introduce more sources of data into your analysis to augment the above. Here are some ideas you can try:

- **Rotten Tomatoes**  
  Rotten Tomatoes is a website that stores review data on most movies and TV shows, including Netflix content. Past contractors have compiled Rotten Tomatoes review data into two data files, both of which are in the `data/extra-challenge/rotten-tomatoes`(../data/extra-challenge/rotten-tomatoes) directory. Use the Rotten Tomatoes review data to substantiate your recommendations.

- **IMDB**  
  The IMDB is a website that stores data on most movies and TV shows, including Netflix content. There's all sorts of goodies in there, including film budgets. Past contractors have compiled IMDB data into a set of data files, all in the `data/extra-challenge/imdb`(../data/extra-challenge/imdb) directory. Then use the IMDB data to substantiate your recommendations.

The following ideas are interesting if you'd like an extra challenge. Expect these to stretch you and require significant additional research beyond what you've already seen in this module's exercises.

- **Enrich your data using Wikipedia's API**  
  Wikipedia is a website that stores data on most movies and TV shows, including Netflix content. Leverage the Wikipedia API to enrich the Netflix dataset with additional information. You could use a Python API wrapper such as [Wikipedia-API](https://github.com/martin-majlis/Wikipedia-API) to help you do this. Then use the Wikipedia data to substantiate your recommendations.

- **Combine data creatively using information from Goodreads**  
  Goodreads is a website that aggregates book reviews. Included in the [data/extra-challenge/goodreads](../data/extra-challenge/goodreads/books.csv) directory is `books.csv`. Use the book data – or any other data you can find – to substantiate your recommendations.

## Submissions

There is a single submission for this project and it is made up of: 

1. The Jupyter notebook you wrote to perform your analysis.
1. Your presentation slides.
1. Your practice presentation slides.


## How to approach this project

The most important thing is to answer the right question.  For example, the answer to a high-level question like "How should Danielle spend $5 billion?" is not quantifiable.
But questions like

- Which genres grossed the most in box office sales in the last 1 year?
- Which directors had the most well-reviewed films in the last 2 years?

are much more specific and will give you better guidance on how where to start looking and how to interpret the data.

So to start with, come up with three questions that will help you answer Danielle's problem but are more specific so that you can use them to guide your analysis.

Once you have your three questions, pick one and save the other two for later on. Ask yourself: 

- Where can I find the information that would help me answer this?
- Is there any other data that would help corroborate my findings?

Then go forth and analyse! Repeat this process for the other two questions. 
Finally, once you've summarised your insights for these three questions, take a step back and reflect: which of these questions generated the most useful findings? Why?

## Resources

As well as the data in the `data` directory, we've curated resources – articles, videos, cheat sheets and websites – relevant to this project. Check out the [inspiration](../inspiration/README.md) directory.

## Submitting Your Work

Use [this form](https://airtable.com/shr6mk28x0fy3OrxN?prefill_Item=data_eng_netflix01) to submit your code and screen recording

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=projects%2Fnetflix.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
