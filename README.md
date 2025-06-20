# PaySim Fraud Detection Analysis

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/atm.jpg?raw=true" width="100%"> 
</div>

> 🔗

---

### Table of Contents <a name="toc"></a>

[1. Background](#background)  <br>
[2. Objective](#objective)<br>
[3. Insights Deep-Dive](#insights-deep-dive) <br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.1. Class Imbalance](#class-imbalance)  <br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.2. Transaction Types by Fraud](#types-fraud)  <br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.3. Amounts in Fraudulent Transactions](#fraud-transactions)  <br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.4. Fraud Overtime](#Fraud-Overtime)  <br>
[4. Modeling & Results](#modeling_results)  <br>
[5. Key Takeaways](#key-takeaways)  <br>
[6. Tools & Libraries](#tools-libraries)  <br>
---

## 1. Background <a name="background"></a>

<p align="justify">
The PaySim dataset contains over 6 million transactions with various features such as transaction type, amount, sender an   d receiver, and fraud labels. The goal is to detect fraudulent transactions using classification modeling and draw insights from exploratory data analysis. The goal is to detect fraudulent transactions using classification modeling and draw insights from exploratory data analysis </p>
</p>

---

## 2. Objective <a name="objective"></a>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/paysim_table.png?raw=true" width="60%">
</div> <br>

<p align="justify">
The objective of this project is to explore patterns behind fraudulent transactions and build a machine learning model that can detect fraud effectively. Using exploratory data analysis, feature engineering, and a Random Forest classifier, the project focuses on achieving accurate results while also addressing the challenge of class imbalance to ensure fair performance across both fraudulent and legitimate cases.
</p>

---
## 3. Insights Deep-Dive <a name="insights-deep-dive"></a>
<a href="#toc">[ back to contents ]</a>

### 3.1. Class Imbalance <a name="class-imbalance"></a>  <a href="#toc">[↑]</a>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/class_imbalance.png?raw=true" width="50%">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/isfraud.png?raw=true" width="50%">
</div> <br>

- <p align="justify"> The Legitimate Transactions is around 99.87%, while the Fraudulent Transactions is around 0.12% which shows Class Imbalance - An issue for training a classification machine learning model since there's not enough data to train a model </p>

---
### 3.2. Transaction Types by Fraud <a name="types-fraud"></a>  <a href="#toc">[↑]</a>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/transaction%20type%20by%20fraud%20status.png?raw=true" width="60%">
</div> <br>

- <p align="justify">Fraudulent activity is mostly observed in TRANSFER and CASH_OUT transactions, in contrast the other types are rarely exhibits fraud</p>

---
### 3.3. Amounts in Fraudulent Transactions"><a name="fraud-transactions"</a>  <a href="#toc">[↑]</a>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/transaction%20amount%20by%20fraud%20status.png?raw=true" width="60%">
</div> <br>

- <p align="justify"> The graph shows that Fraudulent Transactions tends to involve higher amounts. Legitimate Transactions have a wider range but generally lower in average</p>

---
### 3.4. Fraud Overtime <a name="Fraud-Overtime"></a><a href="#toc">[↑]</a>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/fraud%20overtime.png?raw=true" width="60%">
</div> <br>

- <p align="justify"> Fraud peaks during specific steps, implying potential time-based fraud strategies. It could help in setting time-sensitive alerts in production environments.</p>
  
---
## 4. Modeling & Results <a name="modeling_results"></a>
### Preprocessing Steps

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/removed%20columns.png?raw=true" width="85%">
</div>

- <p align="justify">Removed nameOrig, nameDest, and isFlaggedFraud. Transfer the 'isFraud' column for our Y variable, then drop it for our X variable </p>
- <p align="justify">One-hot encoded the "type" column - converting into numerical values that a machine learning can understand.</p>

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/standardscaler.png?raw=true" width="85%">
</div>



- <p align="justify">Scales Features using StandardScaler</p>


<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/standardscaler.png?raw=true" width="85%">
</div>

- <p align="justify">Split dataset (70% training, 30% testing) using stratification to preserve fraud ratio.
</p>


<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/random%20forests%20classifier.png?raw=true" width="85%">
</div>

- <p align="justify">The Machine Learning Model used is RandomForestsClassifier with a class_weights="balanced" to address the class imbalance of the dataset </p>


### Confusion Matrix and classification report

<div align="center">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/confusion%20matrix.png?raw=true" width="50%">
  <img src="https://github.com/RielRoque/paysim-atm-fraud-detection-python/blob/main/classification%20report.png?raw=true" width="50%">
</div> <br>

- <p align="justify">The Accuracy Score of our RandomForestsClassifier Model is 0.99, but Accuracy Score alone is sometimes misleading - so having the right balance between the Precision and Recall is the ideal as it shows positive signs in the trained model.
</p>

## 5. Key Takeaways <a name="key-takeaways"></a>

- <p align="justify">Fraud detection is a high-stakes imbalanced classification problem.

</p>

- <p align="justify">Data shows fraud is more frequent in TRANSFER and CASH_OUT types.

</p>

- <p align="justify">Random Forest performs well with proper balancing and feature scaling..

</p>

- <p align="justify">The high precision and recall of the model shows a significant improvement of our model . 

</p>

---

### Tools & Technologies Used <a name="tools-libraries"></a> 

- Pandas and Numpy (Data Manipulation
- Matplotlib and Seaborn (Visualization)
- Scikit-learn (Machine Learning)

---

**An Analysis of PaySim Fraud Detection by Using a Machine Learning Model by Riel Roque** 🚀
