# Online Retail Sales Dashboard in Excel
## Project Overview 
The primary objective of this project is to conduct an exploratory analysis of the Global Superstore dataset, which comprises data on sales, customers, and shipping details from multiple countries. Our goal is to uncover insights, trends, and patterns that can assist in making informed business decisions. The findings will be showcased in an interactive dashboard, facilitating easy exploration and interpretation of the data.
## Data
The dataset in the `Global_Superstore2.xlsx` file contains a collection of 51,290 orders from a global superstore, covering a time frame from 01/01/2011 to 12/31/2014. Each row represents an individual order, and the dataset is comprised of both categorical and numerical columns. A brief description of each column is provided in the table below:

| Column Name    | Description                                             | Data Type      |
| -------------- | ------------------------------------------------------- | -------------- |
| Row ID         | Row identification number                               | Numeric        |
| Order ID       | Identification number of the order                      | Text           |
| Order Date     | Date when the order was placed                          | Text (Date)    |
| Ship Date      | Date when the order was shipped                         | Text (Date)    |
| Ship Mode      | Shipping method used for the order                      | Text           |
| Customer ID    | Identification number of the customer                   | Text           |
| Customer Name  | Name of the customer                                    | Text           |
| Segment        | Customer segment (e.g., Consumer, Corporate, etc.)      | Text           |
| City           | City where the order was placed                         | Text           |
| State          | State where the order was placed                        | Text           |
| Country        | Country where the order was placed                      | Text           |
| Postal Code    | Postal code of the delivery address (mainly U.S.)       | Numeric        |
| Market         | Market in which the order was made                      | Text           |
| Region         | Region where the order was placed                       | Text           |
| Product ID     | Identification number of the product                    | Text           |
| Category       | Category of the product                                 | Text           |
| Sub-Category   | Sub-category of the product                             | Text           |
| Product Name   | Name of the product                                     | Text           |
| Sales          | Sales amount for the order                              | Numeric        |
| Quantity       | Quantity of items ordered                               | Numeric        |
| Discount       | Discount applied to the order                           | Numeric        |
| Profit         | Profit made from the order                              | Numeric        |
| Shipping Cost  | Cost of shipping for the order                          | Numeric        |
| Order Priority | Priority of the order (e.g., Medium, High, etc.)        | Text           |

The data was sourced from Kaggle:
[Download the dataset](https://www.kaggle.com/datasets/apoorvaappz/global-super-store-dataset/data)
## Data Analytics Workflow

Our analytical journey will traverse through a well-defined process comprising of the following key steps:

`Data Check` → `Explore Data` → `Analyze & Visualize Data` → `Dashboarding` → `Communicate Insights`
### Data Check
Begin by converting the `Order Date` and `Ship Date` columns to the `Date` data type. To do this, select both columns and choose `Date` from the dropdown menu in the `Home` ribbon. 

![image](images/DateType.png)

Next, lets check for duplicates. To do this, highlight all the data, then navigate to the `Data` tab in the menu bar and select the `Remove Duplicates` option.

![image](images/removing_duplicates.png)

Upon initial examination, no duplicate values were identified. Next, we'll proceed to check for missing values. This can be done by formatting the data into a table and then clicking on each column filter to look for any `Blanks` entries.

![image](images/missing_values.png)

We've identified missing values in the `Postal Code` column. Since we don't need the postal code for this analysis we will proceed to remove this column. 
### Explore Data
The next step in our workflow is to conduct an exploratory data analysis to summarize the data and determine key performance indicators. Begin by creating a new worksheet named `Explore Data`. Given that we're using Excel for Mac, it's essential to set up a `Distinct Customer Count` column and a `Distinct Order Count` column to get a unique count of all customers and orders when creating a pivot table, which will serve as a key performance indicators (KPIs). To do this, add a new column named `Distinct Customer Count` to the `Raw Data` worksheet and apply the following formula:
```excel
=IF(COUNTIF($G$2:G2,G2)>1,0,1)
```
Do the same for `Distinct Order Count`:
```excel
=IF(COUNTIF($B$2:B2,B2)>1,0,1)
```
![image](images/distinct.png)

By summing the values in these column within the pivot table, we can determine the unique count of customers and orders. Next, let's add an `Order Year` column adjacent to the `Order Date` column. This will allow us to filter our pivot table by year. We can extract the year from the order date using this formula:
```excel
=YEAR([@[Order Date]])
```

![image](images/OrderYear.png)

Next, navigate to the `Raw Data` worksheet, select all of its contents, go to the `Insert` tab, and choose the `PivotTable` option. Ensure you place the pivot table in the newly created worksheet.

![image](images/PivotTable1.png)

In the `Values` section of the PivotTable, drag the columns `Sales`, `Profit`, `Distinct Customer Count`, and `Distinct Order Count`. Format the sums of both Sales and Profit as `Currency`. Meanwhile, ensure the sums of Customer Count and Order Count are formatted as `Numbers`, rounded to the nearest whole number.

![image](images/KPIs.png)

