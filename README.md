# MICROSOFT MOVIE STUDIO FILMS ANALYSIS.
![Microsoft](https://github.com/ngeny-brian/phase1-project/assets/133016482/d6a3d9be-38ee-4375-aa0a-54063b8834be)

**Author: Brian Kipruto Ngeny.**

## Introduction.
Microsoft software company is creating a movie studio and thus, they want an analysis of the films that are currently doing the best on box office so as to gain insight into the types of films that are currently marktable. Since this is a new studio, we are going to acquire and analyze data from established movie studios and movie rating sites so as to gain knowledge and insight into the current scene of the movie industry. The results of this project could provide valuable information on the movie genres that are most popular right now and the ones that have stood the test of time. Thus, providing Microsoft movie studio with a good basis on where to begin with in film production

## Overview.
This project analyzes the types of films currently doing the best on Box Office to find actionable insights that the head of Microsoft's new movie studio can use to help decide what type of films to create. Eploratory Data Analysis and Evaluation shows that some of the highest rated genres are; Adventure, Drama, Sci-Fi, Comedy, Action and Romance which are also among the most profitable genres, indicating that they are the best perfoming film types currently.

## Business Problem
Microsoft sees all the big companies creating original video content and they want to get in on the fun. They have decided to create a new movie studio, but they don’t know anything about creating movies. Like any new business venture, market analysis is an important step in the establishment of the business. It provides crucial information on market trends, peak seasons and recommendable product or services that can give a business a niche over the competition. To address this issue, I plan to use exploratory data analysis(EDA) to provide the head of Microsoft movie studio with actionable recommendations and insights into the type of films the studio should focus on producing so as to take the movie industry by storm and avoid making too many loses that may lead to the shutting down of the movie studio.

 ## Objectives.
The goal of this project is to;<br>
    1. Analyze the findings of the exploratory data analysis model(EDA) and provide the company with actionable insights that answer the following specific business questions;<br>
    
        i) What is the mean, minimum, maximum and position of outlier amounts for movie gross return values?
        ii)  Does the popularity and original language of a movie affect its rating?
        iii) How does the production budget amount transalte to the gross returns?
        iv) Do higher movie ratings translate to higher gross returns?
        v) Which are the highest rated and most profitable genres of movies currently?

## Notebook structure.
This project's notebook follows the following structure:
1. Business problem.
2. Data understanding.
3. Data preparation.
4. Data Analysis and Evaluation.
5. Conclusions and Recommendations

## The Data
The data used and located in the folder `zippedData` was sourced from:
* [Box Office Mojo](https://www.boxofficemojo.com/)
* [IMDB](https://www.imdb.com/)
* [Rotten Tomatoes](https://www.rottentomatoes.com/)
* [TheMovieDB](https://www.themoviedb.org/)
* [The Numbers](https://www.the-numbers.com/)

Because it was collected from various locations, the different files have different formats. Some are compressed CSV (comma-separated values) or TSV (tab-separated values) files that can be opened using spreadsheet software or `pd.read_csv`, while the data from IMDB is located in a SQLite database.
After visiually inspectiong the sample data from each of the datasets previewed, it is evident that that the only useful datasets are;

> - bom_data sourced from Box office mojo.
This data represents a total of 3387 entries of individual movies with the variables being the title, studio, domestic_gross, foreign_gross and the year of its release. The target variables for this dataset are the title, domestic_gross and foreign_gross. This variables are essential in determining the gross returns for each film domestically, internationally and the total gross returns, the other columns will be dropped in the next step of the project.

> - tmdb_data sourced from The MovieDB.
This data represents a total of 26517 entries of individual films with the variables being the genre_ids, id, original_language, original_title, popularity, release_date, title, vote_average and vote_count. The target variables are, the id, original_language, popularity, title and vote_average. These variables will help me determine how the orginal language of movie relates to the popularity of the movie and also how the popularity affects the rating of the movie using the vote_average as the rating index.

> - tn_movie_budgets data sourced from The Numbers.
This data represents a total of 5782 entries of individual movies with the variables being the id, release_date, movie, production_budget, domestic_gross and worldwide_gross. The target variables for this data are the id, movie, production_budget, domestic_gross and worldwide_gross. These variables will be usefull in determining the relationship between the amount of money allocated for the production budget and the subsequent gross returns both domestically and worldwide.

> - movie_ratings table sourced from IMDB database.
This data represents a total of 73856 entries of individual movies with the variables being movie_id, averagerating and numvotes. The target variables are the movie_id and averagerating which combined with the data from the next table i.e movie_basics, will be used to determine which genres of movies have the highest ratings.

> - movie_basics table sourced from IMDB database.
This data represents a total of 146144 entries of movies with the variables being the movie_id, primary_title, original_title, start_year, runtime_minutes and genre. The target variables for this dataset are the movie_id, original_title and genre. This table is going to be joined to the movie_ratings table and used to determine which genres of movies have the highest ratings on IMDB.

> - imdb_data table.
This dataset is created by merging the two tables from the IMDB database into one table using the movie_id as the unique identifier. The columns generated by this merging process are used in determining the genres of movies and their respective ratings.

> - merged_data table.
This dataset is created by merging the imdb_data table with the bom_data table into one table using the title as the unique identifier. The columns generated by this merging process are used in determining the genres of movies with the highest gross returns.

## Methodology.
This project uses exploratory data analysis, including statistical data value analysis to explore the data provided and determine the trends and corelations between several features of movies which are otherwise hidden.

## Results.
1. The statistical values for the data provided on the production budgets, domestic gross and worldwide gross are as follows:
> a). The average amount for the production budget of a movie is 31,587,757 dollars. The lowest amount on record is 1,100 dollars and the highest amount on record is 425,000,000 dollars.
> 
> b). The average amount for the domestic gross of a movie is 41,873,326 dollars. The lowest amount on record is 0 dollars and the highest amount on record is 936,662,225 dollars.
> 
> c). The average amount for the worldwide gross of a movie is 91,487,460 dollars. The lowest amount on record is 0 dollars and the highest amount on record is 2,776,345,279 dollars.

2. There is no corelation between popularity and rating as evidenced by the scatter plot displayed below:
![scatterplot](https://github.com/ngeny-brian/phase1-project/assets/133016482/faf97869-6a14-4b63-ace2-6e461fd6e855)

3. There is however a close relationship between the rating of a movie and the gross revenue it generates as shown below:
![linegraph](https://github.com/ngeny-brian/phase1-project/assets/133016482/d9ead41c-58ac-41da-a033-fd475590d133)


4. The top most profitable genres are; Adventure, Drama, Sci-Fi, Comedy and Action movies as evidenced below:
![stripplot](https://github.com/ngeny-brian/phase1-project/assets/133016482/5a5df1cf-11de-4b71-8912-80b50e705bd7)


## Conclusions.
Based on the analysis done, this are the conclussions that can be drawn up:

> I) A movie with an average production budget of close to 30,000,000 dollars is expected to return an aproximate total gross amount of 100,000,000 dollars. The good news is that, the box plot shows that most of the outlier values are found above this aproximate value, meaning that a movie is more likely to surpass its aproximated gross return value.

> II) The original language of a movie also has a bearing on the rating and popularity of a movie. English movies are by far the most produced movies in the dataset analyzed but are very lowly rated and not as popular compared to Japanese, French and Spanish movies which are the highest rated and most popular movies in terms of the original languages.

> III) Among the top ten most produced genres of movies, Drama, Comedy and Romance are the most recurrent genres. These three genres also appear more times than any other genre in the top five highest rated list of most produced genre of movies.

> IV) After merging the dataset on ratings and the dataset on gross returns, I concluded that some of the genres that fetch the highest amount of gross returns are, Adventure, Drama, Sci-Fi, Comedy, Action, Fantasy and Sport.

## Recommendations.
The Exploratory Data Analysis and conclusions drawn from the analysis lead to these recommendations for the Microsoft movie studio:

> - __The production budget allocated to an individual movie, should on average be between 25,000,000 dollars and 35,000,000 dollars.__ This will help in mitigating the risk factor involved in any business venture such as this one. If the movie is a success, it will raise upwards of 100,000,000 dollars gross revenue but if it fails it should break-even and generate aproximately the same amount as the production budget.

> - __The Studio should focus on producing content with highly rated features e.g. highly rated original languages and highly rated genres.__ From the analysis done, there is a close corelation between the rating of a movie and the gross revenue it generates. Combining highly rated features in movie production should result in a good, quality movie that is bound to be highly rated and thereafter high revenue returns.

> - __The studio should prioritise these genres; Adventure, Drama, Sci-Fi, Comedy, Action and Romance.__ These genres have been determined from the analysis as the highest rated genres and the most profitable ones. Creating content found within these genres and even combinations of these genre types is an assured tactic of making the studio a success.


