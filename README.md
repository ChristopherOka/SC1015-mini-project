# SC1015-mini-project

## Practical Motivation
Movies are quite popular in our society's culture, and being able to predict the success of a movie is imperative to movie studios, directors, and all other cast and crew.
We decided to analyse whether the title of movies has an impact on a movie's success, with the goal of finding some hidden predictor within the title.

The variables we decided to analyse within the title are as follows:
- Title sentiment (how positive or negative the words in the title are)
- Title Length (word cound)
- Average Title Word Length
- Has Made-Up Word (whether a word in the title isn't in the English dictionary)
- Made-Up Word Count

## Data Collection & Cleaning
We used the movies database also known as TMDB found at [themoviedb.org](https://themoviedb.org)

Using the API, we scraped the data of the 10,000 most popular movies from the database.

We then put this data into a DataFrame and saved it as a CSV file.

To clean the data, we removed any unnecessary columns from the csv.

We then removed any outliers of _Popularity_ and _Vote Average_, using the IQR method.

After removing outliers, we removed any non-native Enlish movies from the dataset, as poor translations could alter the results.

Finally, we removed any movies with a _Vote Count_ less than 10, as few votes could massively skew the _Vote Average_.

## Exploratory Analysis
To create our variables of interest, we used the following methods:
- For Title Sentiment, we used the Natural Language Toolkit (NLTK) to analyse the sentiment of each word in the title, which gave us a total score for the entire title.
- For Title Length, we simply counted the number of words in the title.
- For Average Title Word Length, we calculated the average length of each word in the title.
- For Has Made-Up Word, we used found a JSON file with a list of 479k English words, and checked if each word in the title was in the list.
- For Made-Up Word Count, we counted the number of words in the title that weren't in the list of English words.

This gave us a dataset the response variables of _Popularity_ and _Vote Average_, and the predictor variables of _Title Sentiment_, _Title Length_, _Average Title Word Length_, _Has Made-Up Word_, and _Made-Up Word Count_.

## Machine Learning
We used several methods to predict the response variables, to hopefully find a correlation between the title and the success of the movie.

Since we had 5 of our predictor variables as numerical (_Title Sentiment_, _Title Length_, _Average Title Word Length_, _Made-Up Word Count_), and 1 of our predictor variables as categorical (_Has Made-Up Word_), we decided to use Linear Regression and Random Forest Regression on the numerical variables and a Classification Tree and Random Forest Classification on the categorical variable.

When applying the regression models on the predictor variables, we found quite poor results on the test data, with most R^2 values close to 0. This was disheartening, but we kept testing and continued on with our classification tree and random forest classification models.

With the classification tree, we did find a significant correlation in the data, with the test accuracy being 89% when using the _Vote Average_ and 97% when using the _Popularity_.

When applying the random forest classification model, we found worse results, with the test accuracy being 79% when using the _Vote Average_ and 74% when using the _Popularity_.

## Statistical Inference
Overall, the decision tree was the most accurate model, which helped us infer that the title of a movie does have an impact on the success of a movie. 

We found that whether a movie has a made-up word or not can predict with high-accuracy whether the movie will be popular or not and whether it will have a high vote average or not.




