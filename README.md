Customer Churn Prediction
    This project analyzes a dataset of bank customers to predict whether a customer will churn (i.e., close their account). The goal is to build a classification model that can identify customers at risk of          churning, allowing the bank to take proactive measures.

📊 Data
   The dataset used for this project is churn_prediction.csv. It contains various customer attributes, including:

        customer_id: Unique identifier for each customer.

        vintage: The duration of the customer's relationship with the bank.

        age: The customer's age.

        gender: The customer's gender.
        
        dependents: Number of dependents the customer has.
        
        occupation: The customer's occupation.
        
        city: The customer's city.
        
        customer_nw_category: Customer's net worth category.
        
        branch_code: The code of the bank branch.
        
        current_balance: The customer's current account balance.
        
        last_transaction: The date of the last transaction.
        
        churn: The target variable (1 if the customer churned, 0 otherwise).

⚙️ Methodology
     The project follows these key steps:

     Data Loading & Exploration: The dataset is loaded using pandas, and an initial exploration is performed to understand its structure and identify missing values.
     
     Data Cleaning:
     
          Missing values in numerical columns (doy_ls_tran, woy_ls_tran, etc.) are filled using the median.
          
          Missing values in categorical columns (gender, occupation) are filled using the most frequent value.
          
          Columns like dependents, city, and customer_id were dropped as part of the data preparation process.
     
     Feature Engineering:
     
          The last_transaction column, which is a date, is used to create several new time-based features:
          
          doy_ls_tran: Day of the year of the last transaction.
          
          woy_ls_tran: Week of the year of the last transaction.
          
          moy_ls_tran: Month of the year of the last transaction.
          
          dow_ls_tran: Day of the week of the last transaction.
          
          The original last_transaction column is then dropped.
     
     Data Preprocessing:
     
          Categorical variables are converted into numerical format using one-hot encoding (pd.get_dummies).
          
          All features are scaled to a range between 0 and 1 using MinMaxScaler to ensure that no single feature dominates the model.

🤖 Modeling
     Model Selection: A Logistic Regression model was chosen for this classification task. The class_weight='balanced' parameter was used to handle the imbalance in the churn classes.
     
     Train-Test Split: The data was split into training (70%) and testing (30%) sets to evaluate the model's performance on unseen data.

📈 Results
     The Logistic Regression model achieved the following performance on the test set:
     
          Accuracy: 77.0%
          
          Recall: 61.0%
          
          Precision: 41.0%
          
          F1-Score: 49.1%
          
          Confusion Matrix:
          
          [[5609, 1358],
           [ 603,  945]]

These results indicate that the model has a reasonable ability to identify customers who are likely to churn, although there is room for improvement, particularly in precision.

🚀 How to Use
    To replicate this analysis:

    Ensure you have Python and the following libraries installed:
    
         pandas
         
         numpy
         
         matplotlib
         
         seaborn
         
         scikit-learn
    
    Place the churn_prediction.csv file in the same directory as your script or notebook.
