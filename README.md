# Box Office Movie analysis
## Project Overview
In this project, I conducted an exploratory data analysis of some of the top Box office movies so as to generate insights for Microsoft who want to join this industry.I then translated my findings into insights and even came up with recommendations that the head of Microsoft's new movie studio should use on deciding the type of movies to create.

## Business Understanding
For Microsoft to better understand the film Industry, they need to answer these questions:
1. **What genres are currently performing the best at the box office?**
2. **What re the common characteristics of the top-grossing films (e.g., budget, cast, director, special effects)?**
3. **Who are the target audiences for these successful films?**
4. **How do different regions vary in terms of their movie preferences?**

## Objectives of the Project
- **Analyze Current Box Office trends:** Examine the type of films that are currently succesful at the box office.
- **Identify Key Film Attributes:** Determine the attributes (e.g., genre, target audience, budget range) of the top-performing films
- **Provide Actionable Insights:** Offer recommendations on the type of films Microsoft should produce in the analysis.

## Data Understanding and Analysis
### Data Source
The data used in this project is from two sources:
**Data\bom.movie_gross.csv - This is a csv file which mainly contains information on Movie titles, the year the movies were released, the studio that created the Movie and also gross earnings made from movies both domestically and foreign.**
**Data\tn.movie_budgets.csv - This is also a csv file similar to the one above only that it has additional information on the movie production budget and the worldwide earnings of the Movies**

### Data Analysis
In this file Data\bom.movie_gross.csv,

```python
df.groupby(["studio", "year"])["domestic_gross"].sum()
``` 
**Here we will group our dataset by Studio that produce the movie, the year the movie was produced and the domestic gains for that year.**

While in Data\tn.movie_budgets.csv file as part of my analysis, I found the gross earnings the found the correlation with production Budget;

```python
budgets['Total_gross'] = budgets['domestic_gross'] + budgets['worldwide_gross']
budgets['Total_gross'].head()
```
```python
correlation = budgets[['production_budget', 'Total_gross']].corr()
correlation
```

***From the correlation analysis, i found that Production budget and Total gross have a correlation of 0.739912 indicating a strong positive correlation. Movies with higher production budgets tend to have higher total gross incomes and vice versa.*** 

### Data Visualization
**Here I used matplotlib to visualize the data which will make it simpler for us to interpret.**

```python
plt.figure(figsize=(15,8))
yearly_domestic_gross.plot(kind='bar', color='skyblue')
plt.title('A Bar Plot showing the Total Domestic  Gross by Year')
plt.xlabel('Year')
plt.ylabel('Total Domestic Gross')
plt.show()
```
![alt text](image.png)

#### From the above bar plot, we can see that the year in which the highest domestic gross income was generated was in 2016 where gross income from the movies was 11,253,653,097 dollars.