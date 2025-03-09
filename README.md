# **PHASE 3 PROJECT.**


## **CUSTOMER CHURN PREDICTION FOR SYRIATEL: LEVERAGING PREDICTIVE ANALYTICS TO RETAIN CUSTOMERS**

---

### **OVERVIEW.**

Customer churn is a significant challenge in the telecommunications industry, where companies like SyriaTel face financial losses due to customers discontinuing their services. This project focuses on developing a binary classification model to predict whether a customer is likely to churn. The insights derived from this model will empower SyriaTel to proactively identify at-risk customers, implement targeted retention strategies, reduce churn rates, and improve long-term revenue.

---

### **BUSINESS UNDERSTANDING.**

#### **Objective.**

SyriaTel is experiencing revenue losses due to customer attrition. Retaining existing customers is more cost-effective than acquiring new ones. The primary objective of this project is to develop a binary classification model to predict customer churn. The model will allow SyriaTel to:  
1. Identify customers at risk of churning early.  
2. Design and implement targeted retention strategies, such as personalized offers or loyalty programs.  
3. Enhance customer satisfaction and loyalty.  
4. Minimize revenue losses caused by churn.  

#### **Key Business Questions.**  
1. What are the main factors influencing customer churn?  
2. How can these factors be leveraged to design effective retention strategies?  
3. How accurately can the model predict customer churn, enabling timely interventions?  

---

### **DATA UNDERSTANDING.**

#### **Dataset Overview.**  
The dataset, sourced from Kaggle, contains historical information on SyriaTel customers, covering demographics, usage patterns, account details, support interactions and churn status.

The dataset consists of 20 columns and 3333 rows. 
Key components include:

1. **Target Variable**:  
   - **Churn**: A binary variable indicating whether a customer has churned (1) or not (0).  

2. **Predictor Variables**:  
- **customer_demographics** = ['account length']
service_usage_metrics = ['total day minutes', 'total day calls', 'total day charge',
        'total eve minutes', 'total eve calls', 'total eve charge',
        'total night minutes', 'total night calls', 'total night charge',
        'total intl minutes', 'total intl calls', 'total intl charge']
- **account_information** = ['area code', 'phone number', 'international plan', 
        'voice mail plan', 'number vmail messages']
- **customer_support_interactions** = ['customer service calls']

#### **Initial Observations.**  
- **Class imbalance**: Fewer churn cases compared to non-churn cases, requiring techniques like class weighting or resampling during modeling.  
- **Mixed data types**: Numerical and categorical features require preprocessing for compatibility with machine learning models.  
- **No missing values detected**, but potential outliers exist in numerical features.  

#### **Key Questions for Analysis**  
- Are specific usage patterns (e.g., high international call charges) strongly correlated with churn?  
- How do categorical variables like the presence of an international plan or a voicemail plan influence churn?  
- What role do customer service interactions play in churn prediction?  


### **DATA PREPARATION.**

#### **Objective.**  
To ensure the dataset is clean, transformed, and ready for modeling by addressing quality issues and engineering relevant features to ensure compatibility with the chosen models and improve prediction accuracy.


1. **Data Cleaning**:  
   - Handle missing numerical values with imputation (none detected in this dataset).  
   - Fill missing categorical values (if present) with `'Unknown'`.  
   - Remove duplicate records to avoid bias.  

2. **Outlier Treatment**:  
   - Detect outliers using the Interquartile Range (IQR) and box plots.  
   - Apply capping or winsorization to handle extreme values.  

3. **Feature Transformation**:  
   - Standardize numerical features using a `StandardScaler` for models sensitive to scale.  
   - Encode categorical variables using binary encoding.  

4. **Feature Engineering**:  
   - Create new features like:  
     - **Total call duration**: Sum of day, evening, and night call durations.  
     - **Average call duration per day**: Total call duration divided by the number of days in the account length.  
     - **Customer service call frequency**: Number of calls normalized by account length.  

5. **Class Imbalance Handling**:  
   
   - Adjusting class weights or winsorization.  
     

6. **Data Splitting**:  
   - Split the dataset into training (75%) and test (25%) subsets for evaluation.  

---

### **MODELING.**

#### **Objective.**  
Develop and compare machine learning models to predict customer churn, starting with a base model and progressing to more advanced techniques.

1. **Model Selection**:  
   - **Baseline Model**: Logistic Regression for simplicity and interpretability.  
   - **Advanced Models**: Decision Tree and Random Forest to capture non-linear patterns and improve accuracy.  

2. **Model Training**:  
   - Train each model on the training dataset.  
   - Apply cross-validation to tune hyperparameters and avoid overfitting.  


3. **Evaluation Metrics**:  
   - **Primary Metric**: Accuracy to assess overall performance.  
   - **Complementary Metrics**: Precision, recall, F1-score, and ROC-AUC to provide a comprehensive evaluation, particularly for handling class imbalance.  

---

### **EVALUATION.**

#### **Objective.**  
To assess the model’s performance and ensure it meets business requirements.  

1. **Evaluate Test Set Performance**:  
   - Measure accuracy, precision, recall, F1-score, and ROC-AUC.  
   - Compare test performance with cross-validation results to check for overfitting or underfitting.  

2. **Feature Importance Analysis**:  
   - For Logistic Regression, analyze feature coefficients to interpret their impact.  
   - For Decision Tree and Random Forest, extract feature importance scores to identify key predictors.  

3. **Model Comparison**:  
   - Compare the performance of all models to identify the best-performing one.  
   - Random Forest is expected to outperform in terms of accuracy and AUC.  

4. **Business Impact Analysis**:  
   - Use model insights to identify at-risk customers for retention campaigns.  
   - Quantify potential cost savings from reduced churn rates.  

5. **Final Model Deployment**:  
   - Deploy the best-performing model (Random Forest) in a production environment.  
   - Monitor model performance over time and retrain as needed.  

