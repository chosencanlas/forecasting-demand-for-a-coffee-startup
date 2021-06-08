# Forecasting Demand for a Coffee Start-up with Real Sales Data
Forecasting Business Trends with Real Data with FB Prophet. By forecasting demand for cakes, the most perishable and space inefficient product of a coffee startup, we can maximize profit by reducing food waste, and simultaneously improve inventory management.

# Video Presentation: 
https://www.loom.com/share/55765ab7d9bb457eb26714dce95b0183

### Business issues faced
. Working and coordinating across time zones
. Gathering very messy data from various sources (the company had no internal data infrastructure)
. Data was so messy to the point where 


# Table of Contents

### README.md 
Contains an overview of the project from problem statement, background, methods, data description, methods, modelling, findings & conclusions, and business applications & future directions.

### 0. Overview, the Data & Instructions to create a new environment.ipynb

This notebook contains the business case, data description and instructions to create a new environment suitable to run the notebooks for this project.

### 1. Data cleaning, & Feature Engineering

This notebook contains how I clean the data and engineer features to transform the data into the format Prophet expects

### 2. Modelling with Prophet & Model Evaluation with Sklearn

I forecast the number of slices of cake sold per week using Prophet and evaluate the model using mean absolute error with Sklearn

___________________

# The Problem

The executives of a specialty coffee start-up have identified food waste as a major contributor to their cost. This decreases their profit, introduces storage issues, complications in inventory management, and becomes a government compliance legal and health risk. Food waste due to unsold food because the anticipated demand is lower than the amount of food supplies ordered or missed sales because a product was sold out can be an issue in any company within the food industry. To help the company towards financial sustainability, it is important to coordinate the orders for raw materials with demand prediction to reduce food waste, lessen impact on climate change, and increase profit.
With the time constraint in mind, I narrowed my scope to forecast the demand of the most perishable product: cakes. I will be performing a weekly forecast because raw materials are delivered at most, once a week.

However, I will be cleaning the data in anticipation of applying this project to all other perishable products in the company, and profit calculations.

# Background

Forecasting demand is as old as the market. Producers want to maximize the amount of goods sold and decrease the amount of goods unsold. The food industry is unique in that there is an additional concern: spoilage. Since their products can expire, they also need to avoid not just having unliquidated stock, but their stock expiring on their shelves. When perishable items expire, the company must absorb the loss.

Forecasting demand within the food industry is an ongoing problem that is highly complex. Various forecasting techniques have been employed in the industry from traditional statistical modelling, to machine learning and deep learning techniques.

# The Data
I acquired my data from my father’s specialty café in Manila. This was quite difficult because the company had no internal data infrastructure, and their data was not all in one place. Some of the data I asked for were only handwritten with no digital copy (i.e., delivery records of raw materials). In the end, I was only able to obtain 2 data frames.
The main data contained all sales transactions. It was located in the servers of the POS provider, and was quite difficult to obtain. When downloading all transactions of the café from the website of the provider, the server would crash several times per download attempt. Furthermore, the data set could not be downloaded in full at one time. I could only download the data month by month, so I had to resort to asking the manager to contact the POS provider to get the full data set in one .csv file. This took several weeks because both companies were not fully operational due to the current pandemic.
The second data contains the costing of all products. It was preprocessed by myself last summer when I was trying to integrate business and accounting into the marketing strategy. I had this data mostly prepared, except for some blank cells which I asked the company to fill out. This dataset contains product names, cost for each product, and profit.

# Methods Summary
This project was originally intended to be applied to all perishable products in the store. However, I had to narrow down my scope to cakes. But to prepare for future extensions of this model, I cleaned the data by recategorizing the products. The original categorization was not useful to the analysis, so I created the features ‘Category’ and ‘Subcategory’ by dividing the products according to kind while keeping items with similar expiration dates in mind.
I also merged the costing data frame with the transactions data frame, then created features ‘base price’ and ‘profit’ to prepare for profit forecasting and taking into account shipping costs. The café has an option to have free shipping given that they reach a minimum order quantity, so it will be helpful to the company if I was able to automate this process.

# Modelling Summary

For modelling I used Prophet, a library developed by Facebook in conjunction with business analysts to simplify forecasting. I tried using Prophets inbuilt cross validation and performance metrics to evaluate the model.

# Findings & Conclusions
Using mean absolute error to score the model, the weekly forecast of the number of cake slices sold per week is different from the actual sales by 13 slices on average. However, this metric takes the absolute value, it does not differentiate between actual sales being above or below the forecast. These are two completely different things. If the forecast is lower than the actual sales, and we use it to determine how much raw materials to order, we risk losing revenue through missed sales. If the forecast is higher, then we risk products expiring.

# Business Applications and Future Directions
Moving forward, I want to develop a performance metric that is designed to evaluate the model so we can see how much revenue is being lost to either missed sales, or food spoilage. Second, I want to reach my end goal of recommending when and how much raw materials to order for all products. And third, I would like to utilize other research and modelling techniques that account for factors Prophet does not see.
