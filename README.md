# Module 18 Challenge
## classification-challenge


## Background




The purpose of this challenge was to create a model to predict student loan repayment.


## Installation




The following libraries and dependencies are required to successfully run the project:
- import pandas as pd
- import tensorflow as tf
- from tensorflow.keras.layers import Dense
- from tensorflow.keras.models import Sequential
- from sklearn.model_selection import train_test_split
- from sklearn.preprocessing import StandardScaler
- from sklearn.metrics import classification_report
- from pathlib import Path



## Repository Files and Starter Code
- [Module 18 Starter Code](https://static.bc-edx.com/ai/ail-v-1-0/m18/lms/starter/M18_Starter_Code.zip)
- student_loans_with_deep_learning.ipynb : completed workbook

## Methodology
The project was completed in three parts:
### 1. Prepared data for use on a neural network model
- Read the student-loans.csv file into the loans_df dataframe.
- Standardized features using scikit-learn's StandardScaler.
- Created the target (y) dataset, defined as the "credit_ranking" column.
- Created the features (X) dataset, defined as the remaining columns.
- Split the features and target sets into training and testing datasets, and assigned the function a random_state equal to 1.


### 2. Compiled and evaluate a model using neural network
- Created a deep neural network by assigning the number of input features (11), the number of layers (4 total [input, two hidden, output]), and the number of neurons/nodes on each layer using Tensorflow’s Keras.
- Compiled and fit the model using the binary_crossentropy loss function, the adam optimizer, and the accuracy evaluation metric.
- Evaluated the model using the test data to determine the model's loss and accuracy, which were approximately .5 and .75, respectively
- Saved and exported the model to a keras file (student_loans.keras).

### 3. Predicted loan repayment success using the neural network model
- Reloaded the student_loans.keras saved model.
- Made predictions on the testing data, saved the predictions to a DataFrame ("predictions_df"), and rounded the predictions to binary values.
- Generated a classification report with the predictions and testing data which confirmed the approximately 75% accuracy and demonstrated a pretty balanced performance.



## Evaluation and Discussion

**1. Describe the data that you would need to collect to build a recommendation system to recommend student loan options for students. Explain why this data would be relevant and appropriate.**
> Hopefully the model would have been more fine tuned before use to improve the loss numbers, and increase the accuracy. But for discussion purposes, in order to recommend student loan options to students, you would need a system that could recommend loans for which the students would likely qualify. Given the model we created was about 75% accurate in determining creditworthiness, at a minimum, we would want to collect information that was consistent with the features (X) used in the model: payment_history, location_parameter, stem_degree_score, gpa_ranking, alumni_success, study_major_code, time_to_completion,finance_workshop_score, cohort_ranking, total_loan_score financial_aid_score, and credit_ranking. Using this data, which includes demographic information, financial history, and education/institutional information, we could recommend loans that the student was likely to be approved for. It would also be possible to add additional information to collect about the student's loan preferences, i.e. terms and repayment penalties.  This would provide an opportunity to provide a more customized recommendation.

**2. Based on the data you chose to use in this recommendation system, would your model be using collaborative filtering, content-based filtering, or context-based filtering? Justify why the data you selected would be suitable for your choice of filtering method.**

>The system I would design for recommending student loan options is largely based on collaborative filtering, with a few content-based elements. The recommendation system would use insights gathered from user inputs to compare it with other similarly situated students. The content-based elements I suggested would be recommending particular loan products or structures based on similar loan features the student preferred - for example, perhaps the student was searching for "loans with no prepayment penalties." Returning recommendations for loans that the student would both qualify for and find appealing will be more likely to satisfy the user and convert the student to a loan customer. Since my recommendation model would not focus on sequential information, I would not be using context-based filtering (though I am sure it could be modified to do so).

**3. Describe two real-world challenges that you would take into consideration while building a recommendation system for student loans. Explain why these challenges would be of concern for a student loan recommendation system.**

> The data we would be using to create the recommendation system is challenging. In part, this is because of privacy concerns and fairness. For example, is it fair that someone's choice of major or class ranking has the potential to impact their opportunity to further their education? Or could these features have a disparate impact on protected classes or disproportionately benefit certain classes of students?

> A second consideration that also gives me pause would be the accuracy of the data. Students/users couldn't be trusted to input this data, but how would it be obtained? Would schools submit it, and if so, how could it be verified? Schools inherently have incentive to over-estimate the value of their degrees, so could they inflate their statistics (i.e. inflating alumni success, reducing time to completion, etc) and induce the lender to extend loan options that it would not have otherwise?

> Another consideration, that is less about the data, would be the more recent trend to encourage individuals to look at different options after high school: for example, rather than traditional four year colleges and universities, perhaps the recommendation model could be expanded to account for students looking to pursue trade schools. These students could present an opportunity for lenders that would otherwise be overlooked.



## Resources Consulted
For this challenge, I consulted
- [Module 18 Starter Code](https://static.bc-edx.com/ai/ail-v-1-0/m18/lms/starter/M18_Starter_Code.zip) and my in-class slides, notes, and activities.
- [Original .CSV File](https://static.bc-edx.com/ai/ail-v-1-0/m18/lms/datasets/student-loans.csv)
- I also found this article, [What is a Recommendation System?](https://www.nvidia.com/en-us/glossary/recommendation-system/) to be helpful to further review collaborative, content, and context filtering algorithms.
