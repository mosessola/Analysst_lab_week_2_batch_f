# Superstore Executive Sales Dashboard (Power BI)

An interactive Power BI dashboard that turns four years of retail order data into insights management can act on. Built for the **AnalystLab Africa Data Analytics Internship, Week 2: Business Intelligence & Interactive Dashboard Development**.

## Business Problem

A national retail company needs an executive dashboard to monitor sales performance, profitability, customer behaviour and regional performance. This project prepares the raw data, builds the dashboard, and turns what it shows into recommendations.

The dashboard answers seven business questions:

1. What is the overall sales performance of the company?
2. Which regions generate the highest sales and profit?
3. Which customer segments contribute the most revenue?
4. Which product categories perform best?
5. Which products are the most profitable?
6. What trends can be observed over time?
7. What recommendations should management implement to improve business performance?

## Dataset

- **Source:** Superstore Sales Dataset (Kaggle, `vivek468/superstore-dataset-final`)
- **Size:** 9,994 order lines, 21 columns (28 after cleaning, with the added calculated columns)
- **Period:** January 2014 to December 2017
- **Coverage:** Orders, shipping, customers, geography (region, state, city), products (category, sub-category) and the measures Sales, Quantity, Discount and Profit

## Data Preparation

Data cleaning was done in Python (pandas) in `notebooks/Superstore_Data_Cleaning.ipynb`, and the cleaned file was then loaded into Power BI.

- Loaded the CSV (Latin-1 encoding) and reviewed its structure
- Checked for missing values: none found
- Checked for duplicate records: none found
- Converted `Order Date` and `Ship Date` from text to dates
- Converted `Postal Code` to a 5-character text field so leading zeros are kept
- Trimmed whitespace and checked the category labels (Segment, Region, Category, Sub-Category, Ship Mode)
- Added calculated columns: `Profit Margin`, `Shipping Duration`, `Order Year`, `Order Month`, `Order Month Name`, `Order Year-Month` and `Is Loss`
- Sanity checks: no negative sales, discounts between 0% and 80%, and 1,871 loss-making order lines (18.7%)
- Exported the result as `Superstore_Cleaned.csv`

## Key Metrics (KPI Cards)

| KPI | Value |
|---|---|
| Total Sales | $2.30M |
| Total Profit | $286.4K |
| Total Orders | 5,009 |
| Average Sales per Order | $458.61 |
| Profit Margin | 12.5% |

## Dashboard Contents

- **KPI cards** for the five metrics above
- **Bar and column charts** comparing sales and profit by region, segment, category and product
- **Line chart** showing the sales and profit trend over time
- **Donut chart** showing the share of sales by segment or category
- **Map** of performance by location
- **Matrix/table** with drill-down detail
- **Slicers** for interactive filtering (for example Year, Region, Segment, Category)
- **Executive summary page** with the key insights

## Key Insights

1. **Technology and Office Supplies drive profit, while Furniture barely breaks even.** Technology earns a 17.4% margin and Office Supplies 17.0%, against 2.5% for Furniture, even though Furniture sells almost as much as Technology ($742K vs $836K).
2. **Tables and Bookcases are losing money.** Tables had $206,966 in sales but a profit of -$17,725 (-8.6% margin). Bookcases had $114,880 in sales but -$3,473 profit (-3.0% margin).
3. **The West and East outperform Central and South.** West and East bring in about 61% of total sales. Margins are West 14.9%, East 13.5%, South 11.9% and Central 7.9%.
4. **Heavy discounting is strongly associated with losses.** The 1,166 order lines discounted above 30% lost $125,007 combined, and Discount and Profit have a correlation of -0.22 across the dataset.
5. **Consumer is the largest segment, but Home Office is the most profitable per dollar.** Consumer sales are $1.16M at an 11.5% margin, while Home Office earns 14.0% and Corporate 13.0%.

## Risks and Opportunities

**Risks**
1. **Structural losses in Furniture.** Tables and Bookcases together lost $21,198 on $321,846 in sales.
2. **No guardrails on discounts.** 18.7% of order lines (1,871) were sold at a loss, totalling -$156,131, and most of those losses sit in heavily discounted lines.
3. **Regional profitability imbalance.** Central's margin (7.9%) is about half of West's (14.9%), and states such as Texas (-$25,729) and Ohio (-$16,971) lose money despite sizeable sales.

**Opportunities**
1. **Scale Technology and Office Supplies.** Together they earn $268K in profit at margins of about 17%.
2. **Grow the Home Office segment.** It is the smallest segment ($429,653 in sales) but has the highest margin (14.0%).
3. **Replicate the West's playbook.** The West leads on both sales ($725,458) and margin (14.9%), so its pricing and product mix is a template for Central and weaker states.

## Recommendations

1. **Introduce a discount cap**, for example 20% on Furniture and other low-margin sub-categories, enforced at the point of sale.
2. **Review pricing and supplier costs for Tables and Bookcases** by repricing, renegotiating costs or trimming the product range.
3. **Shift marketing and inventory investment toward Technology and Office Supplies**, the categories that convert sales into profit most efficiently.
4. **Launch an improvement plan for Central and the weakest states**, with an audit of Texas, Ohio, Pennsylvania, Illinois and North Carolina.
5. **Build a targeted Home Office growth campaign**, such as bundled office-setup products and remote-work messaging.

Full evidence for each point is in `reports/Business_Insights_and_Recommendations.docx`.

## Repository Structure

```
Analyst_Lab_2/
├── data/        # Raw Superstore dataset and the cleaned CSV
├── notebooks/   # Superstore_Data_Cleaning.ipynb (data cleaning and preparation)
├── power_bi/    # Power BI project file (.pbix)
├── reports/     # Business Intelligence Overview Report, Business Insights & Recommendations
└── Exports/     # Dashboard exports (PDF / PNG)
```

## How to Use

1. Clone or download this repository.
2. Open the `.pbix` file in `power_bi/` using **Power BI Desktop** (free, Windows).
3. If prompted, refresh the data source to point to the cleaned CSV in `data/`.
4. Use the slicers to filter by year, region, segment and category.

To see the dashboard without Power BI, open the PDF or PNG in `Exports/`.
To reproduce the cleaning, run the notebook in `notebooks/` (needs Python with `pandas` and `numpy`).

## Tools

Microsoft Power BI · Python (pandas, NumPy) · Jupyter Notebook · GitHub

## Skills Demonstrated

Data cleaning and transformation · KPI design · Dashboard design and storytelling · Business analysis · Turning data into recommendations

## Author

**MOSES OLUWATOSIN**
AnalystLab Africa, Data Analytics Internship, Week 2


#AnalystLabAfrica
