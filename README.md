# Superstore Sales Data Analysis

Exploratory data analysis and two small classification experiments on retail sales data, written in Python in a Jupyter Notebook. This was a project for my Data Science Technologies course at the University of Management and Technology (UMT), Lahore.

## Dataset

`train.csv` contains 9,800 order lines with 18 columns, including order and ship dates, ship mode, customer segment, city, state, region, product category, sub-category and sales amount. It is the public Superstore sales dataset; add the source link here (for example the Kaggle page you downloaded it from).

## What the notebook does

1. **Data inspection and cleaning:** summary statistics (mean, standard deviation, coefficient of variation, percentiles), a missing-value check (11 missing postal codes, rows removed) and a duplicate check (none found).
2. **Customer analysis:** customer segments, sales per segment, order frequency and top-spending customers.
3. **Shipping analysis:** use and sales of each ship mode, with box plots to spot outliers.
4. **Geographic analysis:** customers and sales by state and city.
5. **Product analysis:** sales by category and sub-category.
6. **Sales over time:** yearly, quarterly and monthly trends, plus a correlation heatmap of the numeric columns.
7. **Classification experiments:** k-nearest-neighbours (a from-scratch implementation and scikit-learn) and logistic regression, each compared with a majority-class baseline.

## Findings noted in the notebook

- Consumers are the largest customer segment, in both number of customers and total sales.
- Standard Class is the most used shipping mode and has the highest sales.
- California has the highest sales by state, and New York by city.
- Technology is the highest-selling category, and Phones the highest-selling sub-category.

## Classification results

| Experiment | Majority-class baseline | Model result |
|---|---|---|
| 1. Predict product category from sales and segment | 60.3% | k-NN (scikit-learn) 62.0%; from-scratch k-NN 63.6% vs scikit-learn 64.4% on the same first 500 test rows |
| 2. Predict whether a sale is above average (from sub-category, region, ship mode, segment) | 76.3% | Logistic regression 81.8% |

- **Experiment 1:** the from-scratch k-NN matches scikit-learn, which confirms the implementation works. Both are only slightly above the baseline, so sales amount and segment say little about the product category.
- **Experiment 2:** the model identifies below-average sales well (recall 0.93) but finds only 45% of above-average sales (recall 0.45). With balanced class weights it finds 83% of them, but precision falls to 0.46 and overall accuracy to 73.3%, so the better choice depends on whether a missed high-value sale or a false alarm costs more.

## How to run

```bash
pip install -r requirements.txt
jupyter notebook superstore-sales-analysis.ipynb
```

Keep `train.csv` in the same folder as the notebook. The from-scratch k-NN is written in plain Python and takes a minute or two to run.

## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, Jupyter Notebook

## Author

Kausar Arshad, BS Computer Science, University of Management and Technology
