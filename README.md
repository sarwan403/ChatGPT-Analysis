# ChatGPT-Review Analysis
🎯 Project Overview & Objectives
As conversational AI applications become central to daily productivity, understanding user sentiment and operational friction is critical for continuous product optimization.

This repository presents an end-to-end data science project that analyzes user reviews for the ChatGPT mobile application. By utilizing Natural Language Processing (NLP) and time-series evaluation, this project aims to answer several core questions:

What are the prevailing user sentiments regarding the mobile app interface and performance?

How has user sentiment shifted over time, and do specific updates correspond with shifts in ratings?

What are the most frequent keywords and themes present in both high-rating (positive) and low-rating (negative) reviews?

📊 Dataset Understanding
The analysis relies on a dataset (chatgpt_reviews.csv) containing real-world, transaction-level user feedback:

Review Id: A unique alphanumeric identifier (UUID) assigned to each user submission.

Review: Raw text feedback submitted by the app user.

Ratings: Ordinal numerical feedback scale ranging from 1 (lowest satisfaction) to 5 (highest satisfaction).

Review Date: High-resolution timestamps capturing the exact moment of review publication (YYYY-MM-DD HH:MM:SS).

🛠️ Data Pipeline & Technical Methods
The workflow is completely mapped out and executed within the production notebook ChatGPT_Reviews_Analysis.ipynb. The workflow is divided into four distinct operational phases:

1. Data Cleaning & Standardization
Temporal Alignment: Raw text timestamps in the Review Date column are parsed and cast into native pandas datetime64[ns] objects to ensure seamless chronological operations.

Handling Missingness & Noise: Null entries or blank review strings are handled dynamically, and text blocks are prepared for tokenization.

Categorical Binning: Reviews are stratified by their score metrics into high, mid, and low tiers to streamline subsequent targeted exploratory deep dives.

2. Sentiment Analysis (NLP)
Polarity Scoring: Leverages TextBlob to perform lexicon-based sentiment analysis, computing quantitative polarity scores for each individual text review block.

Sentiment Categorization: Maps continuous numerical scores into clear, discrete operational buckets: Positive, Neutral, and Negative.

3. Exploratory Data Analysis (EDA) & Visual Storytelling
Volume Distribution: Analyzes rating frequencies using Seaborn countplots to isolate patterns in standard rating distributions.

Chronological Trend Lines: Aggregates and resamples the dataset into continuous monthly intervals (dt.to_period('M')) using Matplotlib to track chronological shifts in user perception.

Keyword Frequency Analysis: Implements text parsing and filtering regex patterns combined with collections.Counter to extract top keywords from negative reviews, helping isolate core user pain points (e.g., app bugs, server timeouts, or subscription constraints).

💡 Preliminary Insights & Recommendations
Rating Skew: The baseline distribution indicates strong polar clusters, with a significant concentration of 5-star reviews alongside sharp, transactional drop-offs when technical errors occur.

Temporal Volatility: Resampled monthly trend tracking shows visible spikes in specific sentiment bands, which can be cross-examined against historic OpenAI rollout schedules (e.g., infrastructure updates or model rollouts like GPT-4o).

Friction Identification: Frequency analysis of lower-rated text reveals recurring operational keywords relating to server sync lags, loading bugs, or login validation cycles—providing a clear roadmap for mobile development engineering teams.

💻 Environment Setup & Usage
Prerequisites
Ensure you have Python 3.8+ installed along with the required analytical dependencies:

Bash
pip install pandas textblob matplotlib seaborn
Running the Analysis
Clone the repository down to your local directory:

Bash
git clone https://github.com/YOUR_USERNAME/chatgpt-reviews-analysis.git
cd chatgpt-reviews-analysis
Open your preferred environment (Jupyter Notebook, JupyterLab, or VS Code) and execute the project file:

Bash
jupyter notebook ChatGPT_Reviews_Analysis.ipynb
Step sequentially through the notebook cells to reproduce the data cleaning, feature engineering, and visualization outputs.
