<<<<<<< HEAD
# Retail Market Basket Analysis using Apriori Algorithm of
1. Grocery Dataset
2. Online Retail

## Business Value

Market Basket Analysis is the analysis of past buying behaviourof customers to find out which are the products that are bought together by the customers. That means to find out the association between various products. If the retail's management can find this association, while placing the products in the shop, these associated products can be put together. Or, when seeing that a customer is buying a product, the salesman can offer the associated product to the customer.  

We find this association by Association Rule learning which is a machine-learning rule based approach that generates relationship between variables in a dataset. It has major application in retail industry including e-commerce. 

## Problem Statement

To determine the association between various products in the basket by analysing the customer purchase pattern of multiple items.

## Data

__Grocery data__

![](Images/Grocery%20data.PNG)

Each row of data represents a transaction and the attributes the product purchased. For value 0 the attribute item has not been purchased, for value the attribute item has been purchased in that particular transaction

__Online Retail__

![](Images/Online%20Retail.PNG)

Each row of data represents a transaction for a particular item and the attributes correspond to the following:

__InvoiceNo__ : Unique identifier for transaction 

__StockCode__ : Unique identifier for the stock item being purchased

__Description__ : Description of item

__Quantity__ : Number of units purchased

__InvoiceDate__ : Date of purchase

__UnitPrice__ : Cost of one unit of the item

__CustomerID__ : Unique Identifier for customer 

__Country__ : Country of transaction


## Approach

+ Importing Necessary Dependencies

+ Loading Data

+ Data Exploration and Visualization
	
+ Data Processing
    
	- Data Cleaning
	- Transforming data to one transaction per row
	- One Hot Encoding of purchases made

+ Generating Association Rules

+ Refining the rules 

## Evaluation

In order to establish association rules between items we will be using the apriori algorithm which uses a bottomm-up approach where frequent items (items bought together) are extended one item at a time and groups of candidates are tested against the availbale dataset. The process continues until no further extensions are found. It uses the concept of Support, Confidence and Lift to establish the rules. 

Rules which have a higher support and confidence than the predefined support and confidence are taken into account.

Support, confidence and Lift is given by:

![](Images/SCL.PNG)

## Data Exploration and Visualization

### Grocery Dataset__

__Top Sold Items__

![](Images/Top%20Items.PNG)

__Association Rules__

![](Images/Grocery%20Rules.PNG)

### Online Retail Dataset

__Processed Data__

![](Images/Clean%20Online%20Retail.PNG)

__Association Rules__

![](Images/Online%20Rules.PNG)

__Selected Rules__

![](Images/Selected%20Rules.PNG)

## __Conclusion__

__Grocery Dataset__

The rules states that people who bought _other vegetables_ are likely to purchase _root vegetables_ and the Confidence of the rule is 46% which means 46% of the time people bought _other vegetables_ they also bought _root vegetables_ and the Lift for the given rule is 2.24 which means the probability of finding the _root vegetables_ in the transactions having _other vegetables_ is greater than the normal probability of finding the it had the two items been not associated. A lift value of 1 indicates absence of association between the two items.

__Online Dataset__

Understanding the rules for this dataset we see _SET/6 RED SPOTTY PAPER PLATES_ has a confidence of 80% and lift of 6.03 with itemset _SET/20 RED RETROSPOT PAPER NAPKINS_ which means 80% of the times when the latter item was bought _SET/6 RED SPOTTY PAPER PLATES_ was also bought. 

















# Market Basket Analysis
This project performs Market Basket Analysis on two datasets:

1. Grocery Dataset
2. Online Retail Dataset

**Tools:** Python, Pandas, NumPy, Matplotlib, MLxtend



## 1. Business Value

Market Basket Analysis helps us understand which products customers usually buy together.

For example, if customers frequently purchase bread and butter together, a retail store can place these products near each other or recommend butter to customers buying bread.

This helps businesses:
- Understand customer purchasing habits.
- Recommend related products.
- Improve product placement in stores.
- Create better cross-selling strategies.
- Increase sales and customer satisfaction.

We use **Association Rule Learning**, a machine learning technique that finds relationships between different products in transaction data. It is commonly used in retail and e-commerce.




## 2. Problem Statement

The goal of this project is to identify products that are frequently purchased together by analyzing customer transactions and shopping patterns.




## 3. Datasets

### Grocery Dataset

![Grocery Dataset](Images/Grocery%20data.PNG)

The dataset contains **9,835 transactions** (shopping baskets). Each row represents one customer transaction, and each column represents a product.

- `1` means the product was purchased in that transaction.
- `0` means the product was not purchased.

### Online Retail Dataset

![Online Retail Dataset](Images/Online%20Retail.PNG)

Each row represents a purchased item in a transaction.

The dataset contains the following columns:

- **InvoiceNo:** Unique ID for each transaction.
- **StockCode:** Unique code for each product.
- **Description:** Name or description of the product.
- **Quantity:** Number of units purchased.
- **InvoiceDate:** Date and time of purchase.
- **UnitPrice:** Price of one unit.
- **CustomerID:** Unique ID of the customer.
- **Country:** Country where the transaction took place.

Only transactions from **France** are analyzed (**392 invoices** after cleaning).




## 4. Project Approach

The project follows these steps:

1. Import the required Python libraries.
2. Load both datasets.
3. Explore and visualize the data.
4. Clean and prepare the datasets.
5. Convert the data into a transaction format.
6. Apply One-Hot Encoding to represent product purchases as 0s and 1s.
7. Generate association rules using the Apriori algorithm.
8. Filter and select useful association rules.

### Data Preparation (Online Retail)

- Removed rows with a missing invoice number.
- Removed extra spaces from product descriptions.
- Removed cancelled invoices.
- Filtered the data to **France** only.
- Grouped the data by invoice and product, summed the quantities, and pivoted it into one row per invoice.
- Converted quantities into 1 (purchased) or 0 (not purchased).
- Removed the `POSTAGE` column because it is a shipping charge, not a product.




## 5. Evaluation – Apriori Algorithm

We use the **Apriori algorithm** to find products that are frequently purchased together.

Apriori follows a bottom-up approach. It first finds frequently purchased individual products and then combines them into larger groups to identify products that are commonly bought together.

It uses three important measures:

- **Support:** Shows how frequently a product or product combination appears in all transactions.
- **Confidence:** Shows how often customers purchase one product when they have already purchased another product.
- **Lift:** Shows how strongly two products are associated with each other compared to their normal purchase frequency.

![Support, Confidence and Lift](Images/SCL.PNG)

### Settings Used

| Dataset | Transactions | Minimum Support | Rule Filter |
|---|---|---|---|
| Grocery | 9,835 | 0.047 (4.7%) | Lift ≥ 1 |
| Online Retail (France) | 392 | 0.07 (7%) | Lift ≥ 6 and Confidence ≥ 0.8 |





## 6. Data Exploration and Visualization

### Grocery Dataset

**Top Selling Items**

![Top Items](Images/Top%20Items.PNG)

This visualization shows the products that were purchased most frequently.

**Association Rules**

![Grocery Rules](Images/Grocery%20Rules.PNG)

These rules show the relationships between products purchased together.

### Online Retail Dataset

**Processed Data**

![Clean Online Retail](Images/Clean%20Online%20Retail.PNG)

This shows the cleaned and processed transaction data after data preparation.

**Association Rules**

![Online Rules](Images/Online%20Rules.PNG)

These rules identify products that are frequently purchased together.

**Selected Association Rules**

![Selected Rules](Images/Selected%20Rules.PNG)

These are the selected rules based on their support, confidence, and lift values.





## 7. Conclusion

### Grocery Dataset

One of the identified rules shows a relationship between **Root Vegetables** and **Other Vegetables**.

- Confidence: 43.5%
- Lift: 2.25

This means that 43.5% of transactions containing Root Vegetables also contain Other Vegetables.

The lift value of 2.25 indicates that these products are positively associated. Customers are more likely to purchase Other Vegetables when they purchase Root Vegetables compared to the normal purchase rate.

A lift value of 1 indicates that there is no association between the products.

### Online Retail Dataset

One of the selected rules shows a relationship between:

- **SET/6 RED SPOTTY PAPER PLATES**
- **SET/20 RED RETROSPOT PAPER NAPKINS**

The results are:

- Confidence: 80%
- Lift: 6.03

This means that 80% of transactions containing SET/6 RED SPOTTY PAPER PLATES also contain SET/20 RED RETROSPOT PAPER NAPKINS.

The lift value of 6.03 indicates a strong positive association between these products.

This information can help retailers recommend related products, improve product placement, and develop cross-selling strategies.

### Limitations

- Association rules show that products are bought together, not that one purchase causes the other.
- The Online Retail analysis uses only 392 French invoices, so some rules may not hold on a larger dataset.
- The results depend on the minimum support, confidence and lift values chosen.





## 8. How to Run

**Files**

- `Market_Basket_Analysis_of_Grocery_Data.ipynb`: grocery analysis (uses `grocery_dataset.txt`)
- `Market_Basket_Analysis_of_Online_Retail.ipynb`: online retail analysis (uses `Online Retail.xlsx`)
- `Market Basket Analysis.py`: Python script version of the grocery analysis
- `Images/`: screenshots used in this README

**Install the required libraries**

```bash
pip install pandas numpy matplotlib mlxtend openpyxl
```

**Run**

1. Keep the dataset files in the same folder as the notebooks.
2. Open the notebooks in Jupyter Notebook or JupyterLab and run all cells.
=======
# Market-Basket-Analysis
>>>>>>> 5d23c47bc881713a6b06214effcc65a1de1937b8
