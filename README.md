# 📊 INVENTORY OPTIMIZATION FOR RETAIL - Dashboard

An **interactive Power BI dashboard** designed for **inventory optimization** in the retail sector. This project integrates insights from **demand forecasting**, **inventory monitoring**, **pricing analysis**, **product metadata**, and **managerial performance** to support data-driven business decisions.

---

## 🎯 Objective

To build an executive-level **Power BI dashboard** that enables stakeholders to:
- Monitor inventory levels and turnover rates in real time
- Analyze pricing impacts on sales volume and revenue
- Identify underperforming regions, products, and managers
- Optimize product availability and reduce stockouts

---

## 🧰 Tools & Technologies

- Python & Mysql for Data Cleaning 
- Power BI 
- Power Query & DAX
- Light Beige Theme with Brown/Gold Accents

---

## 📁 Data Sources

| File                      | Description                                      |
| ------------------------- | ----------------------------------------------- |
| `demand_forecasting.csv`  | Historical and predicted product demand          |
| `inventory_monitoring.csv`| Inventory levels, stockouts, turnover ratio      |
| `pricing_optimization.csv`| Price, discount, and margin optimization data    |
| `product_master.csv`      | SKU-level metadata: category, subcategory        |
| `manager_details.csv`     | Regional/manager hierarchy                       |
| `date.csv`                | Calendar table for time intelligence             |

---

## 📊 Dashboard Sections

### 1. 🏠 Cover Page
- Title - **Inventory Optimization for Retail**
- Light themed 3D background 
- Bookmark based Navigation Menu

---

### 2. 📈 Sales Overview
- KPIs - **Total Revenue**, **Total Quantity**, **Total Product**
- Line Chart - Monthly Sales Trend
- Bar Chart - Revenue by subcategories 
- Pie chart - Customer Segments
- Donut chart - Seasonality Factors
- Filters - Quarter, Category

---

### 3. 📦 Inventory Monitoring
- KPIs - **Inventory Level**, **Turnover**, **Utilization**, **Average Stockout Frequency**, **Order fulfillment**
- Bar Chart - Inventory Level by Category
- Donut Chart - Stockout % by Category
- Matrix - Inventory Status with conditional icons 
- Filters - Category

---

### 4. 💰 Pricing Strategy
- KPIs - **Average Price**,**Average Competitor Price**, **Average Discount**, **Average Return Rate**
- Line and stacked column chart - Price vs Sales Volume
- Gauge - Sales Volume VS Return Rate, Price VS Competitor Price
- Slicers - Category

---

### 5. 🧑‍💼 Manager Insights
- Table - Manager Performance 
- Area chart - Revenue by Location 
- Clustered bar chart - Revenue by Categories 

---

## 🧠 DAX Highlights

```DAX

Total Revenue = SUMX('demand_forecasting', 'demand_forecasting'[SalesQuantity] * 'demand_forecasting'[Price])

Stock Utilization = SUM(inventory_monitoring[StockLevels]) - SUM(demand_forecasting[SalesQuantity])

Inventory Turnover = DIVIDE([Total Quantity], [Inventory Level], 0)

Total Quantity = SUM('demand_forecasting'[SalesQuantity])

Total Product = DISTINCTCOUNT('demand_forecasting'[ProductID])

Inventory Level = SUM(inventory_monitoring[StockLevels])

Inventory Status =
SWITCH(TRUE(),
    'inventory_monitoring'[Inventory Level] = 0, "🟥 Stockout",
    'inventory_monitoring'[Inventory Level] < 'inventory_monitoring'[Reorder Level], "🟨 Low",
    'inventory_monitoring'[Inventory Level] <= 'inventory_monitoring'[Reorder Level] * 2, "🟩 Sufficient",
    "🟦 Overstock"
)

Stockout % = 
DIVIDE(
    COUNTROWS(FILTER('inventory_monitoring', 'inventory_monitoring'[StockLevels] = 0)),
    COUNTROWS('inventory_monitoring')
)

Avg Stockout Frequency = AVERAGE('inventory_monitoring'[StockoutFrequency])

Avg Return Rate = AVERAGE(pricing_optimization[ReturnRate])

Avg Order Fulfillment = AVERAGE(inventory_monitoring[OrderFulfillmentTime])

Avg Discount = AVERAGE('pricing_optimization'[Discounts])

Avg Competitor Price = AVERAGE('pricing_optimization'[CompetitorPrices])

Average Price = AVERAGE(demand_forecasting[Price])

Sales After Discount = SUMX(pricing_optimization, [Price] - [Discounts])

Sales with Promotions = CALCULATE([Total Quantity], demand_forecasting[Promotions] = "Yes")

```

---

## 🖼️ Design Guidelines

* Theme: Light beige with gold/brown accents
* Font: Segoe UI or Calibri
* Icons/Emojis for KPI highlights
* Consistent card styling (rounded edges, shadow)
* Page navigation using buttons or bookmarks

---

## ✅ Key Benefits

* Real-time inventory alerts using DAX logic
* Improved pricing decisions via visual analysis
* Executive-level KPIs for fast insights
* Drill-through to manager-level data

---

## 👤 Author

**Meshva Patel**  
Power BI Developer | Data Analyst  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/meshva-patel-8750b02b7)

---

## 📌 Tags

```
#PowerBI #InventoryOptimization #RetailAnalytics #DataVisualization #PricingStrategy #DataStorytelling #DashboardDesign

