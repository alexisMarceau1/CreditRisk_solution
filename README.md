# 📊 **CreditRisk: A Credit Scoring Model for Predicting Loan Defaults**

![Dashboard Preview](demo/dash.png)

## 🏢 **Project Overview**

CreditRisk is a machine learning project designed to predict the likelihood of loan defaults for individuals with limited or no credit history. This project aims to build a robust credit scoring model and provide transparent insights into the predictions using an interactive dashboard.

### **Key Objectives**
- **Reduce financial losses**: Identify high-risk clients likely to default on their loans.
- **Maximize profits**: Minimize rejecting good clients who can repay their loans.
- **Ensure transparency**: Explain credit decisions clearly to stakeholders through a dashboard.

---

## 📚 **Dataset Description**
The data and their descriptions are available on the Kaggle competition website: Home Credit Default Risk.
The dataset contains over **300,000 loan applications** with 122 features before feature engineering. The target variable (`TARGET`) indicates:
- `0`: Loan was repaid.
- `1`: Loan was not repaid.

### **Key Characteristics**
- **Data Sources**: Main training dataset, test dataset, and auxiliary datasets for feature enrichment.
- **Imbalance**: ~92% of loans were repaid, and only ~8% defaulted.

---

## 🔍 **Exploratory Data Analysis**

- The dataset exhibits significant class imbalance.
- External score variables (`EXT_SOURCE`) are negatively correlated with the target, indicating higher scores suggest better repayment likelihood.
- Age (`DAYS_BIRTH`) and external scores show correlations, suggesting younger applicants are at higher risk of default.

---

## ⚙️ **Methodology**

### **1. Feature Engineering**
- **Created Features**: Loan-to-income ratios, summary statistics from related datasets (e.g., approved/rejected credit history).
- **Techniques**:
  - One-hot encoding for categorical variables.
  - Grouping and aggregation (min, max, mean, sum, variance) across related datasets.
- **Outcome**: Increased the number of features to 798.

### **2. Data Preprocessing**
- **Sampling**: Selected a sample of 100,000 clients to reduce computational load.
- **Imputation**: Filled missing values using the median strategy.
- **Normalization**: Applied MinMaxScaler to scale features to a 0–1 range.

### **3. Model Training and Evaluation**
- Models tested:
  - **Baseline**: DummyClassifier.
  - **Logistic Regression**.
  - **Random Forest**.
  - **LightGBM (LGBM)**: Selected as the best-performing model.
- **Cross-Validation**: 5-fold cross-validation with hyperparameter optimization using GridSearchCV.
- **Metric**: AUC (Area Under the ROC Curve) to evaluate model performance.

### **4. Addressing Class Imbalance**
- **Techniques**:
  - Undersampling (RandomUnderSampler).
  - Oversampling (SMOTE).
  - Class weighting (`class_weight='balanced'`).

### **5. Custom Cost Function**
- Created a custom cost function prioritizing the reduction of **False Negatives (FN)** over **False Positives (FP)**.
- Hyperparameter tuning with Bayesian optimization (HyperOpt) using the custom cost function.

---

## 🏆 **Results**

### **Best Model**: LightGBM with Balanced Class Weight
- **AUC**: Highest among all tested models.
- **Training Time**: Reasonable for deployment.

### **Optimization Impact**
- Reduced **False Negatives (FN)** from 563 to 545, addressing the most costly prediction errors for the business.

### **Interpretable Results**
- **Global Feature Importance**:
  - Key drivers include `EXT_SOURCE_3`, `EXT_SOURCE_2`, and `DAYS_BIRTH`.
- **Local Interpretations**:
  - Used SHAP to provide detailed explanations for individual predictions.

---

## 💻 **Interactive Dashboard Demo**

The project includes an interactive dashboard that was previously hosted on Heroku. Due to Heroku’s recent policy change ending free hosting services, the dashboard is no longer live. However, detailed instructions for setting up and running the dashboard locally are provided here. 


https://github.com/user-attachments/assets/c12f66ef-31ed-4008-a8f6-466a66160254



https://github.com/user-attachments/assets/1faf7368-595f-48f4-a074-173a5db44d5c



### **Features**:
- Visualize the credit score and its interpretation for each client.
- Compare individual client data against the overall dataset or a group of similar clients.
- Provide transparency and explainability for non-expert stakeholders.

---

## 📈 **Business Impact**

CreditRisk provides significant value for financial institutions by:
1. **Reducing Operational Risk**: Identifying high-risk clients effectively minimizes default rates.
2. **Maximizing Revenue**: By approving good clients, the bank can increase profits.
3. **Enhancing Transparency**: The dashboard allows for clear communication of credit decisions, improving customer trust.

---

## 🚀 **Future Improvements**

1. **Refine Cost Function**:
   - Collaborate with domain experts to adjust the weights for False Positives and False Negatives.
2. **Threshold Optimization**:
   - Analyze business trade-offs to select the most profitable decision threshold.
3. **Advanced Feature Engineering**:
   - Incorporate additional external datasets or temporal features.
4. **Enhanced Dashboard**:
   - Add comparative analysis and deeper insights for credit officers.

---

## 📁 **Project Structure**

The project is divided into two main repositories:

- **Back-End Repository**: [CreditRisk Back-End](https://github.com/alexisMarceau1/CreditRisk_backend)
  Includes all necessary files and instructions to preprocess the data, train the model, and deploy the API.

- **Front-End Repository**: [CreditRisk Front-End](https://github.com/alexisMarceau1/CreditRisk_frontend) 
  Contains the code and setup instructions for running the interactive dashboard locally.

Both repositories include comprehensive documentation to help set up and execute the project locally.

---

## 📫 **Contact**

If you have any questions or want to discuss the project further, feel free to reach out:

**Alexis Marceau**  
📧 [alexis.marceau.12@gmail.com](mailto:alexis.marceau.12@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/alexis-marceau)  

---

