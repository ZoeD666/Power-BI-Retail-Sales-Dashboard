<img width="2213" height="1231" alt="image" src="https://github.com/user-attachments/assets/7cec6453-b854-44d9-ab4a-4c78fce93bd6" /># Retail Sales & Customer Insights Dashboard

**Tool:** Power BI Desktop  
**Dataset:** Kaggle - Online Retail Dataset (Public)  

<img width="2213" height="1231" alt="image" src="https://github.com/user-attachments/assets/496fddda-c3a8-4f57-b2b5-9111c422bd63" />
---

### Objective

This dashboard is designed to provide clear and intuitive business insights for retail operations, focusing on:

- Key metrics such as net sales, return rate, and converted customer count  
- Sales performance by product category and by country  
- Customer quality analysis (Repeat Rate, Average Order Per Customer)  
- Actionable visual analysis to support business optimisation  

---

### Data Preparation & Modeling

Data cleaning and transformation steps in Power BI Power Query include:

- Import the dataset (Excel)  
- Combine the two original tables (`YEAR 2009-2010` and `YEAR 2010-2011`) into a single merged table called `Retail_ALL`  
- Import the product category dimension table `Category`  
- Convert data types (e.g. date and number formats)  
- Remove missing values and invalid transactions (e.g. blank descriptions or zero-value orders)  
- Identify refund transactions by invoice prefix "C"  
- Add calculated columns: `TotalAmount`, `IsReturn`, `Year`, `Month`  
- Filter out non-regular transactions (e.g. shipping fees and financial entries)  
- Build relationships between fact and dimension tables (`Retail_All`, `Category`, `Measure`) using the "Description" field  

---

### Key DAX Measures

| Measure Name              | Description                                                  |
|--------------------------|--------------------------------------------------------------|
| Net Sales                | Net sales amount excluding refunds                           |
| Return Rate              | Refund amount as a percentage of total sales                 |
| ConvertedCustomerCount   | Number of unique customers with non-zero transactions        |
| AvgOrderPerCustomer      | Net Sales divided by ConvertedCustomerCount                  |
| RepeatCustomerCount_60Days | Customers with 2+ purchases within last 60 days (excluding same-day orders) |
| RepeatRate               | RepeatCustomerCount_60Days / ConvertedCustomerCount          |
| ReturnAmount             | Total refund value                                           |
| TotalOrderAmount         | Total sales including refunds                                |
| ReturnAmountbarchart     | Special field for return bar chart visualisation             |

---

### Dashboard Layout & Visuals

#### KPI Cards
- **Net Sales:** Total net revenue  
- **Return Rate:** Percentage of refund  
- **ConvertedCustomer:** Number of real customers  
- **AvgOrderPerCustomer:** Average order value per customer  
- **Repeat Rate:** % of customers who made 2+ purchases in the last 60 days  

#### Middle Visuals
- **Area Chart:** Net Sales and ReturnAmount by Month  
- **Bar Chart:** Net Sales and ReturnAmount by Category  
- **Map:** Sales by Country  
- **Bubble Chart:** Sales Quantity & Average Price by Category  
  - X-axis: Average price per category  
  - Y-axis: Total quantity sold  
  - Bubble size: Sales volume; bubble color: Category  
  - Easily spot high-volume/high-price and low-volume/low-price categories  

#### Filter & Tooltip
- **Filter:** Enables selection by year, month, country, and category, with all cards and visuals updating dynamically in response.  
- **Tooltip:** Each card includes a tooltip explanation (e.g., Repeat Rate = % of customers with 2+ purchases on different dates within last 60 days)  

#### Drill-down & Drill-through
- **Drill-down:** Daily Net Sales and Return Amount for the selected Month  
- **Drill-down:** Monthly Net Sales for the selected Category  
- **Drill-through:** Pie chart of Net Sales by Category for selected countries  

---

### Business Value & Use Cases

| Use Case          | Explanation                                                         |
|-------------------|---------------------------------------------------------------------|
| Sales Analysis     | Identify monthly trends and product-level performance              |
| Product Decisions  | Detect high-return items for improvement or removal                |
| Customer Insights  | Measure customer loyalty and purchase behaviour                    |
| Market Strategy    | Use geographic data to prioritise target regions                   |
