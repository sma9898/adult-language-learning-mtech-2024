# adult-language-learning-mtech-2024

[Write a detailed README]

## Description of the Dataset

[A brief description of the dataset and any motivating questions you had throughout your analysis.]

**Source:** https://www.kaggle.com/datasets/thedevastator/adult-language-learning-profile/data

(Originally pulled from: https://zenodo.org/records/2863533#.Y9Y3pNJBwUE )

The dataset looks at adult language learners in the Netherlands, with data on their demographics and their language learning process.

Motivating Questions:


## Summary of Steps 

[A summary of the steps you took (cleaning, manipulation, analysis).]

### Data Cleaning
* I used df.duplicated() to identify how many rows were duplicated. I found 883 duplicate rows, which is a small enough portion of the dataset that it would be safe to drop them. However, the data source claims each row is a unique individual. Because logically it *is* possible for different people to have identical information in each column, I believe this claim and kept these rows in my analysis.
* I used df.info() to see how many null values existed in the dataset. I found that there were 1,809 null values in the 'morph' column and 2,016 null values in both the 'new_feat' and 'new_sounds' columns. There was no way to impute these values and this was a small enough portion of the data set, which contains 50,235 rows of data, that I could either leave them in or drop the rows with null values. For this analysis, I chose to drop the rows so I could work with a complete data set.
* I used df.describe() and value_counts() on each of the columns to see if there were any obvious logical or standarization errors with the data. There did not appear to be any.
* I identified some outliers in 4 columns (AaA, LoR, Speaking, and morph) by looking for calculated Z-scores greater than 3. I don't believe these are a result of errors, so I left them in the analysis as-is.

### Data Manipulation

[Justify Data Manipulation steps]
* I created a new DataFrame 'L1_group_df' where I grouped the data by the individual's native language (L1) and sorted the data by the average test score (Speaking) from high to low. This way, I could see whether people with different native languages tended to perform differently on the test.
* I created another DataFrame to look at the average score (Speaking) grouped by gender to see if there was a difference.
* I also added a new column 'Monolingual' which indicated whether a person was monolingual (L2 listed as 'Monolingual') or multilingual (knew at least 2 languages) before beginning to study Dutch.

### Analysis

## Visualizations

[Key insights and figures (include screenshots of your visualizations).]


## Key Insights

[Key insights and figures (include screenshots of your visualizations).]
* German, Swedish, and Norweigian highest average scores (also have low morphological and lexical differences)
* Women scored 19 points higher on the test on average

## Instructions to Run Code

[Instructions on how to run your Python code.]
