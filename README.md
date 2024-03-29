# Amazon Purchase Prediction:
This is an internship project with Amazon, aiming to discover potential customers and their demographic characteristics.  
Due to privacy concerns and NDA, the original data set and other team member's codes are not allowed to be shared. The names of the files variables, and columns are also changed to ensure the privacy of content for the data.  

--- 
## Project Overview:  
- **Background**: The business has a new product that gives an in-depth view into shopping habits through web browser cookies, which are believed to provide meaningful insights into the operational strategy. Therefore, this project is made to model this behavior of future purchases and classify whether a customer will purchase in the future and those who will not.  
- **Goal**: To predict the next buyers from the Amazon website and give recommendations to Amazon warehouses based on the findings of the research.  
- **Key Findings**: KNN is the optimal model with 94% accuracy and 58% recall. Also, we found that the demographic of potential buyers is ***new customers, who last visited the website within 7 days and have a habit of visiting Amazon every 5-30 days***. In other words, those Amazon website visitors who carry such characteristics are more likely to purchase a product from Amazon compared to other people.  
 
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

- Secondly, we built a **Decision Tree** model. Due to the characteristic of the Decision Tree model (variable selection is not neccessary), we used the decision tree to again *verify the important varibles to get a better descriptive result of buyer's demographic for Amazon*. However, the decision tree, without prunning, expanded significantly and became extremely hard to interpret. The original continuous variables can provide a solution to the classification problem, but will not be descriptive when it comes to finding customer's demographic.    
  
- Hence, in order to have a more accuracy and meaningful result, we decided to ***break down the 10 original continuous variables into 35 categorical dummies.***
Below here is how I create the dummies variables:  
<img src="dummies.jpg?raw=true"/>  

**3. Model with Categorical Dummies**:  
- **Logistic Model**: we first created the Logistic Model as a benchmark model for others. The model can be summarized as:  
<img src="logit_cat.jpg?raw=true"/>  

One interesting point is that **just_visit** and **visit_last_week** came from the **last_visit** varible, which also included in our *numeric logistic model*. So these dummies actually breakdown  of what included in the previous model. Which mean, more or less, this categorical model had successfully answered our concern on the demographic of potential customers. This will be a valuable information that will be used to provide business insights and recommendation later on.  

- **Decision Tree, Random Forest, KNN, Neutral Network, XG Boosting**: we built all of the other models to compare their confusion matrixes to select the one with the best performance, and turnt out it was **KNN**. From here, we select KNN as our main model for classification.  

**4. Classification with K-Nearest-Neighbour**:  
<img src="KNN.png?raw=true"/>  
<img src="ROC.png?raw=true"/>  
**KNN** performed the best at 94% accuracy and 58% recall.  

**5. Business Recommendation:**  

- User Profile: a customer who will make the next purchase is a past user, who last visited the website within 0 to 7 days and have a habit revisiting Amazon every 5-30 days.  
- New user conversion: Personalized calls-of-action through email/target marketing to convert leads to new customers with digital engagement.  
- Current customer management:  
   
 

 









