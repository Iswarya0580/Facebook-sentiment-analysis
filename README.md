# Facebook-sentiment-analysis
### Name:Iswarya P
### Reg.no:212223230082

## AIM

To perform sentiment analysis on Facebook data using Python and filter only the neutral feedback comments from the dataset.

## PROBLEM STATEMENT

Social media platforms like Facebook contain a large amount of user-generated content such as comments, posts, and feedback. Analyzing these comments manually is difficult and time-consuming. The objective of this project is to classify Facebook comments into Positive, Negative, and Neutral sentiments using Natural Language Processing (NLP) techniques and extract only the neutral feedback comments for further analysis.

## FEATURES USED
Python Programming
Pandas Library
TextBlob Library
Sentiment Analysis
CSV File Handling
Data Filtering

## STEPS

### Step 1:

Install required Python libraries such as pandas, textblob, and nltk.

### Step 2:

Upload the Facebook comments dataset in CSV format.

### Step 3:

Read the dataset using pandas.

### Step 4:

Apply sentiment analysis using TextBlob.

### Step 5:

Classify comments into:

Positive
Negative
Neutral

### Step 6:

Filter only the neutral feedback comments.

### Step 7:

Store the neutral comments in a new CSV file.

## PROGRAM

###  Install required libraries
!pip install textblob pandas nltk

### Import libraries
import pandas as pd
from textblob import TextBlob

### Upload CSV file
from google.colab import files
uploaded = files.upload()

### Read dataset
df = pd.read_csv("facebook_comments.csv")

### Display columns
print(df.columns)

### Sentiment analysis function
def get_sentiment(text):
    analysis = TextBlob(str(text))
    polarity = analysis.sentiment.polarity

    if polarity > 0:
        return "Positive"
    elif polarity < 0:
        return "Negative"
    else:
        return "Neutral"

### Apply sentiment analysis
# Replace 'comment' with your dataset column name if needed
df["Sentiment"] = df["comment"].apply(get_sentiment)

### Filter neutral comments
neutral_df = df[df["Sentiment"] == "Neutral"]

### Save result
neutral_df.to_csv("neutral_feedback.csv", index=False)

print("Neutral feedback extracted successfully!")

### Display neutral comments
print(neutral_df)

## Download output file
files.download("neutral_feedback.csv")

## SAMPLE OUTPUT
```
Columns in dataset:
Index(['comment'], dtype='object')

Neutral feedback extracted successfully!

                     comment Sentiment
0             It is okay      Neutral
1          Average service    Neutral
2      Product is normal     Neutral
```
## RESULT

Thus, sentiment analysis was successfully performed on Facebook data using Python, and the comments containing neutral feedback were filtered and stored in a separate CSV file successfully.
