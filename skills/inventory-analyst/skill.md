---
name: inventory-analyst
description: Analyze inventory and sales data to project demand, determine stock-out dates, and recommend reorder timing
---

# Inventory Analyst

## Overview
Analyzes inventory and sales data to project monthly demand for 12 months, determine stock-out dates, calculate reorder points, and recommend order timing and quantities. Applies trend analysis and seasonality adjustments.

## When to Use This Skill
- Monthly inventory planning
- Preparing purchase orders
- Identifying slow-moving or at-risk stock
- Forecasting cash flow needs for inventory

## Process

### Step 1: Data Intake
Gather:
- Current inventory levels (units by SKU)
- Historical sales data (12+ months preferred)
- Lead times per supplier
- Minimum order quantities
- Storage constraints
- Seasonal factors

### Step 2: Demand Forecasting
For each SKU:
- Calculate average monthly sales
- Identify trend (growing, stable, declining)
- Apply seasonality adjustments
- Project monthly demand for next 12 months

### Step 3: Stock-Out Analysis
- **Days of stock remaining**: Current inventory / daily sales rate
- **Projected stock-out date**: Based on forecasted demand
- **Risk level**: Critical (<2 weeks), Warning (<4 weeks), OK (>4 weeks)

### Step 4: Reorder Recommendations
- **Reorder point**: Lead time demand + safety stock
- **Safety stock**: Based on demand variability and service level target
- **Order quantity**: Economic order quantity or supplier MOQ (whichever is higher)
- **Order date**: Reorder point date minus lead time

### Output
```markdown
## Inventory Report: [Date]

### Critical Actions
[Items needing immediate reorder]

### 30-Day Forecast
| SKU | Current | Monthly Rate | Stock-Out Date | Reorder By | Order Qty |
|-----|---------|-------------|----------------|------------|-----------|

### Trend Alerts
[Items with significant demand changes]

### Cash Flow Impact
[Total inventory investment needed for next 30/60/90 days]
```

## Key Rules
- Never forecast without at least 3 months of historical data
- Always include safety stock — stockouts are more expensive than overstock
- Flag items where demand is changing significantly
- Consider cash flow constraints, not just optimal inventory levels
- Update forecasts monthly as new sales data comes in
