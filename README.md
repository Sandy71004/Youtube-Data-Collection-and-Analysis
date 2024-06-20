# YouTube Data Collection and Analysis

To collect data from YouTube, we need to be clear about what data we need. Let’s collect data about the trending videos on YouTube to analyze and find what makes a video trend on YouTube.

## Setting Up YouTube Data API

To collect data from YouTube, you need to set up an API. Here are the steps you can follow:

1. Go to Google Cloud Console.
2. Click on the project drop-down at the top, then “New Project”.
3. Enter a project name and click “Create”.
4. In the Google Cloud Console, navigate to “APIs & Services” > “Library”.
5. Search for “YouTube Data API v3” and click on it.
6. Click “Enable”.
7. Go to “APIs & Services” > “Credentials”.
8. Click “+ CREATE CREDENTIALS” and select “API key”.
9. Copy the generated API key.

## Step-1: Data Collection

### Code Implementation:

We have collected data about the top 200 trending videos on YouTube.

### Output Observations:

We are using the YouTube Data API to fetch details of the top 200 trending videos in the US, iterating through the API’s paginated responses to collect video details such as title, description, published date, channel information, tags, duration, definition, captions, and various engagement metrics like views, likes, and comments. The script compiles this information into a list, converts it into a pandas DataFrame, and saves the data to a CSV file named `trending_videos.csv`, allowing us to analyze trends and patterns in the collected video data.

## Step-2: Data Description and Data Pre-Processing using Pandas

### Code Implementation:

Used pandas for description of data collected through API i.e., `trending_videos.csv`.

### Output Observations:

Checked for missing values and data types of columns. Found that the description column has 4 missing values. This is minor and can be handled as needed. The data types seem appropriate for most columns, but we may need to convert the `published_at` column to a datetime format and tags might need further processing.

## Step-3: Descriptive Statistics of Data

### Code Implementation:

Parameters: `view_count`, `like_count`, `dislike_count`, `comment_count`

Distribution of views, likes, and comments of all videos in data using matplotlib and Seaborn libraries.

### Output Observations:

The histograms show that the distributions of view counts, like counts, and comment counts are right-skewed, with most videos having lower counts and a few videos having very high counts.

## Step-4: Correlation Matrix

### Code Implementation:

Look at the correlation between likes, views, and comments.

### Output Observations:

The heatmap confirms strong positive correlations between views, likes, and comments. Understanding the correlation between these metrics can provide insights into how engagement on videos is related. For example:
- A high positive correlation between `view_count` and `like_count` suggests that videos with more views also tend to receive more likes.
- A high positive correlation between `view_count` and `comment_count` suggests that videos with more views also tend to receive more comments.

## Step-5: Collecting Category Names

Since we have collected only category ID, let’s collect category names also from the API.

## Step-6: Analyze the Trending Videos by Category

### Code Implementation:

Analyze the number of trending videos on YouTube.

### Output Observations:

The bar chart shows that the Gaming, Entertainment, Sports, and Music categories have the highest number of trending videos.

## Step-7: Average Engagement Metrics by Category

### Code Implementation:

Look at the average engagement metrics by category.

### Output Observations:

Music and People & Blogs categories have the highest average view counts, likes, and comments. Film & Animation also shows high engagement, especially in view counts and like counts.

## Step-8: Convert Duration from ISO 8601 Format to Seconds

Using the `isodate` library to convert the duration of each video from the ISO 8601 format to seconds, which allows for numerical analysis. After converting the durations, categorizing the videos into different duration ranges (0-5 minutes, 5-10 minutes, 10-20 minutes, 20-60 minutes, and 60-120 minutes) by creating a new column called `duration_range`. This categorization enables us to analyze and compare the engagement metrics of videos within specific length intervals, providing insights into how video length influences viewer behavior and video performance.

## Step-9: Analyze the Content and Duration of Videos

### Code Implementation:

Analyze the content and duration of the videos.

### Output Observations:

The scatter plot shows a slight negative correlation between video length and view count, indicating shorter videos tend to have higher view counts. Videos in the 0-5 minute range have the highest average view counts, likes, and comments. Engagement decreases as video length increases.

## Step-10: Analyze the Relationship between Views and Number of Tags

### Code Implementation:

Analyze the relationship between views and number of tags.

### Output Observations:

The scatter plot shows a very weak relationship between the number of tags and view count, suggesting that the number of tags has minimal impact on a video’s view count.

## Impact of Time a Video is Posted on its Views

The distribution shows that most videos are published between 14:00 and 20:00 hours (2 PM – 8 PM), indicating this may be an optimal time for uploading videos. There is a very weak negative relationship between publish hour and view count, suggesting that the hour of publication has minimal impact on engagement metrics.

## Conclusion

So, here’s my conclusion on what makes a video trend on YouTube:
1. Encourage viewers to like and comment on videos to boost engagement metrics.
2. Aim to create shorter videos (under 5 minutes) for higher engagement, especially for categories like Music and Entertainment.
3. Schedule video uploads around peak times (2 PM – 8 PM) to maximize initial views and engagement.
