---
layout: page
title: Is timing everything ?
subtitle: A Data-Driven Dive into Movie Release Strategies and Success
cover-img: /assets/img/season_movie.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
use-site-title: true
---

Sometimes, despite having all the pieces in place and doing everything right, success seems elusive. It's often a game of patience. Hard work is undoubtedly a significant factor in achieving success, but there's another crucial element at play – timing. It's about being in the right place at the right moment, seizing opportunities as they arise, and connecting with others at just the right time.

Movies reflect this aspect of life brilliantly. The impact of a film on us depends not just on its content, but also on when we watch it. The right movie at the right time can make us laugh, cry, or reflect. It's a personal experience, unique to each viewer.

But let's zoom out from the individual experience to the broader perspective of the movie industry. Have you ever considered how the timing of a movie release might be a key to its success? In our story, 'Is Timing Everything?', we delve into the CBU movie dataset to explore this fascinating aspect. We'll look at how the release dates of movies influence their success and reception. So, whether you're a film lover, a data geek, or just someone intrigued by the behind-the-scenes of the movie world, join us. We'll dive into patterns, make predictions, and maybe even unearth some insights useful for filmmakers and the movie industry. Life is often about luck, but what if you could sway it in your favor? What if you knew exactly how to time the release of your masterpiece? Ready to make yourself lucky? Let's begin: Action!

_______________________________________________________________

# Release Dates and Movie Genres - Orchestrating the Perfect Season (Question 1)

Let's dive into the intriguing interplay between movie genres and their release calendars. Are horror films naturally drawn to Halloween? Do summer months exclusively belong to action-packed blockbusters? In this part of our story, we'll try to see if there are any recurring patterns between a film's genre and its release timing within a year. Do these rhythms exist, and if so, do they change depending on where the movie is released? This exploration isn't just about identifying patterns; it's about understanding whether these insights can help us predict the genre of upcoming film releases in different seasons. It's time to discover if there's a secret rhythm dictating when different genres of movies make their grand entrance on the big screen.

## 1.1 Exploration

For this analysis, we will focus on the film genres, the release period of the year, and the locations where they are released.
We will also investigate patterns that may exist between the time of year and the number of film releases.

### 1.1.2. Annual periodicity and film genres
Let's investigate the possible existence of a correlation between annual periodicity and film genres. It is also relevant to examine the existence of trends that are not dependent on the film genre or location. To provide us with an initial idea, we compute the monthly average of films released, considering all genres and locations. This gives us an overview of the distribution of film releases throughout the seasons.

![1_monthly_movie_count.png](./assets/img/1_monthly_movie_count.png) 

This bar chart allows us to conclude that the distribution of films throughout the year is not uniform; for instance, the summer months appear to have fewer releases than others. Therefore, it is necessary to differentiate, for each genre, whether the trend is driven by the overall distribution of films throughout the year or if it is specific to certain film genres.

### 1.1.3. Repartition of the main genre
In our dataset, we have a wide variety of genres represented.  For now, we will focus on the five most represented genres in the dataset.
Let's observe the representation of film genres in our resulting dataset.

![1_movie_genre_dist_pie.png](./assets/img/1_movie_genre_dist_pie.png) 

The 'drama' genre predominates significantly, while the other genres are fairly balanced among themselves.Now, we will examine the distribution of films across months based on their genres.

TONS OF GRAPHS : WHAT TO DO ?

We observe significantly different distributions among genres. Action films appear to have a relatively uniform distribution throughout the year. It's worth noting that action is the only genre that doesn't experience a decline during the summer, which contradicts the general trend. It's important to mention that for our final word, correlation tests will be considered to confirm whether or not months can have an impact on certain genres

### 1.1.4. Repartition of the continent

In our dataset, we have a wide range of countries represented. To study the link between location and the distribution of release months, we will group these countries by their continents.

![1_movie_dist_continent_pie.png](./assets/img/1_movie_dist_continent_pie.png) 

The pie chart shows us the proportion of each continent in our dataset. We observe that three continents represent almost the entirety of our dataset, so we will focus on these.


### 1.1.5. Setting a Threshold for Data Inclusion

Before continuing, it is important to take into account and important factor, the distribution of the number of data by year.

HISTOGRAM INTERACTIVE 

This histogram displays the distribution of the number of films released each year, regardless of their genre or release location. We observe a significant increase over the years. To maintain the relevance of our analysis, we have established a threshold of 200 films per year as a selection criterion for the years to be included in our study. After applying this criterion, we selected the most recent year that did not meet it and then excluded all data prior to that date. This approach ensures that our dataset remains statistically relevant and consistent over time.

Furthermore, upon examining this graph, we notice that after 2009, the number of films decreases significantly in the dataset. This trend appears counterintuitive and may be attributed to the difficulty of obtaining recent data (the dataset was published in 2012). To avoid potential data bias, we are focusing on data up to the year 2009.

## 1.2. Comprehensive Seasonality Analysis Across All Genres and Locations

Let's now investigate the possibility of seasonality in film releases, regardless of genre or location, over time. 

### 1.2.1. Monthly Cinematic Release Dynamics: Histogram Analysis of Release Rates

We conduct a thorough analysis with the aim of predicting the percentage of films released each year during a specific month.

![1_mean_percent_release_month_histo.png](./assets/img/1_mean_percent_release_month_histo.png) 

Upon examining this plot, we observe that the percentage of film releases per month is not evenly distributed throughout the year. This leads us to increasingly consider the hypothesis that there may be seasonality in film releases over the course of the year. However, we must exercise caution with this type of analysis because it's possible that if there is any seasonality in film releases, it may not have been consistent over time. For example, there might have been a pattern in the last 10 years, such as fewer film releases in July, but this may not have been the case in earlier years.

To investigate this further, we will utilize the Canova Hansen Test.

### 1.2.2. Seasonal Pattern Stability: Canova-Hansen Tests on Time Series Data

In the Canova-Hansen test, the 'm' parameter represents the data's seasonal period, for example, 12 for monthly data and 4 for quarterly data. A result of 'D = 1' indicates the need for seasonal differentiation to stabilize the seasonal pattern, suggesting variable seasonality in the data.

The result of our Canova-Hansen Test is **1** which reveals that the seasonal patterns in our data are not constant over the analyzed period. To deepen our understanding, we will calculate the autocorrelation of our data at various time lags. This analysis will enable us to determine how long a specific seasonal pattern persists in our dataset, providing more precise insights into the underlying temporal dynamics and the persistence of seasonal trends.

### 1.2.3. Analysis of Seasonal Pattern Persistence : Autocorrelogramme

An autocorrelation plot, or autocorrelogram, is a vital tool in time series analysis, used for visualizing and measuring autocorrelation, i.e., the relationship between a time series and its past values at different lags.

**Interpretation**
- **Significant Peaks**: A peak in the autocorrelogram at a specific lag indicates significant autocorrelation at that lag. Peaks beyond the confidence bounds suggest statistically significant autocorrelation.

- **Seasonality and Temporal Dependence**: Regular peaks at multiples of a specific period indicate seasonality. For example, annual peaks in monthly data would appear every 12 months, revealing a yearly seasonal trend.

![1_autocorrelation_graph.png](./assets/img/1_autocorrelation_graph.png) 

#### Analysis of the Autocorrelation plot:

1. **Initial Peak**: The first lag exhibits a peak close to 1, which is expected as it represents the correlation of the series with itself.

2. **Subsequent Lags**: Several spikes are observed that exceed the blue shaded area, indicating statistical significance. These prominent peaks suggest significant autocorrelation at those lags.

3. **Seasonal Patterns**: Notable peaks appear at regular intervals of 12 months (1 year) and persist beyond the confidence intervals up to a lag of 17 years. This implies two important findings: 

   - The significant spikes at lags corresponding to multiples of 12 months (1 year, 2 years, etc.) suggest a strong and consistent annual seasonality in the data.
   
   - The presence of these significant peaks at regular intervals, especially up to a lag of 17 years, indicates that the seasonal effect is not only strong but also has a long-term influence on the series. This suggests that past values, not just from the previous year but several years back, influence the current values.

**Conclusion**: We can assert two key findings: there is an annual seasonality in our data, as evidenced by the significant peaks occurring every 12 months in our autocorrelation plot. Furthermore, it seems that the seasonal effect has a long-term impact on the years, exhibiting significant correlations up to 17 years later.
Additionally, the fact that this autocorrelation is no longer significant after 17 years provides us with additional information: seasonality has evolved over time, aligning with the implications of the Canova-Hansen Test result.

### 1.2.4. Decoding Trends and Seasonality: Seasonality Visualization

Now that we know that seasonality has changed over time and that patterns tend to change approximately every 17 years, we will attempt to visualize these differences. To do so, we extract two datasets from our data. The first contains the most recent 17 years [1993, 2009], and the second the preceding 17 years [1976, 1992]. Subsequently, we conduct a Canova-Hansen test to ensure that among these datasets, the seasonal motif remains stable.

The result of the Canova-Hansen Test for the the past years is 0, and that is also true for the recent years.

Great! Now that we've ensured this pattern is stable, we'll attempt to extract the seasonality from our two different datasets. To do this, we'll use the highly useful function `seasonal_decompose` from `statsmodels`. This function allows us to decompose our time series into three components:

**The trend component** outlines the long-term direction of movie release data, smoothing out temporary changes and showing if the industry is growing, shrinking, or holding steady. In our multiplicative model, this trend's influence may vary at different data levels.

**The seasonal component** detects recurring patterns within set timeframes, like annual cycles in monthly data, indicating when releases typically spike or dip. This effect scales with the data, meaning it can make the natural highs and lows more pronounced if the overall trend is rising.

**The residual component** is what's left unexplained after accounting for trend and seasonality, representing random variations. In this model, residuals are calculated by dividing the data by both trend and seasonal factors. Significant residuals might suggest unusual events impacting movie releases that the model doesn't otherwise account for.

![1_season_decomposition.png](./assets/img/1_season_decomposition.png)

Without surprise, we observe that the overall trend increases for both the movies from [1976-1992] and those from [1993-2009]. We also notice that the seasonal patterns are different. Let's try to visualize them in more detail.

![1_seasonal_effect_histos.png](./assets/img/1_seasonal_effect_histos.png)

Indeed, we observe that the seasonal patterns have changed between these two periods. The more recent period seems to exhibit more pronounced differences among the months of the year compared to the previous period. For instance, in the most recent period, the month of July has a multiplicative factor relative to the trend of about 0.6, while in the past period, it was 0.8. On the other hand, the month of September is well above the general trend in the most recent period, at 1.6 times the trend, whereas in the past period, it was only 1.2.

In conclusion, it's fascinating to observe how seasonal patterns evolve over time. We notice significant differences. The most recent period in our dataset appears to exhibit more pronounced variations than before, suggesting that these month-to-month differences seem to intensify over time.

## 1.3. Detailed Study by Genre and Location

In this section, we will examine whether there are differences in seasonality between film genres and locations. To do this, we will work exclusively with data from the ten most recent years in our dataset.

### 1.3.1. Monthly Cinematic Release Dynamics: Histogram Analysis of Release Months depending on Genre and Location

In this section, we explore the potential presence of seasonality in film releases, considering both genre and location, across time. To do so, we will perform a similar analysis to that in Section 2.1, while distinctly separating genres and locations.

TABLE

INTERRACTIVE PLOT

### 1.3.2. Seasonal Stability Diagnostics: Canova-Hansen Testing by Category and Region

TABLE 

It appears that the seasonal patterns within genres and locations remain stable throughout the selected period [1993-2009]. It's worth noting that this period was initially chosen in section 2.3 because the seasonal patterns, encompassing all genres and locations, were stable during that time. This latest analysis simply demonstrates that when we subdivide our dataset by genre and location, any intrinsic patterns within these subdatasets also remain consistent over the same period.

### 1.3.2. Seasonal Stability Diagnostics: Canova-Hansen Testing by Category and Region
To further delve into this analysis, we will calculate autocorrelation, as done in section 2.3. However, this time, we will separate the film genres and continents.

TABLE

It appears that the seasonal patterns within genres and locations remain stable throughout the selected period [1993-2009]. It's worth noting that this period was initially chosen in section 2.3 because the seasonal patterns, encompassing all genres and locations, were stable during that time. This latest analysis simply demonstrates that when we subdivide our dataset by genre and location, any intrinsic patterns within these subdatasets also remain consistent over the same period.

To further delve into this analysis, we will calculate autocorrelation, as done in section 2.3. However, this time, we will separate the film genres and continents.

![1_matrix_genre_continent.png](./assets/img/1_matrix_genre_continent.png)

The heatmap analysis uncovers intriguing patterns in movie release timing, showing that the predictability of release patterns varies by genre and region. For example, action movies in North America do not show a consistent annual pattern, suggesting their release timings are varied year to year.

On the other hand, dramas, especially in Europe and North America, have a strong and consistent annual release pattern that can persist for up to four years, indicating a predictable seasonal trend in these regions.

Overall, Asia displays the least predictability in movie release patterns, while Europe and North America exhibit more consistency according to genre. The analysis also highlights that while some genres follow strong seasonal trends, others show no such regularity.

### 1.3.3. Decoding Trends and Seasonality : by Genre Category and Region

Similarly to the analysis conducted in point 2, we now focus on examining the seasonal multiplicative factors. The objective here is to highlight, for genres and locations exhibiting seasonal patterns as identified in point 3.2, the months that stand out from the general trend and contribute to the formation of these patterns.

![1_heatmap_seasonality.png](./assets/img/1_heatmap_seasonality.png)

The drama genre presents a fascinating case study. While it shows an overall annual seasonality, a closer look reveals distinct regional differences. In Europe, May stands out as a popular month for drama releases, with a significant uptick compared to the average, while this month is not as prominent for drama releases in North America. Conversely, January is more significant for drama releases in North America than in Europe.

Both regions, however, see a surge in drama releases during June and July and a dip in September. This analysis confirms that while annual seasonal patterns do exist for certain genres and locations, they also display unique regional variations.

## Transition :

As our data story unfolds, it's clear that certain movie genres do have their preferred release times. But why? While it's straightforward for Christmas and Halloween movies, other genres aren't as clear-cut. Perhaps production companies are tuning into the public's mood, providing just the right kind of film at just the right time. Or maybe, they've learned from experience that release timing can significantly influence a film's success. After all, isn't that a key goal for them - to make their movies as successful as possible? But here's a thought - what exactly defines success in the film industry? Is it the accolades from peers or the applause from the audience? Well, it's time to explore both. To satisfy the film aficionados among us, let's first dive into how the release calendar impacts the most prestigious accolade in the movie world – the Oscar.

_______________________________________________________________

# Setting Your Watch for the Red Carpet - How Timing Influences Oscar Success (Question 2)

Now, as we roll out the red carpet, it's time to see how timing influences a movie's journey to Oscar glory. Is there a 'golden month' for releasing a film that could increase its chances of capturing that coveted golden statue? In this part of our exploration, we will try to see which factors impact a movie's success, especially in terms of its likelihood to win an Oscar. Does release timing play a crucial role, and has its effect evolved over time? We're also going to delve into whether it's possible to predict a film's Oscar odds based on various factors, including its release month, the country of origin, language, and more. Let's discover the intricate dance between the calendar and the Oscars.  

### 2.1 Overview
There is no shortcut to win the crown. However, good timing makes an easier way! We can sometimes observe that winning movies are not always promised to be the best. While opinions on the quality of movies can vary, one example often cited as a movie with mixed critical reception that still won multiple Oscars is "Crash" (2004). Directed by Paul Haggis, it won the Academy Award for Best Picture at the 78th Academy Awards. However, its victory was met with controversy, as some critics and viewers felt that other films, such as "Brokeback Mountain," were more deserving. Another example is "The Greatest Show on Earth" (1952) directed by Cecil B. DeMille. This circus drama won the Academy Award for Best Picture at the 25th Academy Awards. While it achieved commercial success, it wasn't universally praised by critics and has received a quite low IMDb rating of only 6.5/10.  

Among other factors, We will ask, if the release timing plays a role in winning an Oscar prize. We first have a look at how the movies with different release months are distributed in the Oscar selection.  

![Release_Month_Distribution](./assets/img/Release_Month_Distribution.png)  

The imbalanced distribution indicates that we can explore how timing poses an impact on the possibility of winning an Oscar. For example, why movies released in December are significantly more than in other months?  

### 2.2 Level I: Entry to Oscar selection
As a bright pearl in the film industry, the Oscar Prize favors only the most successful movies with profound thinking and artistic value. Due to the fierce competition for final awards, many good movies cannot eventually get the Oscar prize, but getting selected as Oscar candidates is also an amazing achievement. Therefore, directors holding films with aspirations for the Oscar awards want to ask, if an optimal release timing can help them to win in the Oscar selection more easily. Generally, we can inspect the ratios of selection in each month. To view the results more clearly, we run a k-means clustering for release months.  

![Selection_Kmeans](./assets/img/Selection_Kmeans.png)

From the graph, the optimal timings for entering Oscar selection are December and June, while movies released from January to April are harder to win the favor of the judges.

### 2.3 Level II: Oscar Winner
Do you know, that only **17.35%** nominated movies successfully take home Oscar awards! And thinking about the low selection ratio, winners need not only good quality films but also some good luck.  

If a director has produced a film expected to be highly praised and is confident that this movie can be selected for Oscar grading for sure, when is the optimal timing in this case? Is it the same as timing for Level I players? We investigated it by clustering the winning ratio in the Oscar selection dataset.  

![Win_Kmeans](./assets/img/Win_Kmeans.png)  

The results reveal that the optimal timing is shifted to January and May, and December is now a very bad choice, only better than June and July.  

How does the winning probability change over the years?  

![Dynamic Graph: Oscar Probability over Years]
![Oscar_Probability_over_Years](./assets/img/Oscar Probability over Years.png)

### 2.4 Confounders: Locations and Languages
Except for the timing, other factors may influence the winning probability as well. Here, we can take locations and languages into account.  

We first check their percentage in the selected movies dataset.  
![Movie_Countries_Selected](./assets/img/Movie_Countries_Selected.png)
![Movie_Languages_Selected](./assets/img/Movie_Languages_Selected.png)

Then, for the winners:
![Movie_Countries_Win](./assets/img/Movie_Countries_Win.png)
![Movie_Languages_Win](./assets/img/Movie_Languages_Win.png)

They show the phenomenon that US movies and English movies take a predominant majority because they are mostly overlapping. We therefore assume that the influence of languages can be covered in location influence. For simplicity, we convert the countries to continents. 

![Win_Possibility_per_Continent](./assets/img/Win_Possibility_per_Continent.png)

It presents that the most intense competition happens in North American movies. Even though their number is large in absolute value, it is never easy for them to win Oscar awards. In contrast, each Oceanian movie selected has a 40% winning probability.  

Based on this, we suggest that **common** North American directors, with the wish to win Oscar prizes, should generally consider releasing new movies in January and May. For **common** Australian directors, they should release the films in December and June.

As a detailed exploration, we run clustering on the continental subsets to evaluate the chance of winning an Oscar after the nomination. 

![Continent_Clustering](./assets/img/Continent_Clustering.png)

Then we can advise **successful directors** who promise to have Oscar-selected movies: 
- for American and European movies, the general suggestion in Level II  (January) still holds.
- despite the limited data, we are reluctant to say that, for Asian movies, the optimal timings are March, August, and November, while for Oceanian movies November is the only best time
- for African and South American movies, we cannot conclude anything without extra data.

Intuitively, this is shown in the heat map below.
![Oscar_Heatmap](./assets/img/Oscar_Heatmap.png)

## 2.5 Box Office Revenue

To continue our analysis of research question 2, we now delve into the other factors impacting a movie's success. We start by looking at the box office revenue of the movies in our dataset. Our insight leads us to believe that higher box office revenues are correlated with a higher probability of winning an Oscar, which we will test via statistical analysis.  

Let us first plot the box office revenue of movies based on whether they received an Oscar or not.  

![Oscar_Box](./assets/img/Oscar_Box.png)

Mean Box Office Revenue (Oscar Winners): $141.49 million  
Standard Deviation Box Office Revenue (Oscar Winners): $274.32 million  

Mean Box Office Revenue (Non-Winners): $94.29 million  
Standard Deviation Box Office Revenue (Non-Winners): $164.44 million  

The difference in Mean Box Office Revenue between Winners and Non-Winners: $47.20 million  

As shown by the box plot and the statistics of our movies' box office revenues, we can see that the average and median box office revenue of movies that received an Oscar is higher than the average box office revenue of movies that did not receive an Oscar. We also notice that the standard deviation of the box office revenue of movies that received an Oscar is much higher than for those that did not, indicating more variability in this category.  

Indeed, if we compare the differences between the highest and lowest-grossing movies that have received an Oscar, we notice a huge difference as shown below. Movies such as "The Times of Harvey Milk" received the Oscars for Best Documentary Feature in 1984 with a box office revenue of 29,802 USD, while movies such as "Avatar" received the Oscars for Art Direction in 2009 with a box office revenue of 2,782,275,172 USD. This indicates that the Oscars Awards do not necessarily reflect the success of a movie, which can often be the case for movies that are not blockbusters.  

To test whether the difference in box office revenue is statistically significant, we will perform a Welch's t-test. This test is used to test the null hypothesis that two populations have equal means. It is an adaptation of the Student's t-test and is more reliable when the two samples have unequal variances and unequal sample sizes.  

The key findings of this analysis are as follows:  

1) T-test Results:  

- T-test statistic: 3.49  
- T-test p-value: 0.0005  

Conclusion: The t-test results reveal a substantial difference in box office revenue between movies that received Oscars and those that did not. The low p-value of 0.0005 indicates a high level of statistical significance. This suggests that the observed difference in box office revenue is unlikely to have occurred by random chance.  

2) Correlation Analysis:  

- Correlation coefficient: 0.09  
- Correlation p-value: 0.0005  

Conclusion: The correlation analysis indicates a significant positive correlation (coefficient of 0.09) between box office revenue and the number of Oscars won. The low p-value of 0.0005 reinforces the statistical significance of this positive correlation. Therefore, higher box office revenue is associated with an increased likelihood of receiving Oscars.  

Our analysis provides compelling evidence supporting a clear relationship between box office success and Oscar recognition. The statistically significant t-test results affirm that movies with Oscars differ significantly in terms of box office revenue from those without Oscars. Additionally, the positive correlation observed further emphasizes that higher box office revenue is positively linked to an increased likelihood of receiving Oscars. This underscores the influential role of commercial success in garnering industry acclaim and recognition.  

However, as we have shown previously, it is important to notice that the Oscars do not necessarily reflect the success of a movie. Indeed, the Oscars can be awarded to movies that are not blockbusters. This is why we will now look at the ratings of the movies in our dataset to see if they are correlated with the Oscars.  

## 2.6 Ratings

We will now conduct a similar analysis to the one we performed for box office revenue, but this time for ratings. We will start by plotting the ratings of movies based on whether they received an Oscar or not.  


Mean Average Vote (Oscar Winners): 6.89  
Standard Deviation Average Vote (Oscar Winners): 0.92  

Mean Average Vote (Non-Winners): 6.59  
Standard Deviation Average Vote (Non-Winners): 0.92  

The difference in Mean Average Vote between Winners and Non-Winners: 0.29  

Once again, we can see that movies that received an Oscar have a higher average and median rating than movies that did not receive an Oscar. We also notice that the standard deviation of the ratings of movies that received an Oscar is higher than for those that did not, indicating more variability in this category, as noticed for the box office revenue.

To test whether the difference in ratings is statistically significant, we once again performed a Welch's t-test.  

The key findings of this analysis are as follows:  

1) T-test Results:  

- T-test statistic: 5.77  
- T-test p-value: 8.99e-09  

Conclusion: The t-test results indicate a substantial difference in average ratings between movies that won Oscars and those that did not. The extremely low p-value of 8.99e-09 underscores the high level of statistical significance. This implies that the observed disparity in average ratings is highly unlikely to have occurred by random chance.  

2) Correlation Analysis:  

- Correlation coefficient: 0.12  
- Correlation p-value: 8.99e-09  

Conclusion: The correlation analysis reveals a significant positive correlation (coefficient of 0.12) between average ratings and the likelihood of winning an Oscar. The extremely low p-value of 8.99e-09 emphasizes the statistical significance of this positive correlation. Therefore, higher average ratings are associated with an increased likelihood of winning the Oscars.  

In Summary:  

Our analysis provides compelling evidence supporting a clear relationship between average ratings and Oscar recognition. The statistically significant t-test results affirm that movies with Oscars differ significantly in terms of average ratings from those without Oscars. The positive correlation observed further indicates that higher average ratings are positively linked to an increased likelihood of winning the Oscars. This underscores the importance of critical acclaim and audience appreciation in influencing industry recognition.  

Associated with our analysis of box office revenue, this statistical test and the measures of our ratings prove once again the importance of a movie's sucess in its likelihood of receiving awards. However, as we have shown previously, it is important to notice that the movies that have received Oscars can divert from these assumptions, receiving low ratings and box office revenue. This is mostly due to artistic opinions directing the awards designations, which can be very different from the public opinion, as well as categories. Movies such as documentaries or foreign ones are often less likely to gross high revenues or receive high ratings, but can still be awarded Oscars. We show these deviations in the following section.  

![Oscar_Category_Box](./assets/img/Oscar_Category_Box.png)
![Oscar_Vote_Box](./assets/img/Oscar_Vote_Box.png)

As we can see from the two box plots shown above, there is a significant difference in box office revenue and ratings between movies that received Oscars based on their category. Movies with Oscars such as Best Actress (in general) or Best Documentary generally received lower box office revenue and ratings than movies with Oscars such as Best Short Film or Actor. We also notice that the best documentary categories showcase an especially high variability in box office revenue and ratings, which is not the case for the best short film category. All these features indicate thus once again the biases that can be shown in the Oscars awards, which are not always correlated with the success of a movie, even though on a general basis, the Oscars are awarded to movies that have a higher box office revenue and ratings.  

#### **Conclusion:** 

USA is the country of most movies in the dataset, and the majority of movies are in English. While the correlation between release month and whether the movie wins an Oscar award is weak, release timing might still be a significant factor influencing the success of the movie. 

#### Transition :

Alright, film enthusiasts, brace yourselves for a bit of a reality check. Let's face it - are Oscar-winning movies always the ones we enjoy the most? Think about it. We know the superhero blockbusters aren't exactly Oscar bait, but come on, how good was the latest Spiderman? With that in mind, let's shift our focus from the glittering Oscars to the wider world of box office hits and audience favorites. After all, there's more to movie success than just golden statues.

_______________________________________________________________

# Box Office and ratings – Timing the Public's Pulse (Question 3)

As we continue our quest to discover if a movie's success can be timed, we now turn to the big question: how does the release timing impact a movie's box office success and public appeal? We're about to connect the dots between calendars, cash, and crowds. For this, we'll delve into the box office, which essentially measures the total revenue a movie earns from ticket sales. It's a fair assumption that the more people flock to see a movie, the more it resonates with the general public.

But that's not the only metric we're considering. We're also looking at how viewers rate movies, another crucial indicator of public opinion.

In this part, we will try to see how the release month of a movie influences its overall success and popularity. We'll examine this through various lenses – box office revenues, viewer votes, and ratings, while also considering how the quality of data documentation has evolved over the years. Let's dive into this multifaceted analysis and see what the numbers reveal about timing and movie success.

### 3.1. Ratings Versus Revenue – Does a "bad movie" makes less money than a "better" one ?
First, let's tackle the correlation between ratings and revenue. It seems intuitive that higher ratings should mean more money, right? Well, our data tells a more nuanced story. We'll explore why movies with mediocre ratings don't necessarily earn less, and how those with top ratings don't always hit the jackpot in terms of revenue. It's a complex equation where excellence in ratings doesn't always translate into box office gold.
### 3.2. Timing and Ratings – Searching for a Pattern
Next, we look at whether there's a link between when a movie is released and the ratings it receives. Does a summer blockbuster get rated differently from a cozy winter flick? Our findings might surprise you, as we unravel the (non)relationship between release months and how viewers rate these films.
### 3.3. Box Office Timing – Identifying the Lucrative times
#### 3.3.1. By Month – The Monthly Box Office Cycle
Let's break down the box office cycle month by month. We'll analyze which months are box office magnets, attracting audiences in droves, and which ones seem to be stuck in a cinematic slump. Our data suggests that not all months are created equal when it comes to raking in the revenue.
#### 3.3.2. By Season – The Seasonal Box Office Trends
Zooming out, we'll assess box office performance by season. Is summer really the blockbuster champion? Does winter bring more than just the holiday spirit to theaters? We'll see how each season stacks up in the race for box office success.

### 3.1. Ratings Versus Revenue – Does a "bad movie" makes less money than a "better" one ?
![Rating_Heatmap](./assets/img/Rating_Heatmap.png)

Using the color bar scale for movie ratings that range from 5.6 to 6.6, we can draw specific conclusions from the first heatmap, which shows the relationship between movie ratings and release months across different genres:  

Consistent Ratings Across Genres: The overall range of ratings is relatively narrow (one point difference from the lowest to the highest), which suggests that there is not a dramatic fluctuation in movie ratings based on release month. This indicates a relative consistency in how audiences rate movies across different times of the year.  

Slight Variations Within Genres: Within individual genres, there are slight variations in ratings across different months. For example, dramas and thrillers show a slightly darker shade in the later months of the year, which might indicate a small increase in ratings for these genres during that period. This could be due to a variety of factors, such as the release of more award-contending films during the end-of-year "Oscar season."  

No Extreme Seasonal Bias: Since the color variations are mild, we can conclude that there is no extreme seasonal bias in movie ratings. While some months may yield slightly higher ratings for certain genres, the impact of release timing on ratings is not overly pronounced.  

![Vote_Correlation](./assets/img/Vote_Correlation.png)


Now, with the color bar scale for the number of votes, which ranges from 10,000 to 70,000, let's analyze the second heatmap that shows the correlation between the number of votes and release months for different movie genres:  

Votes Distribution Across Months:  

Lower Engagement Periods:  
Lighter shades, indicating lower numbers of votes, appear in some months for various genres. For example, comedies and romantic films show a dip in votes during certain periods, possibly when fewer films of these genres are released or when these genres are less popular.  


Votes Distribution Across Months:  

Some genres, such as action and drama, show higher numbers of votes in certain months, as indicated by the darker blue colors. This could suggest that these genres are more popular during these months, possibly due to holiday releases or summer blockbusters which typically draw more viewers.  


Strategic Release Decisions:  

Movie studios might analyze these trends to schedule the release of films in genres that tend to receive more votes during specific months. For example, if action movies receive more votes (indicating popularity) during summer months, studios might aim to release their big-budget action films during that period.

Seasonal Patterns:  

Despite the overall consistency, there are slight variations within genres across different months that are common to both ratings and votes. For instance, dramas and thrillers might both show a trend of increased ratings and votes in the later months, potentially corresponding with the end-of-year awards season.

Strategic Release Timing:  

The analysis indicates that movie studios could use these insights for strategic release decisions. For example, action movies showing higher numbers of votes during summer months might also be the ones receiving higher ratings, encouraging studios to release their major action titles during this period to capitalize on increased viewership.  

To have a more complete analysis and validation, Causal Analysis is done later  

### 3.2. Timing and Ratings – Searching for a Pattern

Now, Plot a histogram of Ratings and check the mean, median, and mode  

![Histogram_Rating](./assets/img/Histogram_Rating.png)

Movie Box Office Revenue:  
The mean revenue is approximately 49.92 million, but there's a large standard deviation ($110.47 million), indicating a wide range in revenues.  

Release Month and Year:  

Movies are distributed across all months, with the Release Month ranging from 1 to 12.  

Votes Number:

The average number of votes is 22,530, but this varies widely (standard deviation of 96,625).

Rating:
The average rating is 6.31 out of 10, with a standard deviation of 1.13. 
   

## Causal Analysis  
The dataset contains several columns that are relevant to our causal analysis. Here's a brief overview of the columns:  

Movie name: Another column for the movie title  

Moviebox office revenue: Box office revenue for the movie  

Movie runtime: Runtime of the movie  

Movie languages: Languages in which the movie was released  

Movie countries: Countries where the movie was released  

Movie genres: Genres of the movie  

Release Year: Year of release  

Release Month: Month of release  

Release Day: Day of release  

votes_number: Number of votes received  

RATING: Rating of the movie  

For the causal analysis, the key variables of interest are Release Month, Movie box office revenue, votes_number, and RATING. Other variables like Release Year, Movie genres, Movie runtime, and Movie countries could be important as confounders or control variables.  

We will start by creating a causal graph. This graph will illustrate the assumed causal relationships between the release month and the movie's success/popularity, as well as other relevant variables. We'll then use propensity score matching and sensitivity analysis to draw conclusions.  

Movie Genres, Runtime, and Countries: These could act as important control variables in our analysis. We might impute missing values or use only complete cases, depending on the distribution and nature of these missing values.   

For Causal Analysis we will focus on the number of votes and ratings, which have complete data.  

A causal graph is a visual representation of the assumed causal relationships between variables. In our case, it will depict how the release month might influence a movie's number of votes and ratings, while also showing the potential influence of other variables like genre, runtime, and release year.  

We'll create a basic causal graph based on common assumptions in film analytics:  

The release month (Release Month) may directly affect the number of votes (votes_number) and ratings (RATING).  

The movie's genre (Movie genres), runtime (Movie runtime), and the year of release (Release Year) can also influence its popularity and critical reception.  

The release year might have an indirect effect on the number of votes and ratings through its impact on the evolution of data documentation quality and changes in viewer behavior over time.  

Let's visualize this causal graph  

![Causal_Graph](./assets/img/Causal_Graph.png)

Release Month: Directly impacts both the number of votes (votes_number) and ratings (RATING).  
Movie Genres, Runtime, and Release Year: These variables are assumed to influence both the number of votes and ratings.  

Indirect Effects: The graph also allows for the possibility of indirect effects, such as the impact of the release year on votes and ratings through changes in industry trends, data documentation, and audience behaviors over time.  

With this causal framework in place, the next step is to use propensity score matching. This method will help us estimate the causal effect of the release month on the number of votes and ratings by balancing the distribution of other covariates (like genres, runtime, and release year) across different release months.  

### Propensity Score Estimation: 


Propensity Score Estimation: We'll estimate the propensity scores for each movie, which is the probability of being released in a particular month, given the observed covariates (movie genres, runtime, release year).  
Matching: We'll match movies based on their propensity scores to create comparable groups for each release month.  
Effect Estimation: After matching, we'll estimate the average effect of being released in each month on the number of votes and ratings.  

Since we have multiple release months, we'll treat each month as a separate "treatment" and compare it with the rest. This process will be iterative, comparing one month against all others in turn.  

We'll use logistic regression, treating each month as a binary treatment (e.g., January vs. non-January) in separate models. After that, we'll proceed with the matching and effect estimation.  

Propensity scores for each movie's likelihood of being released in January (and similarly for other months) have been estimated using logistic regression. These scores represent the probability of a movie being released in a specific month, given its genre, runtime, country of release, and release year.

### Matching and Comparisons

The next step is to perform the matching. We will match movies based on these propensity scores to create comparable groups for each release month. There are various matching techniques, but a common approach is to use nearest-neighbor matching. This method pairs each movie in the treatment group (e.g., released in January) with a movie in the control group (not released in January) that has the closest propensity score.  

After matching, we will compare the average number of votes and ratings between matched movies in the treatment and control groups for each month. This will allow us to estimate the average effect of being released in each month on these outcomes.  

The nearest-neighbor matching has been performed for each release month. For instance, for movies released in January (treatment group), we have identified the closest matches from movies not released in January (control group) based on their propensity scores.  

Now, we will estimate the average effect of being released in each month on the number of votes and ratings. We'll calculate the Average Treatment Effect (ATE) for each month by comparing the matched pairs.  

The ATE will be calculated as follows for each month:  

Average number of votes and ratings in the treatment group (released in a specific month)  

Average number of votes and ratings in the matched control group (not released in that month)  

ATE = Average in treatment group - Average in control group  

| Month      | ATE Votes      | ATE Ratings   |
|------------|----------------|---------------|
| January    | -7413.056614   | -0.020796     |
| February   | -4036.678596   | -0.053162     |
| March      | -746.548258    | -0.018964     |
| April      |  971.221314    | -0.011769     |
| May        |  4329.514253   |  0.029846     |
| June       |  4811.658418   | -0.035587     |
| July       |  5038.932812   | -0.038047     |
| August     |  1445.506012   | -0.030679     |
| September  |  1979.354775   |  0.149349     |
| October    | -4794.863486   | -0.027556     |
| November   | -663.190941    |  0.037936     |
| December   |  6810.117530   |  0.051232     |

Key Observations:  

Movies released in May, June, July, September, November, and December generally have a higher number of votes compared to those released in other months, suggesting greater popularity.  

The highest increase in ratings is observed for movies released in September and December.  

Movies released in January, February, March, and October show a decrease in both votes and ratings, indicating lesser popularity and lower critical reception on average.  

This analysis provides insights into how the timing of a movie's release can impact its success and popularity.  

Based on the provided Average Treatment Effect (ATE) data for votes and ratings across various genres (Drama, Comedy, Thriller, Action, Romance Film), let's draw conclusions for each genre:  

#### Drama Genre  

Positive ATE in votes for April, September, November, and December, suggesting these months favor drama movies in terms of popularity.  

Negative ATE in votes for May and June, indicating lesser popularity.  

Ratings show a general increase, particularly in September and December.  

These Observations are consistent with the Observations from Correlation heatmaps  


#### Comedy Genre  

A mixed pattern in ATE for votes, with significant increases in April and December, and decreases in other months like May and July.  

Ratings peak in December but show declines in other months such as April and May.  


#### Thriller Genre
A varied ATE for votes, with significant negatives in January, March, and October, but positives in June, September, and December.  

Ratings are highest in December, with notable declines in February and July.  

These Observations are consistent with the Observations from Correlation heatmaps  


#### Action Genre

ATE for votes shows a negative trend in the early part of the year and a positive trend towards the end, especially in June and September.  

Ratings fluctuate, with the highest increase in December and significant drops in February and July.  

#### Romance Film Genre  

ATE for votes indicates lesser popularity for most of the year, except for a few months like April and May.  
Ratings are generally low with a few exceptions, such as an increase in March and December.  

### General Conclusions:  

Seasonality: Each genre exhibits distinct seasonal patterns in both popularity (votes) and critical reception (ratings).  

Popularity Peaks: Genres like Drama and Comedy seem to fare better in votes towards the latter part of the year.  
Ratings Variability: Ratings fluctuate significantly across months and genres, with some genres like Thriller and Action experiencing their highest ratings towards the end of the year.  

Strategic Release Timing: These insights suggest that strategic timing for movie releases can be crucial and should be tailored according to the genre to maximize success and reception.  


#### Transition :
Small conclusion

_______________________________________________________________

# Conclusion

Summary, and conclusion.
<iframe src="assets/plot/distribution_ethnicity.html" width="750px" height="530px" frameborder="0" position="relative">Genre plot</iframe>

Deuxième : 

<iframe src="assets/plot/plot.html" width="750px" height="530px" frameborder="0" position="relative">Genre plot</iframe>
