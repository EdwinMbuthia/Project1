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
budgets['International_gross'] = budgets['worldwide_gross']-budgets['domestic_gross'] #Here we've created an international column to represent the earnings from the rest of the world.
```
```python
budgets_df = budgets[['movie', 'production_budget', 'domestic_gross', 'International_gross']]
```

***From the correlation analysis, i found that Production budget and Worldwide gross have a correlation of 0.739912 indicating a strong positive correlation. Movies with higher production budgets tend to have higher worldwide gross incomes and vice versa.*** 

### Data Visualization
**Here I used matplotlib to visualize the data which will make it simpler for us to interpret.**

Data Visualization - Data\bom.movie_gross.csv
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

Data Visualization - Data\tn.movie_budgets.csv
```python
plt.figure(figsize=(15,8))
plt.bar(top_5_movies['movie'], top_5_movies['International_gross'], color='skyblue')
plt.xlabel('Movie')
plt.ylabel('International_gross')
plt.title('International_gross earnings for Top 5 Movies')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
![alt text](image-1.png)

This barplot shows the International gross earnings of the top_5_movies on the Box office.

```python
plt.figure(figsize=(15,8))
plt.bar(top_5_movies['movie'], top_5_movies['production_budget'], color='skyblue')
plt.xlabel('Movie')
plt.ylabel('Production Budget')
plt.title('Production Budget for Top 5 Movies highest earning Movies')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
![alt text](image-3.png)

This barplot shows the production budget spent on the top_5_movies on the Box office.

```python
plt.figure(figsize=(15,8))
plt.bar(top_5_movies['movie'], top_5_movies['domestic_gross'], color='skyblue')
plt.xlabel('Movie')
plt.ylabel('Domestic Gross')
plt.title('Domestic Grossfor Top 5 Movies highest earning Movies')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
![alt text](image-2.png)

This barplot shows the domestic earnings from the top_5_movies on the Box office.

## Conclusion
### Findings based on genre
##### From the top_5_movies based on World wide earnings, Microsoft should create Science Fiction Movies as they are the highest earners.Of the top_5_movies from the bar graphs above, it is only Titanic that isn't a Science Fiction film the rest are SciFi movies.Below is a breakdown of the genres of the top_5_movies in terms of their Worldwide earnings at the Box Office:
- **Avatar - Science Fiction**
- **Titanic - Romance, Disaster, Historical Drama**
- **Star wars Ep.7: The Force Awakens - Science, Action,Fantasy**
- **Avengers: Infinity War - Science Fiction, Action, Drama**
- **Jurassic World - Science Fiction, Action, Adventure**

##### The other most recommendable genre that Microsoft should produce is Action movies as they are also doing well at the Box Office.

### Findings based on Production Budget
##### We can see that production budget of a movie is quite essential in determining the amount of earnings a Movie will make. For instance, the movie Avatar had a production budget of 425 million dollars and the worldwide gross earnings from the movie were 2.7 billion dollars. Though this might not be the only factor for these high earnings, it is quite essential that Microsoft sets aside a proper production budget should they venture into production of Movies.

### Findings based on Target Market
##### When  we compare the bar graphs on the International gross earnings and Domestic earnings, we can deduce that alot of earnings for most of the movies are from International markets. Therefore, in as much as catering to the Domestic audience is essential, Microsoft should create Movies with an International appeal so as to attract foreign audience.
