# spotify-dataset-analysis

## Overview
This repository contains exploratory and inferential statistics over 1M Spotify tracks (2000-2023), downloaded from https://www.kaggle.com/datasets/amitanshjoshi/spotify-1million-tracks/data.
The Jupyter notebook `analysis.ipynb` inspects metadata such as popularity, genre, tempo, loudness, and energy to understand how audio features and categorical attributes relate to track success.

Key goals:
- describe distributions of numeric features and highlight notable patterns
- test independence between genre and popularity using a chi-square test with fine-grained popularity bins
- compare popularity across musical mode, measure monotonic trends over time, and relate energy to danceability

## Repository Structure
- `analysis.ipynb` - main analysis notebook with code, visuals, and statistical tests
- `spotify_data.csv` - raw dataset exported from Spotify (over 1.1M rows, 20 columns)
- `README.md` - project documentation (this file)

## Dataset
The dataset provides one row per track with the following groups of variables:
- identifiers and metadata: `artist_name`, `track_name`, `track_id`, `year`, `genre`
- popularity score: integer 0-100 (higher means more streams / playlist presence)
- audio features: `danceability`, `energy`, `valence`, `tempo`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`
- tonal info: `key`, `mode`, `time_signature`
- duration: `duration_ms`

No missing values are present in the delivered CSV. Tracks are not deduplicated by artist, so multiple entries per artist exist.

## Environment Setup
1. Create a Python environment (Python 3.9+ recommended).
2. Install the required packages:

~~~bash
pip install pandas numpy scipy matplotlib
~~~

   Optional: install seaborn if you want the styling used in some exploratory plots.
3. Launch Jupyter Lab/Notebook and open `analysis.ipynb`.

## Notebook Guide
The notebook is organised into the following sections:
1. **Import & data loading** - read the CSV, set display options, inspect schema and head.
2. **Missing values** - confirm there are no NaNs and compute per-column counts.
3. **Descriptive statistics** - histograms for core metrics, commentary on skewness and central tendency.
4. **Comparisons by category** - boxplots/aggregations for mode and time signature, yearly popularity trends, scatter plots for feature pairs.
5. **Correlation matrix** - Pearson correlations across numeric features.
6. **Hypothesis testing** - chi-square independence for genre vs popularity quantiles, independent-sample t-tests, and Spearman correlations.

The notebook blends code cells and markdown commentary so you can follow the reasoning behind each figure or test.

## Future Work
- Model popularity using regression or tree-based approaches with cross-validation.
- Explore time-aware analysis (rolling windows by year, release cohorts).
- Extend the chi-square framework to artists after stronger aggregation rules or to playlists/regions if data becomes available.

Feel free to open issues or propose improvements via pull requests.
