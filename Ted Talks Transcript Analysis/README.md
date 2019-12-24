# Text Analytics - Ted Talks Transcripts Analysis

## Goal of the Project
The goal of this project was to determine how the content structure of a speech can be influential towards the popularity of the speech.

## Data Used
To determine a Ted Talk's popularity, we scraped speech titles of Ted Talks from Youtube (Since Youtube has it's own algorithm of counting number of views, we thought it would be a reliable source to determine a talk's popularity level). 
Following are the steps performed to do the same :
1. We access Ted's Youtube channel and sort videos by popularity. The link to the page can be found [here](https://www.youtube.com/user/TEDtalksDirector/videos?view=0&sort=p&flow=grid)
2. We then use [Octoparse](https://www.octoparse.com/) to extract the Title and number of views of each of the popular talks. [This](https://www.octoparse.com/tutorial-7/scraping-video-info-from-youtube) is a helpful tutorial to do the same. The scraped data can be found in `data/Popular_Videos_Titles`
3. The Title of the video from Youtube is structured as follows: "[Title of speech] | [Speaker Name]". So we split the Title field into Title of Speech and Speaker name respectively.
4. Using the extracted fields from Step 3, we contruct the urls to be scraped from the [Ted Website](https://www.ted.com/talks) as per the structure of the website. The code to perform Step 3 and 4 can be found in `Building URLs from Youtube data.ipynb` and the final urls to be scraped can be found in `data/final urls.csv`.
5. We use Octoparse again to now scrape the urls and extract the transcripts from the Ted Website. A helpful tutorial to do the same can be found [here](https://www.octoparse.com/tutorial-7/extract-data-with-a-list-of-urls). The final data containing transcripts can be found in `data/Transcripts.csv'

## Data Preprocessing


## Analysis and Insights


## Conclusion
