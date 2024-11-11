# Mapping Dataflow ETL Project

## Table of Contents
- [Objective](#objective)
- [Dataset](#dataset)
- [Steps Involved](#steps-involved)
  - [Step 1: Inject Data into Dataflow](#step-1-inject-data-into-dataflow)
  - [Step 2: Filter Transformation](#step-2-filter-transformation)
  - [Step 3: Join Transformation](#step-3-join-transformation)
  - [Step 4: Aggregate Transformation](#step-4-aggregate-transformation)
  - [Step 5: Pipeline Creation](#step-5-pipeline-creation)
  - [Step 6: Data Output](#step-6-data-output)
- [Final Transformation](#final-transformation)
- [Conclusion](#conclusion)
- [Author](#author)

## Objective
The primary objective of this project is to load and transform retail data using Azure Data Factory (ADF) to calculate the daily revenue of various products. This involves creating an ETL pipeline that processes data from a storage account, performs necessary transformations, and outputs the final result to a Parquet file.

## Dataset
The dataset used consists of two tables:
1. **Order Details**
2. **Order Items**

Both datasets are in text format, and the final objective is to compute the daily product revenue based on these tables.

## Steps Involved

### Step 1: Inject Data into Dataflow
- The **Order Details** table was ingested into the dataflow.
- The schema was defined with columns for `order_id`, `order_date`, `order_customer_id`, and `order_status`.

  ![image](https://github.com/user-attachments/assets/534ad5e4-6a98-426c-b365-d557839c496f)


  ![image](https://github.com/user-attachments/assets/6ba483ab-1ea3-4e52-8684-a972335db4bb)



### Step 2: Filter Transformation
- Applied a filter transformation to select records where the `order_status` is either "COMPLETE" or "CLOSED."
- This step ensures that only finalized orders are considered in the revenue calculation.

![image](https://github.com/user-attachments/assets/70dde261-ac9e-4156-baaf-d67be781e350)


### Step 3: Join Transformation
- Performed a join operation between the **Order Items** and **Order Details** tables using the `order_id` field.
- This merge is crucial for associating product details with the corresponding orders.

![image](https://github.com/user-attachments/assets/fb8941bc-a4c5-4bd4-9196-a7ce7b320712)


![image](https://github.com/user-attachments/assets/2ce91a37-aa1d-4946-9819-5592b403b0ce)



### Step 4: Aggregate Transformation
- Grouped the data by `order_date` and `order_item_product_id`.
- Used the aggregate function to calculate revenue by summing up the `order_item_subtotal` for each product on a given day.

![image](https://github.com/user-attachments/assets/8f7b7de1-a4ff-4b5f-a5fb-c1344d9f977e)

![image](https://github.com/user-attachments/assets/958e1c8c-f5d7-4162-8d5d-3a24d0696c28)



### Step 5: Pipeline Creation
- Created a pipeline to manage and automate the dataflow process.
- After creating the pipeline, the dataflow was published and triggered.

![image](https://github.com/user-attachments/assets/2f643754-fa1c-4685-99b8-b08988900adb)


### Step 6: Data Output
- The final transformed data was stored in a **Parquet file**, which serves as the sink.
- The resulting dataset includes three columns: `order_date`, `product_id`, and `revenue`, representing the daily revenue grouped by product and date.

![image](https://github.com/user-attachments/assets/5be73617-ccc3-4cfe-83a1-dd3bbfde0ef2)


## Final Transformation
The transformation combines data from:
- **Order Details**
- **Order Items**



![image](https://github.com/user-attachments/assets/aaa05e20-aaff-4975-a25b-6d68ad755dda)


![image](https://github.com/user-attachments/assets/7dc0cd1c-e921-4d9d-bf55-d4929728ca98)



## Conclusion
This project demonstrates the use of Azure Data Factory to perform ETL operations on a retail dataset, transforming raw data into valuable insights. The final output provides a comprehensive view of daily product revenue, which can be further used for business analysis and reporting.

## Author
**Sujeet Nayak** 
Data Engineering
