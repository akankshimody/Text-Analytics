# Text Analytics - Ted Talks Transcripts Analysis

## Goal of the Project
The goal of this project was to determine how the content structure of a speech can be influential towards the popularity of the speech.

## Data Used
We use transcripts of ~190 popular Ted Talks. To determine a Ted Talk's popularity, we scraped speech titles of Ted Talks from Youtube (Since Youtube has it's own algorithm of counting number of views, we thought it would be a reliable source to determine a talk's popularity level). 
Following are the steps performed to collect our data:
1. We access Ted's Youtube channel and sort videos by popularity. The link to the page can be found [here](https://www.youtube.com/user/TEDtalksDirector/videos?view=0&sort=p&flow=grid)
2. We then use [Octoparse](https://www.octoparse.com/) to extract the Title and number of views of each of the popular talks. [This](https://www.octoparse.com/tutorial-7/scraping-video-info-from-youtube) is a helpful tutorial to do the same. The scraped data can be found in `data/Popular_Videos_Titles`
3. The Title of the video from Youtube is structured as follows: "[Title of speech] | [Speaker Name]". So we split the Title field into Title of Speech and Speaker name respectively.
4. Using the extracted fields from Step 3, we contruct the urls to be scraped from the [Ted Website](https://www.ted.com/talks) as per the structure of the website. The code to perform Step 3 and 4 can be found in `Building URLs from Youtube data.ipynb` and the final urls to be scraped can be found in `data/final urls.csv`.
5. We use Octoparse again to now scrape the urls and extract the transcripts from the Ted Website. A helpful tutorial to do the same can be found [here](https://www.octoparse.com/tutorial-7/extract-data-with-a-list-of-urls). The data containing transcripts can be found in `data/Transcripts.csv`
6. This data is then cleaned to remove punctuations and digits. The code for the same can be found in `Data Cleaning.ipynb`. The final data we used can be found in `data/cleaned_data.csv`

## Analysis and Insights
We performed Sentiment Analysis on the cleaned data. The code for the same can be found in `Sentiment Analysis Part 1.ipynb` and `Sentiment Analysis Part 2.Rmd`. 

Some key insights we found were:
1. 84% of the Ted Talks had an overall positive sentiment while only 16% of the talks had an overall negative sentiment.<br>
<img src=" alt="Image1" width="500"/><br><br>
Some examples of the negative talks are :
  a. Sleep is your superpower - Matt Walker
  b. How to stay calm when you know you'll be stressed - Daniel Levitin
  c. The price of shame - Monica Lewinsky
  d. My escape from North Korea - Hyeonseo Lee
2. As we progress in the talk, laughter gradually decreases.<br>
<img src="" alt="Image2" width="500"/><br><br>
3. The timing of seriousness/ negative sentiment in more popular talks differs from that of less popular talks.<br>
<img src="" alt="Image3" width="500"/><br><br>
