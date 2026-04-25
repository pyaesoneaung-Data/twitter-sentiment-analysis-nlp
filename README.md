# Twitter Sentiment Analytics Dashboard

## Overview
An end-to-end sentiment analytics workflow built to transform raw Twitter data into a reporting-ready Power BI dashboard. The project combines Python-based text preprocessing, feature engineering, sentiment scoring, and aggregated exports to support interactive exploration of sentiment behavior over time.

## Objectives
- Prepare noisy tweet data for downstream sentiment analysis and dashboard modeling.
- Engineer text and time-based features that support descriptive analytics.
- Classify tweets into Positive, Neutral, and Negative sentiment groups.
- Produce clean fact and summary tables optimized for Power BI.
- Visualize sentiment patterns, polarity behavior, and tweet activity across dates and hours.

## Dataset
- Source: Twitter dataset from 2009
- Fields used: tweet text, timestamps, sentiment labels, tweet identifiers, and user metadata
- Raw file: `Twitter(X)-Raw_Data-2009.csv`
- Working approach: a balanced sample was prepared from the raw data for analysis and dashboard modeling

The processed analytical layer covers 200,000 tweets across the period from `2009-04-06` to `2009-05-30`.

## Methodology
- Standardized tweet text through lowercase normalization and regex-based noise removal.
- Parsed timestamp strings into structured date and hour dimensions for temporal analysis.
- Engineered text metrics including `word_count`, `text_len`, and boolean indicators for URLs, mentions, and hashtags.
- Computed polarity scores with TextBlob on cleaned tweet text.
- Converted polarity into a 3-class sentiment label: Positive, Neutral, or Negative.
- Aggregated tweet-level data into daily and hourly summary tables for dashboard consumption.

## Data Pipeline
1. Load the 2009 Twitter dataset in Jupyter Notebook using Pandas.
2. Clean and normalize text by removing noise and preserving analysis-ready tokens.
3. Extract temporal fields from tweet timestamps.
4. Generate tweet-level features such as polarity, word count, and text length.
5. Assign 3-class sentiment labels from polarity values.
6. Build export tables for detailed and summarized reporting.
7. Load the CSV outputs into Power BI for modeling, DAX measures, and visualization.

Exported outputs:

- `powerbi_out_3class/daily_summary_3class.csv`
- `powerbi_out_3class/hourly_summary_3class.csv`
- `powerbi_out_3class/fact_tweets_3class.csv`
- `powerbi_out_3class/tweet_text_sample.csv`

## Dashboard Insights
- Sentiment distribution is led by Positive tweets at approximately `42.65%`, followed by Neutral at `37.79%`, and Negative at `19.56%`.
- Daily trend views highlight how sentiment volume shifts across the analysis window rather than relying on a single overall score.
- Average polarity by sentiment helps validate separation between the three sentiment classes.
- Hourly tweet volume reveals when engagement is most concentrated across the day.
- Text diagnostics such as average word count and text length provide additional context for message behavior by sentiment group.

## Dashboard Preview

![Dashboard Overview](./dashboard_overview.png)

[View Full Dashboard (PDF)](./TwitterSentimentAnalysisDataVisualization.pdf)

## Project Structure
```text
.
├── powerbi_out_3class/
│   ├── daily_summary_3class.csv
│   ├── fact_tweets_3class.csv
│   ├── hourly_summary_3class.csv
│   └── tweet_text_sample.csv
├── Twitter Sentiment Analysis_Notebook.ipynb
├── Twitter(X)-Raw_Data-2009.csv
├── TwitterSentimentAnalysisDataVisualization.pbix
├── TwitterSentimentAnalysisDataVisualization.pdf
├── requirements.txt
└── README.md
```

## How to Run
1. Create and activate a Python environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open `Twitter Sentiment Analysis_Notebook.ipynb`.
4. Update any dataset path references if needed.
5. Run the notebook cells sequentially to generate cleaned features and exported CSV files in `powerbi_out_3class/`.
6. Open `TwitterSentimentAnalysisDataVisualization.pbix` in Power BI Desktop and refresh the data model if required.

## Future Improvements
- Replace rule-based polarity thresholds with a trained sentiment classification model.
- Expand preprocessing with lemmatization, stopword handling, and domain-specific normalization.
- Introduce topic extraction or keyword clustering for richer textual insights.
- Parameterize the notebook into reusable pipeline scripts for repeatable execution.
- Publish the dashboard through Power BI Service for scheduled refresh and web access.
