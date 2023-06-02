# Pseudonymisation and anonymisation 

## Learning Outcomes
---
- Understand the concepts of pseudonymisation and anonymisation and their importance.
- Differentiate between identifiable data, pseudonymised data, and anonymised data.
- Apply appropriate methods of pseudonymisation and anonymisation to ensure the security and privacy of data while preserving its usefulness for research, analysis, or other purposes.


## Introduction
---

Pseudonymisation and anonymisation are two techniques used to enhance data privacy and protect the identities of individuals. 

**Identifiable Data**

Let's say we have the following patient data from a hospital. The <span style="background-color: lightblue">lightblue</span> columns are identifiable data.

| Hospital_ID |<span style="background-color: lightblue">First_Name </span>| <span style="background-color: lightblue">Last_Name</span> | <span style="background-color: lightblue">Gender</span> | <span style="background-color: lightblue">Date_of_Birth</span> | <span style="background-color: lightblue">Postcode </span>  |
|-------------|------------|-----------|--------|---------------|------------|
| `4kjHgF0a`    | John       | Smith     | M      | 15/07/1985    | `E1 6AN`     |
| `8bNdEJ3q`    | Jane       | Doe       | F      | 22/03/1990    | `SW1A 1AA`   |
| `1tRkLp9w`    | Michael    | Johnson   | M      | 05/11/1978    | `NW1 4RY`    |
| `9yXzPm6v`    | Emily      | Williams  | F      | 10/09/1995    | `BB1 6NZ`    |
| `2gVfDs5x`    | David      | Brown     | M      | 12/04/1982    | `M3 4JR`     |
| `7uNbHj4z`    | Sarah      | Miller    | F      | 01/12/1998    | `EC2V 7AD`   |
| `3dGcJe1k`    | Robert     | Davis     | M      | 25/06/1973    | `NE1 7RU`    |
| `5qAzWs8e`    | Lisa       | Taylor    | F      | 18/02/1989    | `OX1 1HB`    |
| `6fRvTk2y`    | Matthew    | Anderson  | M      | 09/08/1992    | `G1 1LH`     |
| `0jKiHn7s`    | Amanda     | Lee       | F      | 30/01/1987    | `AB10 1XG`   |


## Pseudonymisation
---
Pseudonymisation is a data protection technique that involves replacing or encrypting personally identifiable information (PII) with pseudonyms or unique identifiers. The purpose is to separate sensitive data from direct identifiers, making it more challenging to identify individuals without additional information. Pseudonymised data can still be linked back to the original identities through the use of additional information held separately.


**Original data, pseudo_id added**


| Hospital_ID | First_Name | Last_Name | Gender | Date_of_Birth | Postcode   | <span style="background-color: yellow">Pseudo_ID</span> |
|-------------|------------|-----------|--------|---------------|------------|-----------|
| `4kjHgF0a`    | John       | Smith     | M      | 15/07/1985    | `E1 6AN`     | 1001      |
| `8bNdEJ3q`    | Jane       | Doe       | F      | 22/03/1990    | `SW1A 1AA `  | 1002      |
| `1tRkLp9w`    | Michael    | Johnson   | M      | 05/11/1978    | `NW1 4RY`    | 1003      |
| `9yXzPm6v`    | Emily      | Williams  | F      | 10/09/1995    | `BB1 6NZ`    | 1004      |
| `2gVfDs5x`    | David      | Brown     | M      | 12/04/1982    | `M3 4JR `    | 1005      |
| `7uNbHj4z`    | Sarah      | Miller    | F      | 01/12/1998    | `EC2V 7AD`  | 1006      |
| `3dGcJe1k`    | Robert     | Davis     | M      | 25/06/1973    | `NE1 7RU`    | 1007      |
| `5qAzWs8e`    | Lisa       | Taylor    | F      | 18/02/1989    | `OX1 1HB`    | 1008      |
| `6fRvTk2y`    | Matthew    | Anderson  | M      | 09/08/1992    | `G1 1LH`     | 1009      |
| `0jKiHn7s`    | Amanda     | Lee       | F      | 30/01/1987    | `AB10 1XG`   | 1010      |
```

**Pseudonymised Data**

The Age column provides a generalised representation of individuals' age without exposing their actual birth dates, reducing the risk of identifying individuals. The Pseudo_ID can be used as a unique identifier to track and analyse data while keeping the original identity of individuals anonymous.

| <span style="background-color: yellow">Pseudo_ID</span> | Age | Gender | Condition                      |
|-----------|-----|--------|--------------------------------|
| 1001      | 37  | M      | Hypertension (High blood pressure) |
| 1002      | 33  | F      | Diabetes mellitus                  |
| 1003      | 44  | M      | Arthritis                          |
| 1004      | 27  | F      | Migraine                           |
| 1005      | 41  | M      | Allergies                          |
| 1006      | 24  | F      | Arthritis                          |
| 1007      | 49  | M      | Diabetes mellitus                  |
| 1008      | 34  | F      | Allergies                          |
| 1009      | 30  | M      | Hypertension (High blood pressure) |
| 1010      | 36  | F      | Migraine                           |



## Anonymisation
---
Anonymisation goes a step further than pseudonymisation by transforming data in such a way that it becomes impossible or highly unlikely to identify individuals even with additional information. Anonymised data is irreversible, and the process aims to remove all identifiable information from the dataset.

For example, if a dataset contains names, addresses, and national insurance numbers, the anonymisation process would involve removing or aggregating those elements to ensure individuals cannot be identified. This could include replacing specific data points with general categories or removing certain fields altogether.

**Anonymised Data**

| Age | Salary |
|-----|--------|
| 35  | 50000  |
| 42  | 60000  |
| 28  | 45000  |
| 31  | 55000  |

**Anonymised data - aggregated**

| Age Group | Total Salary |
|-----------|--------------|
| 18-25     | 120000       |
| 26-35     | 210000       |
| 36-45     | 180000       |
| 46-55     | 240000       |



The goal of anonymisation is to minimise the risk of re-identification while maintaining data utility for research, statistical analysis, and other purposes.

Both pseudonymisation and anonymisation techniques contribute to data privacy and protection. The choice between the two techniques depends on the specific requirements and risks associated with the data processing activities.

### Exercise
For this exercise, we are using 
- the Jupyter notebook [anonymisation.ipynb](./notebooks/anonymisation.ipynb) and
- the dataset [hospital_data.csv](./datasets/hospital_data.csv).

You will be using `Faker` a python library. Analyse the code example and have a look at the Faker documentation.

### Challenge
In the previous exercise you have calculated the 'Age' of a patient. Based on this age, assign each patient to the following Age Groups:

| Age Group |
|-----------|
| 18-25     |
| 26-35     |
| 36-45     |
| 46-55     |

*Hint: Research the internet on 'binning' numerical data with pandas.*

<!-- OMITTED -->

## Considerations
---
There are three main considerations when anonymising data:
1. What needs to be anonymised;
2. How it should be anonymised;
3. Whether it needs password protecting.

## Step-by-step checklist
---

The [UK Data Service](https://ukdataservice.ac.uk/) provides access to a wide range of data, including UK government surveys, longitudinal studies, census data, business data, and qualitative data. They offer support, guidance, and best practices for handling and sharing data. Their guidance is the 'gold standard'. Here is the UK Data Service's step-by-step checklist for anonymising data:

1. Find and highlight direct identifiers
2. Assess indirect identifiers
3. Assess the wider picture
4. Remove (or pseudonymise) direct identifiers.
5. Aggregate or blur (in)direct identifiers.
6. Redact indirect identifiers.
7. Re-assess any remaining disclosure risk.

### 1. Find and highlight direct identifiers
A direct identifier is information which could identify a single individual on its own. Some direct identifiers are completely unique, such as passport numbers, whilst others are not unique but still highly specific, such as name and address.
The first action to take when anonymising data is to find and highlight all direct identifiers in your data. Typically, we would remove these before sharing or working with the data.

### 2. Assess indirect identifiers
Personal data is continuously collected from various sources, including more anonymised and generic data such as GPS, phone, and travel data. Through data analytics, even when data sources are anonymised, the combination of multiple datasets can potentially reveal identifiable information.\
For instance, individual attributes like age, location, or telephone provider may not individually isolate someone, but their combination could uniquely identify an individual.
Indirect identifiers refer to fields that, when combined with other sources, have the potential to uniquely identify individuals.\
Common indirect identifiers include 
- birthplace 
- race
- religion
- weight
- activities
- employment details
- medical information
- education data and 
- financial information.

It is important to assess the potential risk associated with each indirect identifier included in your dataset.

### 3. Assess the wider picture
This step encourages you to take a more holistic view of the data. Run descriptive statistics and cross-tabulate information to find unique cases and rare combinations of variables that could potentially identify an individual in the dataset.\
Use your understanding of the data to think holistically about whether it is possible to isolate individuals from all the other data and documentation available to those who might have access to your dataset.

### 4. Remove (or pseudonymise) direct identifiers.
Unless the people you are sharing data with need the information (and need it for the purposes that it was originally collected) you should remove any direct identifiers from the data. Usually, you should also do this when working with the data yourself to protect the privacy of those individuals as much as possible.
The alternative is to pseudonymise the data. This means replacing all unique identifiers with a new set of random unique identifiers that you hold back when sharing the data. This is sometimes necessary when shared data needs to be merged with other data sources using the direct identifiers as a “key”.

### 5. Aggregate or blur (in)direct identifiers.
You should also minimise the potential for indirect identifiers to isolate single individuals. Two ways to do this include **aggregation** and **blurring**.

**Aggregation** means to provide summary tables for each indirect identifier rather than the original data itself.\
For example, you might provide a table which shows the average responses for people of different ethnicities rather than the actual response of each individual person.

**Blurring** means to convert more precise values into more approximate values.\
For example, you could convert postcodes (e.g. FD12 4RG) into postal sectors (e.g. FD12 4). The postal sectors are less precise and therefore the risk of identification is lower.

### 6. Redact indirect identifiers.
If aggregation or blurring is not possible, then you should simply remove indirect identifiers wherever they could potentially identify a single individual 

### 7. Re-assess any remaining disclosure risk.
Finally, you should re-assess any remaining risks.
As an extra layer of security, you could consider using password protection on any sensitive data that you share with other people or other organisations. This ensures that the information will not be accidentally seen by people without the password.

## Reflective questions
---
The following questions aim to help you to reflect on your responsibilities as a data engineer in a company.

- How can you ensure data privacy and comply with regulations as a data engineer?
- What steps can you take to effectively anonymise data and protect individual identities?
- How can you balance data utility and analysis with the need for data privacy in your role?
- What measures can you implement to enhance data security during the anonymisation process and prevent potential breaches?

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pills%2FPseudonymisation_and_anonymisation.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pills%2FPseudonymisation_and_anonymisation.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pills%2FPseudonymisation_and_anonymisation.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pills%2FPseudonymisation_and_anonymisation.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fintro-to-data-analysis&prefill_File=pills%2FPseudonymisation_and_anonymisation.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
