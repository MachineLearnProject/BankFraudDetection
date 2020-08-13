# BankFraudDetection
Analysis
In the Banking Fraud Analysis Project, the goal was to find a model that would reasonably fit the data that we had. As our group was looking to do a financial-based machine learning project, we found issues getting actual financial transaction data. To work around this we were able to access a Kaggle dataset (https://www.kaggle.com/ntnu-testimon/paysim1) that was based on actual transactions. This dataset comprises of in excess of 6 million data points of which just over 8 thousand are fraudulent.

Our group found this challenge interesting as we could leverage machine learning see if we could catch fraudlent activities based on signatures of previous fraud. To tackle this problem we decided to work with the Scikit-Learn library and more specifically the Logistic Regression, Naive-Bayes, SVM and KNN models to see which would best match the data. We initially tried taking values as-is from the dataset to run our analysis but found out that in many cases the dollar amount whether small or very large, on it's own had very little effect on whether the transaction would be fraudulent or not. As this was the case we took a step back and categorized the data as a series of 1's or 0's based on factors that we repeatedly saw within the dataset.

The categories we did use were the type of transaction, whether it was a merchant or customer transaction, whether the transaction resulted in a zero balance or if it was a large transaction in excess of $200,000. Additionally, we quickly realized that we had very low frauds compared to overall transactions which is a realistic scenario in the real world. To overcome this we used a SMOTE (Synthetic Minority Oversampling Technique) function which generates additional data points for the quantity that is under represented.

For this model we found that the SVM model and KNN models took more than a day and we were still not able to get a response as such we discontinued reviewing these models. We did find that we were able to successfully run the Logistic Regression and Naive-Bayes models and that they gave us reasonably good metrics.

| Model	              | Type  	 | Accuracy	| Precision	| Recall	| F1     |
| ------------------- | -------- | -------- | --------- | ------  | ------ |
| Logistic Regression	| Training | 80.36%  	| 71.81%	  | 99.98%	| 83.58% |
|                     | Testing	 | 80.35% 	| 71.79%	  | 99.97%	| 83.57% |
| Naive-Bayes	        | Training | 77.83% 	| 69.80%	  | 98.07%	| 81.56% |
|                     | Testing	 | 77.87% 	| 69.87%	  | 98.06%	| 81.60% |

Accuracy Score: TP+TN/TP+FP+FN+TN

Precision Score: TP/TP+FP

Recall Score: TP/TP+FN

F1 Score: F1 Score = 2*(Recall * Precision) / (Recall + Precision)


The metrics presented above are for both training and testing. As can be seen the values for both the training and testing values are similar. The accuracy is the true positives divided by the total of our sample size. The precision is the true positives divided by the true positives plus the true negatives, in this case looking at how many false positives slipped through the cracks. Recall, which in this exercise is one of the most critical elements is the true positives divided by the true positives plus the false negatives. Recall is the most critical as making sure we get as many frauds is critical The F1 score is a weighted average of recall and precision which is a good balance capturing false positives and false negatives.

Based on our analysis it appears that the Logistic Regression and Naive-Bayes have very similar values with Logistic Regression being better of the two.
