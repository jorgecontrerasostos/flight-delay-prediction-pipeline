# Flight Delay Prediction Pipeline Using PySpark

## **Overview**
This project aims to predict whether a flight will be delayed upon arrival using the PySpark framework. By leveraging a structured data pipeline, various feature transformations and machine learning techniques are applied to build a predictive model. Some data exploration was made with SQL queries to showcase how these can be used as well when some PySpark queries may get a bit tricky. However, it depends on our use case to decide which approach to use.

## **Project Workflow**

1. **Data Cleaning**  
   The dataset contains flight information, including departure/arrival times, delays, and other features. Missing or invalid values (`NA`) are removed to ensure data quality.  

2. **Feature Engineering**  
   - **String Indexing:** Categorical columns like `month` and `carrier` are converted into numerical indices using the `StringIndexer`.  
   - **Vector Assembling:** Selected features such as `day`, `dep_time`, `arr_time`, `distance`, and indexed columns (`month_indexed`, `carrier_indexed`) are combined into a single feature vector using the `VectorAssembler`.  
   - **Binarization:** The `arr_delay` column is binarized into `arr_delay_binary` to represent delayed flights (`1`) and non-delayed flights (`0`), with a threshold of 15 minutes.

3. **Model Training**  
   - A **Decision Tree Classifier** is used to predict whether a flight will be delayed (`arr_delay_binary`).  
   - The training dataset consists of features (`features`) and the binary target variable (`arr_delay_binary`).  

4. **Pipeline Creation**  
   To streamline the process, a PySpark **Pipeline** is created with the following stages:  
   - String Indexers (`indexer_month` and `indexer_carrier`)  
   - Vector Assembler (`assembler`)  
   - Binarizer  
   - Decision Tree Classifier  

5. **Evaluation**  
   The model's performance is evaluated using metrics like accuracy, precision, recall, and the F1 score. A confusion matrix is used to understand the distribution of true/false positives and negatives.

## **Key Steps**

- **Input Data Columns:**  
  The input data includes features like `month`, `day`, `dep_time`, `arr_time`, `carrier`, `distance`, `air_time`, and `arr_delay`.  

- **Pipeline Stages:**  
  The pipeline includes transformations and the classifier to simplify the modeling process.  

- **Evaluation Metrics:**  
  Metrics are computed to assess model performance. Recommendations for improvement include addressing class imbalance, hyperparameter tuning, and feature enrichment.

## **Conclusion**
This project showcases a structured approach to building a flight delay prediction model using PySpark, emphasizing data preprocessing, pipeline creation, and evaluation. The results highlight areas of improvement, such as recall enhancement and better handling of class imbalance.
