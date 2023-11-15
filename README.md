# Ecommerce Sales Analysis

![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Dashboard%20Overview.png)

[**Link to Dashboard in Tableau Public**](https://public.tableau.com/app/profile/joel.obafemi/viz/EcommerceSalesDashboard_16998760932500/DashboardOverview?publish=yes)

# Introduction
The project presents a high-level view of an e-commerce store's performance, including customer demographics, sales, and transactional behaviour. 

# Problem Statement
The e-commerce store seeks to understand its performance in various dimensions to identify any potential issues or areas for improvement. A key issue discovered from this analysis was customer retention as the store had a significant churn rate.

Handling churn in e-commerce requires a multifaceted approach.

It's about creating a balance between winning back customers and understanding the reasons behind their departure.

Here's a streamlined strategy to address this:

🔄 **Optimize Post-Purchase Experience**: This includes addressing buyer's remorse, ensuring product adoption, and providing exceptional customer service through thoughtful follow-ups.

👗 **Refreshing Product Lines**: For a category like clothing, introducing new collections maintains a fresh and appealing product range. This helps attract new customers and re-engage existing ones, thereby reducing churn.

🚀 **Effective Onboarding and Education**: Ensuring customers understand and enjoy the product through effective onboarding and education increases the likelihood of customer loyalty.

⏰ **Monitor Repurchase Patterns**: Analyze repurchase rates and the time lag between orders to understand customer buying behaviours. These insights can be used to optimize communication, especially in critical periods, to encourage repeat sales.

🌐 **Building Diverse Retention Channels**: If engagement drops in one channel, another can take its place, ensuring consistent communication and reducing churn.

🔎 **Learn from Churn**: When re-engaging a customer isn't possible, gathering qualitative feedback is essential. This information is crucial for improving all aspects of the customer journey, from acquisition to post-purchase.

A high return rate during some periods was also discovered. Soliciting and analyzing customer feedback, especially during high return periods, is crucial. This direct line of insight allows the store to understand the ‘why’ behind returns which is crucial for impactful improvements.

## SQL Queries

1. **Average Customer Age:**

   SELECT AVG (Customer_Age) AS Average_Customer_Age

   FROM ecommerce_customer_data

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Average%20Customer%20Age.png)

2. **Top Selling Product Category By Revenue:**

    SELECT (Product_Category) AS Product_Category,

    SUM (Total_Purchase_Amount) AS Total_Revenue

    FROM ecommerce_customer_data

    GROUP BY Product_Category

    ORDER BY Total_Revenue DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Top%20Selling%20Category.png)

3. **Top Selling Product Category By Quantity:**

    SELECT (Product_Category) AS Product_Category,

    SUM (Quantity) AS Total_Quantity

    FROM ecommerce_customer_data

    GROUP BY Product_Category

    ORDER BY Total_Quantity DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Top%20Category%20By%20Quantity.png)

4. **Total Revenue Per Month (2020):**

    SELECT DATENAME (MONTH, Purchase_Date) AS Month_Name, DATENAME (YEAR, Purchase_Date) AS Year_Name,

    SUM (Total_Purchase_Amount) AS Total_Sales

    FROM ecommerce_customer_data

    WHERE DATENAME (YEAR, Purchase_Date) = '2020'

    GROUP BY DATENAME(MONTH, Purchase_Date),  DATENAME (YEAR, Purchase_Date)

    ORDER BY Total_Sales DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Revenue%20-%202020.png)

5. **Total Revenue Per Month (2021):**

    SELECT DATENAME (MONTH, Purchase_Date) AS Month_Name, DATENAME (YEAR, Purchase_Date) AS Year_Name,

    SUM (Total_Purchase_Amount) AS Total_Sales

    FROM ecommerce_customer_data

    WHERE DATENAME (YEAR, Purchase_Date) = '2021'

    GROUP BY DATENAME(MONTH, Purchase_Date),  DATENAME (YEAR, Purchase_Date)

    ORDER BY Total_Sales DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Revenue%20-%202021.png)

6. **Total Revenue Per Month (2022):**

    SELECT DATENAME (MONTH, Purchase_Date) AS Month_Name, DATENAME (YEAR, Purchase_Date) AS Year_Name,

    SUM (Total_Purchase_Amount) AS Total_Sales

    FROM ecommerce_customer_data

    WHERE DATENAME (YEAR, Purchase_Date) = '2022'

    GROUP BY DATENAME(MONTH, Purchase_Date),  DATENAME (YEAR, Purchase_Date)

    ORDER BY Total_Sales DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Revenue%20-%202022.png)

7. **Total Revenue Per Month (2023):**

    SELECT DATENAME (MONTH, Purchase_Date) AS Month_Name, DATENAME (YEAR, Purchase_Date) AS Year_Name,

    SUM (Total_Purchase_Amount) AS Total_Sales

    FROM ecommerce_customer_data

    WHERE DATENAME (YEAR, Purchase_Date) = '2023'

    GROUP BY DATENAME(MONTH, Purchase_Date),  DATENAME (YEAR, Purchase_Date)

    ORDER BY Total_Sales DESC

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Revenue%20-%202023.png)

8. **Total Payments Made By PayPal:**

    SELECT COUNT (Payment_Method) AS PayPal

    FROM ecommerce_customer_data

    WHERE Payment_Method = 'PayPal'

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Payments%20By%20PayPal.png)

9. **Total Payments Made By Credit Card:**

    SELECT COUNT (Payment_Method) AS Credit_Card

    FROM ecommerce_customer_data

    WHERE Payment_Method = 'Credit Card'

   ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Payment%20By%20PayPal.png)

10. **Total Payments Made By Cash:**

    SELECT COUNT (Payment_Method) AS Cash

    FROM ecommerce_customer_data

    WHERE Payment_Method = 'Cash'

    ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Payment%20By%20Cash.png)

11. **Top 10 Customers By Revenue:**

    SELECT DISTINCT TOP 10

    (Customer_Name) AS Customer_Name,

    SUM (Total_Purchase_Amount) AS Total_Spend

    FROM ecommerce_customer_data

    GROUP BY Customer_Name

    ORDER BY Total_Spend DESC

    ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Top%2010%20Customers%20By%20Revenue.png)

12. **Top 10 Customers By Returns:**

    SELECT TOP 10 

    (Customer_Name) AS Customer_Name,

    COUNT (Returns) AS Total_Returns

    FROM ecommerce_customer_data

    GROUP BY Customer_Name

    ORDER BY Total_Returns DESC

    ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Top%2010%20Customers%20By%20Returns.png)

13. **Total Returns Per Year:**

    SELECT DATENAME (YEAR, Purchase_Date) AS Year_Name,

    COUNT (Returns) AS Total_Returns

    FROM ecommerce_customer_data

    GROUP BY DATENAME (YEAR, Purchase_Date)

    ORDER BY Total_Returns DESC

    ![](https://github.com/Joel-web3/Ecommerce_Sales_Analysis/blob/main/Total%20Returns%20By%20Year.png)

# Recommendations

- **Customer Retention**: Implement targeted retention strategies, especially around the mid-year when churn rates spike. This could include loyalty programs or special promotions to encourage repeat purchases.

- **Enhance Payment Systems**: Given the preference for credit card payments, ensure the payment system is robust, secure, and streamlined to avoid checkout friction.

- **Product Quality and Satisfaction**: Investigate the cause of high return rates in specific months and address any product quality issues. Customer feedback can be leveraged to improve product offerings.

- **Diversify Customer Base**: While the store has key customers generating significant revenue, diversification is crucial. Marketing efforts should be broadened to reduce dependence on a small number of big spenders.

- **Demographic Outreach**: Tailor marketing campaigns to engage other demographic segments, particularly females and younger age groups, to expand the customer base and increase market share.

