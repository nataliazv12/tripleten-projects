# Study of Factors Behind Video Game Sales Success

**Business question:** Which factors determine whether a video game sells well, based on historical worldwide sales data through 2016 for the online store "Streamchik"? The goal is to spot the patterns that predict success so that future marketing and inventory decisions can focus on promising platforms, genres, and regions.

**Context:** Global sales data for computer games, with regional breakdowns (North America, Europe, Japan, other), critic and user review scores, ESRB age ratings, platform, genre, and release year. Game platforms are regularly replaced by newer models roughly every 5 years, so sales patterns shift as consoles rise and fall in popularity, the analysis needs to account for that lifecycle.

## Tools

`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scipy`

## Approach

1. Data cleaning: dropped missing values in `name`, `genre`, and `year_of_release` (each under 5% of rows, with no reasonable replacement); placeholder values for missing critic/user scores; resolved the `tbd` ("to be determined") anomaly in user scores before converting the column to float; removed one implicit duplicate record
2. Feature engineering: `total_sales` as the sum of regional sales columns
3. Release trends: games released per year (peak 2008-2009, followed by a steady decline) and platform lifecycle analysis (PS2, X360, PS3) showing sales rise, peak, and fall as each console ages and is succeeded by a new model
4. Restricted the "current" analysis window to 2014-2016 for relevance to forecasting, since platforms cycle roughly every 5 years
5. Platform comparison via box plot of total sales (2014-2016), and the relationship between critic/user review scores and sales (scatter plots + Pearson correlation), tested on PS4 and on the other platforms combined
6. Genre comparison via box plot of total sales by genre (2014-2016)
7. Regional user profiles: top-5 platforms and top-5 genres by total sales in North America, Europe, and Japan, plus the effect of ESRB rating on Japanese sales
8. Hypothesis testing (Welch's t-test): (a) average user ratings of Xbox One vs. PC, (b) average user ratings of the Action vs. Sports genres

## Key Findings

- Game releases peaked in 2008-2009 and have declined since; sales data for any one platform is only relevant for a few years around its release, since a new console typically supersedes the previous one within about 5 years
- Of the 2014-2016 window, PS4 and Xbox One are the only platforms whose sales grew from 2014 to 2015; every other platform declined
- Critic review scores show a weak positive correlation with sales on PS4 (≈0.40) and a smaller positive correlation on other platforms (≈0.22); user review scores show essentially no correlation with sales anywhere (≈−0.04 on PS4, ≈−0.01 elsewhere), critic opinion matters more than user opinion for commercial success
- Shooter is both the highest-total and highest-median-selling genre (consistently profitable); Puzzle is the least profitable; Action has many low-selling outliers alongside its hits
- Regional tastes diverge: North America and Europe both favor PS4/Xbox One and Action/Shooter genres, while Japan favors the 3DS and Role-Playing/Action genres, Japan's market behaves distinctly from the Western markets
- ESRB age rating is associated with meaningfully different sales levels in Japan
- User ratings for Xbox One and PC are statistically indistinguishable (failed to reject H0), while user ratings for the Action and Sports genres are statistically different (rejected H0)

## Deliverables

- `Video Game Sales Success Factors.ipynb` — full analysis notebook (data cleaning, feature engineering, exploratory analysis, platform/genre/region comparisons, hypothesis testing, conclusions)

*Note: a few chart axis labels in the notebook's saved plot images remain in the original language, since the source dataset was not available to re-run the notebook end-to-end when preparing this English version. All code, comments, and written analysis are in English.*
