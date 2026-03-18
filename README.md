# ChatGPT-Review-Analysis

In this presentation, we will explore these reviews by analyzing sentiment, patterns over time, and common issues,
The key objectives of this problem statement are:
Sentiment Analysis: 
       to Identify positive, negative, and neutral user sentiments
Issue Identification:
       to Detect common problems driving negative reviews
Time-Series Analysis:
       to Track how sentiment evolves over time
	   
First we will review the dataset, it contains 4 fields:
Review ID:
    A unique identifier for every review
Review:
    Comments given by the user
Rating:
    Represents the levels of satisfaction on a scale of 0-5
Review date:
    When the review was posted
	
	
By using this dataset, we need to clean the data, do some analysis and create visuals by using python libraries.

For this we will use some libraries like pandas, seaborn, matplotlib

1) We need to clean the date by using
   df = pd.read_csv('')
   df.info()
   by using this we will get data columns from the csv file
   
   we can use print(df.head(5))
   It will give top 5 rows in the dataset
   
   to change headers to lower case and replce space with _
   we can use .str.lower().str.replace(' ', '_')
   
   for missing values in a pandas DataFrame and counts them per colu
   we can use df.isnull().sum() 
    
   For replacing missing (NaN/None) values in the 'review' column with empty strings
   we can use .fillna('') function
   
   It converts the review_date column to datetime format while handling invalid entries
   we can use pd.to_datetime
   
   It converts the 'ratings' column to a numeric type (float/int) while handling invalid entries
   we can use pd.to_numeric
   
   
2) To Create sentiment polarity scores from review text using TextBlob, then applies it to create a new DataFrame column.
   Declares a function that takes a single text input
   First checks for missing values (pd.isna() catches NaN/None) or empty strings. Returns neutral score 0 to avoid errors
   Converts input to string, then wraps it in TextBlob object.
   Accesses .sentiment.polarity property, which returns a float from -1.0 to 1.0
   Applies the function row-wise to the 'review' column via .apply(), creating a new numeric 'sentiment_polarity' column.

   Declares a function that takes a single text input
   Here we will use if else funtion to get postive, negative and neutral values
   Applies the function row-wise to the 'sentiment_polarity' column via .apply(), creating a new numeric 'sentiment_category' column.
   
   Same we will use this like first function and 
   Applies the function row-wise to the 'review' column via .apply(), creating a new numeric 'sentiment_subjectivity' column.
   
   Later we will create bar graph visualizations by using these data for better undestanding on how data will get showcase.
   
3) To analyze Postitive Reviews 

   to filter the DataFrame to extract only the review texts classified as positive.
   we can use positive_reviews = df[df['sentiment_category'] == 'positive']['review']
   and we will join the postive reviews and use for loop and counter to get the positive phrases
   by using that data will create bar graph visualizations for better undestanding
   
4) To analyze Negative Reviews 

   to filter the DataFrame to extract only the review texts classified as negative.
   we can use negative_reviews = df[df['sentiment_category'] == 'negative']['review']
   and we will use same process as previous to get negative reviews
   
5) To analyze Neutral Reviews 

   to filter the DataFrame to extract only the review texts classified as neutral.
   we can use neutral_reviews = df[df['sentiment_category'] == 'neutral']
   and we will use same process as previous to get neutral reviews
