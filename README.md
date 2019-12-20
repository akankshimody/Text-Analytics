# Text Analytics - Insights from Edmunds.com
This project is part of coursework for the Text Analytics class in UT Austin's MSBA Program

## Goal of the Project
Edmunds.com is an online forum for automative information. We extract information on Entry Level Luxury cars from a forum on Edmunds.com to identify which brands are mentioned together and what are the most common attributes associated with the top 5 brands.

## Data Used
We scrape 4000 to 5000 comments on Entry Level Luxury cars from https://forums.edmunds.com/discussion/2864/general/x/entry-level-luxury-performance-sedans/ using Selenium. The code for the scraper can be found in `scraper.ipynb`
The scraped data can be found in `comments.csv`

A detailed tutorial on the same can be found [here](https://towardsdatascience.com/web-scraping-using-selenium-python-8a60f4cf40ab)

## Data Preprocessing
We use Pandas [NLTK](https://www.nltk.org/) to perform the following data preprocessing operations:
1. Remove missing values
2. Remove punctuations
3. Convert to lower case
4. Replace model names with brand names. The mapping file can be found in `models.csv`
5. Tokenize words in the comments
6. Remove stopwords

## Analysis and Insights
1. MDS Map of top 10 brands (based on word frequency) using lift scores <br><br>
![MDS Map](https://github.com/akankshimody/Text-Analytics---Insights-from-Edmunds.com/blob/master/MDS%20Map.PNG)<br><br>
Mercedes and Volvo have the strongest association. This is an interesting relation because Mercedes is undisputably a luxury car brand, but Volvo is not. The data is from entry-level-luxury-performance-sedans forum, and it is easy to guess luxury brand such as Mercedes, Audi, and BMW will have a significant lift with each other. However, people tend to talk more about a luxury car brand with a rather normal brand. This can be interpreted as people thinking about either buying a car with luxury brand or buying a car with reasonable price. Thus, luxury car brand managers should not only consider other luxury brands but also qualified brands with reasonable price as competitors.

2. Identify most frequently mentioned attributes for the top 5 brands (based on word frequency)<br><br>
(i) Performance is the most frequently mentioned attribute for all brands based on word frequency, so it is recommended that all product managers pay close attention to the design of engines and raise their performance. If we take the lift scores into consideration, BMW and infiniti are the most strongly associated with price. Assuming a positive sentiment, we suggest product managers continue working on reducing the costs while maintaining the high performance of cars. Acura is most strongly associated with looks, so designing stylish and good-looking luxury cars for the brand is recommended. Audi is most strongly associated with interiors, while Honda is most strongly associated with experience. Product managers should focus a greater proportion of their efforts on these specific attributes. Below is the lift matrix of brand with respect to top mentioned attributes<br><br>
(ii) Recommended marketing focuses:<br><br>
BMW and Infiniti - good value for money<br>
Acura - stylish luxury cars<br>
Audi - luxurious interior design<br>
Honda - best driving experience<br>

Brand | performance | price |	experience | look | interior
------------ | ------------- | ------------ | ------------ | ------------ | ------------
bmw	| 1.16783	| 1.3542 | 1.19542	| 1.18655	| 1.22402
acura	| 1.08869	| 1.13571	| 1.18579 | 1.50397 | 1.2296
audi	| 1.13299	| 1.17046	| 1.38727	| 1.31134	| 1.58645
infiniti	| 1.13543	| 1.41912	| 1.26205	| 1.27807	| 1.2824
honda	| 0.649578	| 0.637511	| 0.770712	| 0.770418	| 0.538015 

3. Identify the most 'aspirational' brand<br><br>
To assess which brands were the most 'aspirational', we decided to create a list of aspirational words (dream, beaity, desire, etc.) and replace those words with the word 'aspirational', similarly to what we did with the brands and models. From there, we did a count of how many times the brand appears in post, and then how many times the word 'aspirational' appears with that brand. From there, we calculated lifts, which can be found in the table above. The brand with the highest lift ended up being Chrysler, which we thought was interesting. We think that Chrysler could capitalize on this from a marketing perspective- Chrysler, though it is not associated with typical luxury brands like Mercedes or BMW, has a higher representation of people that aspire to own a Chrysler. Chrysler can create marketing campaigns that capitalize on this, and thus generate even further interest in the brand.

