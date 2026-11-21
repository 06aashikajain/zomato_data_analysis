# Zomato Dataset Cleaning Project

This project cleans and preprocesses the raw Zomato restaurant dataset (`zomato.csv`) using Python and `pandas`, producing a cleaned dataset (`zomoto_clean_dataset`).

## Project Structure

```text
zomato-data-cleaning/
├── readme.md/
│   └── readme.md
├── requirment.txt/
│   └── requirment.txt
└── notebook.ipynb
```

## Data Cleaning Pipeline

Based on the notebook workflow, the following preprocessing steps are performed:

1. **Data Loading**: Reads `zomato.csv` into a pandas DataFrame (`zomo`). *(Note: Ensure opening quote is present: `pd.read_csv('zomato.csv')`)*
2. **Feature Selection (Dropping Irrelevant Columns)**:
   - Drops `url`, `address`, `name`, `listed_in(city)`
   - Drops `rest_type`, `dish_liked`, `reviews_list`, `menu_item`
   - Drops `phone`
3. **Deduplication**: Removes duplicate rows via `drop_duplicates()`.
4. **Handling Missing Values**:
   - Drops rows where `location` is missing (`dropna(subset=['location'])`).
   - Imputes missing `cuisines` values with `'unknown'`.
   - Imputes missing `approx_cost(for two people)` values with `'0'`.
5. **Data Type Formatting & Imputation**:
   - Removes commas from `approx_cost(for two people)` and converts the column to integer (`int`).
   - Replaces `0` values in `approx_cost(for two people)` with the column's mean.
6. **Export**: Saves the cleaned DataFrame to `zomoto_clean_dataset`.

## Setup & Usage

1. Install dependencies:
   ```bash
   pip install -r requirment.txt/requirment.txt
   ```
2. Place `zomato.csv` in the working directory.
3. Run the notebook cells sequentially to generate `zomoto_clean_dataset`.
