# Data Dictionary — Store Sales Forecasting

---

## Target Variable

| Column | Type | Description |
|---|---|---|
| sales | float | Total sales for a product family at a particular store on a given date |

---

## train.csv

| Column | Type | Description |
|---|---|---|
| id | int | Unique row identifier |
| date | date | Date of the sale |
| store_nbr | int | Store identifier |
| family | str | Product category (e.g. GROCERY I, BEVERAGES, DAIRY) |
| sales | float | Total sales for that store/family/date |
| onpromotion | int | Number of items in that family on promotion at that store on that date |

---

## stores.csv

| Column | Type | Description |
|---|---|---|
| store_nbr | int | Store identifier |
| city | str | City where the store is located |
| state | str | State where the store is located |
| type | str | Store type/category (A–E) |
| cluster | int | Grouping of similar stores |

---

## holidays_events.csv

| Column | Type | Description |
|---|---|---|
| date | date | Date of the holiday or event |
| type | str | Holiday, Event, Additional, Transfer, Bridge, or Work Day |
| locale | str | Scope of the holiday: National, Regional, or Local |
| locale_name | str | Specific region/city the holiday applies to |
| description | str | Name/description of the holiday or event |
| transferred | bool | Whether the holiday was officially moved to another date |

---

## oil.csv

| Column | Type | Description |
|---|---|---|
| date | date | Date of the oil price record |
| dcoilwtico | float | Daily WTI crude oil price (USD), used as a proxy for Ecuador's oil-dependent economy |

---

## transactions.csv

| Column | Type | Description |
|---|---|---|
| date | date | Date of the transactions record |
| store_nbr | int | Store identifier |
| transactions | int | Number of transactions recorded at that store on that date |

---

## Engineered Features

Features created during data cleaning and feature engineering:

| Column | Description |
|---|---|
| is_holiday | Binary flag — 1 if the date is a national holiday, 0 otherwise |
| year | Year extracted from date |
| month | Month extracted from date |
| day | Day of month extracted from date |
| day_of_week | Day of week (0 = Monday, 6 = Sunday) |
| week_of_year | ISO week number of the year |
| is_weekend | Binary flag — 1 if Saturday or Sunday, 0 otherwise |
| quarter | Calendar quarter (1–4) |
| sales_lag_7 | Sales value for the same store/family 7 days earlier |
| sales_lag_14 | Sales value for the same store/family 14 days earlier |
| sales_lag_28 | Sales value for the same store/family 28 days earlier |
| rolling_mean_7 | Rolling average of sales over the previous 7 days (store/family group) |
| rolling_mean_14 | Rolling average of sales over the previous 14 days (store/family group) |
| rolling_mean_28 | Rolling average of sales over the previous 28 days (store/family group) |

---

## Removed Features

| Column | Reason |
|---|---|
| id | Row identifier — no predictive value |
| date | Replaced by extracted time-based features (year, month, day, day_of_week, etc.) |
