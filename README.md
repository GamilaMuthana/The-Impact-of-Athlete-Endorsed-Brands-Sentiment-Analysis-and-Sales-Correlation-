# The Impact of Athlete-Endorsed Brands: Sentiment Analysis and Sales Correlation (1)

# Project

This project aims to analyze the impact of athlete endorsements on brand sentiment and sales, with a focus on Nike and Adidas. It includes a sentiment analysis of news articles, a comparison of sentiment scores against sales data and a case study on Colin Kaepernick’s 2018 Nike ad and its effect on sales. 

The project analyzes the sentiment of news articles mentioning athletes and brand names, correlating the sentiment with brand sales data, and exploring the influence of high-profile endorsements, particularly controversial cases.

# Data Description

## News Article Data

The news articles used were collected through GNews API, filtering for content mentioning specific athlete names. The articles were filtered for those with content mentioning Nike or Adidas using BeautifulSoup. 

The final dataset for news articles contains the athlete mentioned, the article title, the URL, the article content, and the date the article was published. 

`articles/notebooks/sentiment analysis/articles_cleaning.ipynb > articles`

![Screenshot 2024-08-15 at 10.51.43 AM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/248639a3-fb0f-47cb-81b0-628dcd28cb94/Screenshot_2024-08-15_at_10.51.43_AM.png)

## Colin Kaepernick Data

## The tweets used to gauge sentiment around Colin Kaepernick’s controversial Nike ad are stored in a dataset containing tweet dates, tweet contributors, tweet favorite and retweet counts, user follower counts, and other metadata about each tweet.

# Process and Methodology

## Data Collection

### Gather Tweets

The tweets used to gauge sentiment about Nike after Colin Kaepernick’s ad were collected from a Kaggle dataset containing tweets about Nike (containing the #JustDoIt tag) in 2018. 

### Collect News Articles

`articles/notebooks/sentiment analysis/collect_articles.ipynb`

`articles/notebooks/sentiment analysis/scrape_articles.ipynb`

1. A list of athlete names was compiled from [sports-reference.com](http://sports-reference.com), which contains many types of references and data for multiple sports. 
2. The list was passed to the [GNews API](https://gnews.io/), which processed the dataset and fetched articles for each athlete from different news sources across the internet. 
    - This resulted in a dataset containing athlete names, article titles about them, URLs, and article timestamps.
3. The URLs stored in the dataset with article titles were used to scrape the content of each article, filtering for those mentioning Nike and Adidas. 
    - The resulting data contained all columns from the GNews dataset, plus the content of each article.

### Find Sales Data

The quarterly sales data used in this project was found on the Nike and Adidas websites.

Financial Publications - adidas Group
In our Download Center, you find all publications related to our quarterly and full year results of the past ten years as well as the links to our analyst
https://www.adidas-group.com/en/investors/financial-reports

NIKE, Inc. - Investor Relations - Investors - News, Events and Reports
All information presented was current at the time of that event. The company assumes no duty to update the information to reflect subsequent events and developments. For additional earnings release materials, please go to
https://investors.nike.com/investors/news-events-and-reports/?toggle=reports

## Data Cleaning and Preprocessing

### Clean News Articles

`articles/notebooks/sentiment analysis/articles_cleaning.ipynb`

1. The content of each article was cleaned prior to preprocessing.  Contents were converted to lowercase for consistency, and HTML tags and special characters were also removed.
2. The article contents were tokenized (split into a list of words in the article), and stopwords were removed. Contents were also lemmatized.
3. Tokens were rejoined into a new column in case this became necessary during analysis. 

# Colin Kaepernick Case Study

In our digital age, where data shapes opinions and influences societal movements, the power to extract meaningful insights from information has never been more crucial. The Colin Kaepernick protest is a prime example—initially sidelined, it grew into a national movement, challenging narratives and revealing truths that traditional media often obscured. As data science advances, it equips us to uncover hidden trends and challenge misinformation, empowering the majority and preventing the manipulation of information by a few.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/03ce84a1-3789-4cca-9f0f-5867b8c2e0e1/image.png)

### Geographical Analysis

We analyzed the geographical distribution of tweets by using the 'tweet_coordinates' column to identify where the tweets are coming from. Heatmap shows the density of tweets from different locations. Most concentrated is San Francisco, the team Kolin Kaepernick was drafted into.

![Screenshot 2024-08-15 at 10.47.30 AM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/3b7163da-2242-4eeb-bf53-f525c9e4d889/Screenshot_2024-08-15_at_10.47.30_AM.png)

VADER uses (a dictionary of words) where each word is assigned a sentiment score between -4 and +4: Positive words (e.g., "happy", "excellent") have positive scores. Negative words (e.g., "sad", "terrible") have negative scores. Neutral words generally have a score of 0.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/acb6a48f-87f9-4af5-aaf0-97cca428ef9e/image.png)

[5,000 #JustDoIt! Tweets Dataset](https://www.kaggle.com/datasets/eliasdabbas/5000-justdoit-tweets-dataset)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/d3fafded-fefe-4955-baf3-64e0dcb71197/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/b3631185-c7d1-4e6a-8765-6132cb83e177/image.png)

- A focused analysis on the impact of Colin Kaepernick’s Nike ad.
- Evaluating public sentiment before and after the ad and its effect on Nike’s sales.

# Sentiment Analysis

The TextBlob library was used to perform sentiment analysis on news articles. This resulted in polarity and subjectivity scores for each row in the articles dataset. 

- **Polarity** measures the positivity or negativity of the text, ranging from -1 (extremely negative) to +1 (extremely positive).
    - Most articles had a polarity score between 0.1 and 0.2, indicating that the overall sentiment of the articles is slightly positive.
- **Subjectivity** measures how subjective or objective the content is, ranging from 0 (completely objective) to 1 (completely subjective).
    - The subjectivity distribution is concentrated around 0.4 to 0.5, indicating that the content of the articles is a mix of objective and subjective language.
    
    ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/eb4cf210-3138-4cc3-b3cf-1ef128ec3308/image.png)
    

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/cf418a96-afe0-43d3-8af3-4776f7e8d837/image.png)

### Polarity and Subjectivity:

The correlation coefficient between polarity and subjectivity is 0.357, which indicates a moderate positive relationship. This suggests that as the sentiment of an article becomes more positive, it tends to be more subjective.

### Publish Timestamp and Source Encoded:

The correlation is 0.261, indicating a moderate positive relationship. This suggests that certain sources might be publishing more frequently or more recently than others.

### General Interpretation:

The correlations in this matrix are weak to moderate, suggesting that there are no strong linear relationships between the variables.
The most notable correlation is between polarity and subjectivity.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/fb3d026f-4ba3-46e3-b273-b2885e7f4471/image.png)

### **Monthly Polarity Trend:**

- **Nike:** The polarity trend for Nike shows significant fluctuations over time. There are periods where the sentiment dips into negative territory, notably in early 2022 and mid-2023. Despite these dips, the overall trend is relatively stable, with some positive peaks, indicating that **while Nike experiences occasional negative sentiment, it generally maintains a positive outlook**.
- **Adidas:** The **polarity for Adidas remains more stable compared to Nike**, with fewer sharp dips into negative sentiment. However, Adidas's trend shows a more gradual and less volatile pattern, suggesting more consistent sentiment around the brand.

### **Monthly Subjectivity Trend:**

- **Nike:** The subjectivity trend for Nike is quite volatile, with significant fluctuations over time. This suggests that the public's opinion about Nike is more emotional or opinion-based at certain periods, with some months showing higher levels of subjectivity, which may be tied to specific events or marketing campaigns.
- **Adidas:** Adidas’s subjectivity trend shows an increasing pattern, especially in early 2023, indicating that discussions around Adidas have become more opinion-based over time. This could be due to new product launches, endorsements, or controversies that sparked more subjective discussions.

### **Comparison:**

- **Polarity:** Both brands show positive sentiment overall, but Nike experiences more volatility in public opinion, with sharper rises and falls. Adidas, on the other hand, maintains a more stable sentiment, although it does not reach as high peaks as Nike.
- **Subjectivity:** Nike’s subjectivity is more erratic, suggesting that the brand elicits strong opinions from the public at various points in time. In contrast, Adidas shows a more steady increase in subjectivity, indicating that the brand’s perception is gradually becoming more opinion-driven.

# Sales Data Analysis

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/e8a4a687-8fe4-4f38-b3a4-3690e7df0c07/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/ff6f77d9-f816-4760-9a2e-b9feb4576f74/image.png)

**Fluctuating gross profit might reveal underlying operational issues, such as unstable production costs or inconsistent sales performance.**

- The most significant dip in gross profit was in 2020-Q2. Both brands experienced this decline as a result of the start of the COVID-19 pandemic.
- In October of 2022, Kayne West posted a series of controversial statements on social media, causing a boycott of his products. On October 25, 2022, Adidas suspended their partnership with him and halted the production and sales of Yeezy products. The company wrote off unsold inventory, which significantly impacted its gross profit and overall financial results.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ba38de16-45fb-4bee-a66f-1b3b44d806e4/aa408dc1-df5b-4b1c-b5eb-1196b0ff4a05/image.png)

### Polarity and Subjectivity:

There is a very strong positive correlation (**0.9336**) between polarity and subjectivity. **As the sentiment of the text becomes more positive , it also tends to become more subjective.** This makes sense because subjective opinions often carry a positive or negative slant.

### Polarity and Sales/Profit Metrics:

Polarity has a low positive correlation with Operating Profit Sum (**0.2446**). This indicates that **a slight increase in positivity might be associated with an increase in sales and profit**, but the relationship is not strong.

### Sales and Profit Metrics:

Units Sold Sum has an extremely strong positive correlation with both Operating Profit Sum (**0.9934**) and Operating Margin Sum (**0.9936**). This indicates that as the number of units sold increases, both operating profit and operating margin also increase almost proportionally.
**Operating Profit Sum and Operating Margin Sum are also very strongly correlated (**0.9837**), which is expected as profit and margin are closely related financial metrics.**
