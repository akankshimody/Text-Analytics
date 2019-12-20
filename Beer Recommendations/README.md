# Text Analytics - Beer Recommendations
This project is part of coursework for the Text Analytics class in UT Austin's MSBA Program

## Goal of the Project
Create the building blocks of a crowdsourced recommendation system. This recommendation system should accept user inputs about desired attributes of a product and come up with 3 recommendations.

## Data Used
We scrape around 6000 reviews of craft beers from [Beeradvocate](https://www.beeradvocate.com/beer/top-rated/) using Beautiful Soup.
The code for the scraper can be found in `Scraper.ipynb`
The scraped data can be found in `reviews.csv`

## Data Preprocessing
We use Pandas [NLTK](https://www.nltk.org/) to perform the following data preprocessing operations:
1. Remove missing values
2. Remove punctuations
3. Convert to lower case
5. Tokenize words in the comments
6. Remove stopwords

## Analysis and Insights
1. Word Frequency Analysis and Attribute Selection<br>
We select three attruibutes on the basis of which the script will recommend beer. We also perform a word frequency analysis of the data collected to make sure that the above attributes are actually mentioned. <br>
Selected attributes:<br>
  a. Crisp - Highly carbonated; effervescent
  b. Hoppy - Herbal, earthy, spicy, or citric aromas and flavors of hops
  c. Robust - Rich and full-bodied
  
2. Similarity analysis with the 3-attribute set and the reviews<br>
We perform a similarity analysis using Spacy and choose 300 reviews that have the highest similarity scores with the defined attribute set.

3. Sentiment analysis on top 300 reviews and Sorting them (high to low) by the sentiment scores<br>
We conduct a sentiment analysis on the reviews chosen in Step 2 using VADER.

4. Recommend 3 beers to the customer based on similarity and sentiment<br>
Using a combined score from Step 2 and Step 3, we get the following recommendations for the defined attribute set:<br>
Emerald Grouper, Flora, Thicket

5. Recommend 3 beers to the customer based on similarity, sentiment and user rating<br>
Using a combined score from Step 2 and Step 3 along with the average user rating, we get the followng recommendations for the defined attribute set:<br>
Chemtrailmix, Kentucky Brunch Brand Stout, It Was All A Dream

## Conclusion
The recommendations change quite a bit between the two methods. One major reason is because we are using the entire dataset of reviews rather than those that are most similar to the attributes we are looking for. We are looking at all reviews for all products, regardless of the review's relevance to the input attributes (we used 'crisp', 'hoppy', and 'robust'). In general for something as subjective as beer preferences, using all of the reviews is not going to recommend anything personal to the user. Taste differs from person to person. That is why recommending the top rated beers without paying attention to similarity and sentiment isn't a good idea - you can see from the results above that the three top rated beers from Step 5 do not all fit well with our input attributes. One of them is actually one of the worst recommendation scores that we have in the dataset with a score of 1.179436. The other two perform closer to the mean recommendation of the set. Ultimately, blindly recommending high-rated beers will not meet the requirements of the user looking for recommendations.
