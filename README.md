# E-commerce Sales Analytics & Visualization

Exploratory data analysis (EDA) on the Sample Superstore dataset — customer purchasing patterns, product performance, regional trends, and profit margins, explored through interactive Plotly visualizations.

## Overview

- **Dataset:** Sample Superstore (~9,994 transactions, 21 columns, 2015–2018, US)
- **Goal:** Uncover sales trends, seasonality, and profitability drivers to support business-intelligence-style decision making
- **Type:** Data science / BI learning project, suitable for portfolio or coursework

## Tech Stack

| Component | Technology |
|---|---|
| Environment | Jupyter Notebook |
| Language | Python 3.x |
| Data Processing | Pandas |
| Visualization | Plotly (Express & Graph Objects), Plotly.io, Plotly.colors |
| Data Format | CSV (Latin-1 encoded) |

## Project Structure

```
E-commerce/
├── README.md                     # Project description
├── Sample - Superstore (1).csv   # Dataset (9,994 records, 21 columns)
└── Untitled22.ipynb              # Main analysis notebook
```

## Dataset Schema

| Category | Columns |
|---|---|
| Identifiers | Row ID, Order ID, Customer ID, Product ID |
| Dates | Order Date, Ship Date, Order Month, Order Year, Order Day of Week |
| Customer Info | Customer Name, Segment, Country, City, State, Region, Postal Code |
| Product Info | Category, Sub-Category, Product Name |
| Metrics | Sales, Quantity, Discount, Profit, Ship Mode |

**Key Stats**
- Avg sales: $229.86/order
- Avg quantity: 3.79 units/order
- Profit range: -$6,599.98 to +$8,399.98
- Discount range: 0%–80%
- Categories: Furniture, Office Supplies, Technology
- Segments: Consumer, Corporate, Home Office
- Ship modes: Standard Class, Second Class, First Class, Same Day

## Workflow

1. **Data Exploration** — inspect structure, `describe()`, `info()`, check dtypes/missing values
2. **Data Cleaning** — standardize dates, handle Latin-1 encoding, validate integrity
3. **Feature Engineering** — derive `Order Month`, `Order Year`, `Order Day of Week` from `Order Date`
4. **Aggregation & Grouping** — e.g., monthly sales via `groupby`
5. **Visualization** — interactive Plotly charts (`plotly_white` theme, hover tooltips)

### Sample Code

```python
import pandas as pd

# Load data
data = pd.read_csv("Sample - Superstore.csv", encoding='latin-1')

# Convert dates
data['Order Date'] = pd.to_datetime(data['Order Date'])
data['Ship Date'] = pd.to_datetime(data['Ship Date'])

# Feature engineering
data['Order Month'] = data['Order Date'].dt.month
data['Order Year'] = data['Order Date'].dt.year
data['Order Day of Week'] = data['Order Date'].dt.dayofweek

# Monthly sales aggregation
sales_by_month = data.groupby('Order Month')['Sales'].sum().reset_index()
```

## Key Findings

**Monthly Sales Trends**
- Highest: November ($352K), December ($325K), September ($307K) — holiday season surge
- Lowest: February ($59K) — post-holiday decline
- Clear Q4-dominant seasonal pattern

**Profit Analysis**
- Average profit: $28.66/transaction
- High variance indicates some product/segment combinations are loss-making
- Discount levels correlate with profitability

## Use Cases

- **Business Intelligence** — sales trend and seasonality identification
- **Marketing Analytics** — customer segment performance
- **Financial Planning** — profit margin optimization by product/region
- **Learning** — hands-on BI workflow using the Python data stack

## Getting Started

```bash
pip install pandas plotly jupyter
jupyter notebook Untitled22.ipynb
```
