# Amazon Purchase Prediction:
This is a academic project with the aim of predicting the potential customers and their demographic characteristics.  
Due to privacy concern, the original data set and other team member's codes are not allowed to be shared. The name of the files and variables, columns are also changed to ensure the privacy of content for the data.  

--- 
## Project Overview:  
- **Background**: The business has a new product which gives an in-depth view into shopping habits through web browser cookies, which are believed to provide menaningful insights to the operational strategy. Therefore, this project is made to model to this behavior of future purchases and classify whether a customer will purchase in the future and those who will not.  
- **Goal**: To predict the next buyers from Amazon website and give recommendation to Amazon warehouses based on the findings of the research.  
- **Key Findings**: KNN is the optimal model with 94% accuracy and 58% recall. Also, we found that the demographic of potential buyers are ***new customers, who last visited the website within 7 days and have a habit of visiting Amazon every 5-30 days***. In other words, those Amazon website visitors who carries such characteristics are more likely to purchase a product from Amazon comparing to other people.  
 
---
## Project Outlines:
**1. Data Cleaning and EDA:**  
- Fill in the NaN with 0, drop 'Unamed' columns. 
- Plot histogram, correlation matrix, and VIF scores to test multicolinearity.  
- Realized the data is highly skewed toward y_buy ( dependent variable), hence various approach had been taken to cope with this imbalanced data set, namely *Undersampled, Oversampled and SMOTE*. As a result, we decided that **Undersample** will be the most suitable method for this dataset. Briefly, Undersampling techniques remove examples from the training dataset that belong to the majority class in order to better balance the class distribution, such as reducing the skew from a 1:100 to a 1:10, 1:2, or even a 1:1 class distribution.  
  In our case, the Undersampled result can be illustrated as:   
<img src="Undersampled.png?raw=true"/>  

**2. Model Building:**    
- Firstly, we built **OLS** as a benchmark for variables selection for other model, then applying Backward Selection to filter valuable varibles. From there, using VIF to eliminate multicollinearity of the selected variables to build a **Logistic Regression**. The two models can be illustrated as:  
<img src="Logit + OLS.png?raw=true"/>  

- Secondly, we built a **Decision Tree** model. Due to the characteristic of the Decision Tree model (variable selection is not neccessary), we used the decision tree to again *verify the important varibles to get a better descriptive result of buyer's demographic for Amazon*. However, the decision tree, without prunning, expanded significantly and became extremely hard to interpret.    
  
- Hence, in order to have a more accuracy and meaningful result, we decided to ***break down the 10 original continuous variables into 35 categorical dummies.***

**3. Model with Categorical Dummies**:  
- **Logistic Model**: we first created the Logistic Model as a benchmark model for others. The model can be summarized as:  
<img src="logit_cat.jpg?raw=true"/>


