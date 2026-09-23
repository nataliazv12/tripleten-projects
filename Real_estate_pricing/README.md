# Apartment Listings Price Analysis — Real Estate Market Research

**Business question:** What factors determine an apartment's sale price, and how quickly do listings sell, based on Yandex Real Estate listing data for St. Petersburg and surrounding areas?

**Context:** Archive of apartment sale listings covering several years, with both user-entered attributes (price, area, room count, etc.) and map-derived attributes (distance to center, airport, parks, ponds). Goal: identify the parameters that drive market value, as a foundation for detecting pricing anomalies and fraudulent listings.

## Tools

`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn`

## Approach

1. Data cleaning: handling missing values across ceiling height, balcony count, floor count, kitchen/living area, locality name, and listing duration, using segment-specific means, structural relationships (e.g. studio apartments have no separate kitchen), and quantile-based outlier removal
2. Deduplication of locality names (implicit duplicates from inconsistent settlement-type labeling)
3. Feature engineering: price per sq m, day/month/year of listing publication, floor category (first/last/other), distance to city center in km
4. Exploratory analysis of each parameter's distribution (total/living/kitchen area, price, room count, ceiling height, floor, distance to center/airport/park, publication timing)
5. Price-driver analysis: area, room count, floor category, and publication timing (day of week, month, year)
6. Price-per-sq-m comparison across the 10 localities with the most listings
7. Price-vs-distance-to-center analysis specifically within St. Petersburg, including investigation of anomalous price dips at 3 km and 27 km

## Key Findings

- Price rises directly with total area, living area, and kitchen area, and with the number of rooms
- First-floor and top-floor apartments are priced noticeably lower than mid-building ("other") floors
- Listings published Monday–Wednesday sell at a premium versus those published Friday–Sunday
- Listings published March–April and November–December carry higher prices than the rest of the year; June listings are the cheapest
- Zelenogorsk has the highest average price per sq m among the top-10 localities by listing volume; Staropolye has the lowest
- Within St. Petersburg, price rises steadily with proximity to the city center — apparent dips at 3 km and a drop at 27 km turned out to be explained by the local mix of floor categories (more first/last-floor units) and a single outlier record, not by location itself
- Typical listings stay live for around 100 days (median); under 30 days is fast, over 150 days is unusually long

## Deliverables

- `Apartment Listings Price Analysis.ipynb` — full analysis notebook (data cleaning, feature engineering, exploratory analysis, price-driver analysis, conclusions)
