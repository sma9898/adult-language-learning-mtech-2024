# Adult Language Learning Sample Final Project

## Description of the Dataset

**Source:** https://zenodo.org/records/2863533#.Y9Y3pNJBwUE (Found through Kaggle)

The dataset looks at adult language learners in the Netherlands, with data on their demographics and their language learning process.

### Motivating Questions:
* What factors are most correlated with differences in test scores?
* Is there a difference in scores across different genders?
* Is there a difference in scores for those who speak more than one language, compared to those who are monolingual?
* How can I use Python to gain insights into a dataset?

## Summary of Steps 

### Data Cleaning
* I used df.duplicated() to identify how many rows were duplicated. I found 883 duplicate rows, which is a small enough portion of the dataset that it would be safe to drop them. However, the data source claims each row is a unique individual. Because logically it *is* possible for different people to have identical information in each column, I believe this claim and kept these rows in my analysis.
* I used df.info() to see how many null values existed in the dataset. I found that there were 1,809 null values in the 'morph' column and 2,016 null values in both the 'new_feat' and 'new_sounds' columns. There was no way to impute these values and this was a small enough portion of the dataset, which contains 50,235 rows of data, that I could either leave them in or drop the rows with null values. For this analysis, I chose to drop the rows so I could work with a complete dataset.
* I used df.describe() and value_counts() on each of the columns to see if there were any obvious logical or standarization errors with the data. There did not appear to be any.
* I identified some outliers in 4 columns (AaA, LoR, Speaking, and morph) by looking for calculated Z-scores greater than 3. I don't believe these are a result of errors, so I left them in the analysis as-is.

### Data Manipulation
* I created a new DataFrame 'L1_group_df' where I grouped the data by the individual's native language (L1) and sorted the data by the average test score (Speaking) from high to low. This way, I could see whether people with different native languages tended to perform differently on the test.
* I created another DataFrame to look at the average score (Speaking) grouped by gender to see if there was a difference.
* I also added a new column 'Monolingual' which indicated whether a person was monolingual (L2 listed as 'Monolingual') or multilingual (knew at least 2 languages) before beginning to study Dutch. I wanted to see if this impacted their ability to learn Dutch.

### Analysis
* The ages of people in this dataset range from 0 to 88 years old, with an average age of 26. The mean (26.5) and median (26) are very similar and the mode is 25, so there doesn't seem to be significant skew.
* The average length of residence is 3.9 years with 75% of respondants having a residence of 5 years or less. Though there are a few outliers, including at least one person who has resided in the Netherlands for 59 years.
* The column that has the strongest correlation with test score (Speaking) is lex at -0.439832, which is a moderate negative correlation. The other features most correlated with Speaking are Enroll, morph, new_feat, and new_sounds. All but Enroll are measures of how different Dutch is from the individual's native language (L1) and are significantly correlated with one another.

## Visualizations
![image](https://github.com/user-attachments/assets/900c3a8b-af9b-4e0e-87f6-4040230acae2)
![image](https://github.com/user-attachments/assets/ed7af91b-aea5-48b5-9da6-4fd04e8f6160)
![image](https://github.com/user-attachments/assets/df4ef168-ed2d-4442-861c-0a9ba13778ee)
![image](https://github.com/user-attachments/assets/609667d4-b572-4f2e-9e0e-b52818e8fee8)
![image](https://github.com/user-attachments/assets/c121d28d-42b3-46f6-86cc-5b9480054db6)
![image](https://github.com/user-attachments/assets/fe8cfcaa-6757-44af-aca0-106520b2cfaf)
![image](https://github.com/user-attachments/assets/e6b2ff66-df71-4afa-99b5-4d4224e7018d)

## Key Insights
* Participants who spoke German, Swedish, or Norwegian as their native language had the highest average scores. Notably, these languages also have low morphological and lexical differences compared to Dutch.
* Women scored 19 points higher on the test on average compared to men.
* 81.9% of the people in this study spoke at least 2 languages before learning Dutch, but this did not have a noticeable effect on their test scores compared to monolingual people learning Dutch (9 points difference on average).
* Test scores were higher for individuals who spoke languages that had fewer morphological, lexical, and phonological similarities to Dutch.
* The statistical analysis on the correlation between features in this dataset seems to indicate that the differences in a person's native language compared to Dutch are the factors that are most correlated with how well that person performs on the test.

## Instructions to Run Code
1. Open Python script (Final_Project.ipynb) in Google Colab
2. Upload data file (stex.csv) to Google Colab notebook
3. Run Python script in Google Colab
