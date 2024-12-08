# terry_stop_project
<h3>Background information</h3>

A Terry Stop, also known as an "Investigative Detention" or "Stop and Frisk," allows law enforcement officers to temporarily detain a person for investigation when they reasonably suspect involvement in criminal activity. This stop is used when there is insufficient evidence for an arrest (i.e., no probable cause) but enough suspicion to justify a brief investigation. The primary purpose is to confirm or dispel the officer's suspicions. If probable cause for an arrest arises during the stop, the suspect is arrested. If no probable cause is found, the suspect is released.

<h3>Problem statement</h3>

Terry stops can disrupt the normal lives of individuals, especially when no arrests are made. During these stops, police officers may spend valuable time that could be used to address crime in other areas. Additionally, Terry stops initiated through 911 calls can lead to a waste of resources, particularly when they result in no arrests. These stops have also been plagued by concerns of racial profiling, with many individuals believing that the stops are disproportionately based on their race or gender. This has eroded the public’s perception of law enforcement and diminished their confidence in the police.A model was proposed to be developed to predict whether a Terry stop will result in an arrest. Given that Terry stops can be initiated through various channels such as 911 calls, messages, alarms, and police interactions, this model can help schedule calls appropriately and allocate resources more efficiently.

<h3>Objective</h3>

To build and determine the best classifier model for predicting Terry stop arrests with an accuracy above 75% and an F1 score above 80%

<h3>Data Understanding</h3>h3

The data for this analysis was obtained from the Seattle police department. It represents  Each row represents a unique stop. Each record contains the perceived demographics of the subject, as reported by the officer making the stop, and officer demographics as reported to the Seattle Police Department. The original dataset contained 62020 entries. the officer squad had missing values which were dropped resulting in 61459 entries with 23 columns. Due to the sensitivity and data ethics consideration, gender and race columns were not used in the analysis. the data can be obtained from:http://tiny.cc/l4hzzz  and the  columns description:http://tiny.cc/c5hzzz.

<h3>Data Preparation</h3>

The following were applied to prepare the data for analysis:

Handling of missing values- only the officer squad had missing values at 9%  which were dropped.

The reported date and time were converted to DateTime format. The date was then extracted into components: day of the week, day, month, and year. The original "reported date" and "reported day" columns were dropped to avoid multicollinearity. Only the hour component was retained, and the "time reported" column was dropped.

Column Preparation: The "Weapon Type" column was grouped into three categories: "Weapon Found," "Weapon Unknown," and "No Weapon." This was done to simplify the analysis. The same approach was applied to other columns as appropriate.

N/B Not all columns were converted to integers for visualization purposes. The column values were later converted to integers for modeling.

    4. Irrelevant columns dropped. Columns containing sensitive information, such as gender, race, and personal identifiers like Officer ID, were dropped. Gender and race were excluded from the analysis to ensure the model remains unbiased and does not inadvertently reinforce stereotypes or discriminatory practices. The goal was to build a fair and objective model that focuses solely on relevant factors, avoiding any potential influence of sensitive attributes.

The resulting data frame contained 61459 rows and 16 columns. The data frame still contained object datatype and while
some columns were transformed.

<h3>modelling and evaluation</h3>

<h3>Building a Logistic regression model</h3>

![image](https://github.com/user-attachments/assets/f12de9da-bc9c-4dc1-b2cd-25252f67563a)

                precision   recall  f1-score   support

           0       0.97      0.71      0.82     13637
           
           1       0.26      0.83      0.40      1728

    accuracy                           0.72     15365
    
   macro avg       0.62      0.77      0.61     15365
   
weighted avg       0.89      0.72      0.77     15365

The model achieves an accuracy of  72%. The model performs poorly in predicting the minority class and a macro average f1 score of 61%. A decision tree classifier model is recommended to improve the prediction.

<h3>Building  a decision tree model(no hyperparameter tuning)</h3>

                 precision    recall  f1-score   support

           0       0.94      0.93      0.94     13637
           
           1       0.50      0.54      0.52      1728
           

    accuracy                           0.89     15365
    
   macro avg       0.72      0.73      0.73     15365
   
weighted avg       0.89      0.89      0.89     15365

![image](https://github.com/user-attachments/assets/b17103b5-719b-40d4-9681-e84b233b6701)

The Area Under the Curve (AUC) value is 0.74, indicating that the model has moderate performance

<h3>Hypertuning the parameters to solve the problem of overfitting</h3>

![image](https://github.com/user-attachments/assets/80614ea7-0323-4797-89ed-1655362ae383)


   precision    recall  f1-score   support

           0       0.95      0.92      0.93     13637
           
           1       0.49      0.61      0.54      1728

    accuracy                           0.88     15365
    
   macro avg       0.72      0.77      0.74     15365
   
weighted avg       0.90      0.88      0.89     15365

![image](https://github.com/user-attachments/assets/e941dc91-c6b6-481f-8f18-526cbdf8cb38)

Hyper tuning slightly improved the f1 score thus prioritizing the minority class.The accuracy however decreased slightly from 89 to 88 precision has slightly improved from 89 to 90%

The model demonstrates moderate performance and can be improved further.A random forest classifier can improve the performance of the model.

<h3>Building a random forest classifier</h3>

![image](https://github.com/user-attachments/assets/72b885e8-0897-422c-ad62-c6ab96224d7b)


              precision    recall  f1-score   support

           0       0.96      0.91      0.94     13637
           
           1       0.50      0.71      0.59      1728

    accuracy                           0.89     15365
    
   macro avg       0.73      0.81      0.76     15365

   
weighted avg       0.91      0.89      0.90     15365

![image](https://github.com/user-attachments/assets/5c4d2ae7-2dc5-428f-9bfb-815d26a6fba6)

The curve is close to the top-left corner, showing a high TPR and a low FPR, which signifies a good balance.AUC of 0.93 indicates a strong predictive power of the model.

<h3>Conclusion</h3>

The random forest model performs the best in terms of f1 score .It has the AUC score at 93% indicating a strong predictive power of the model.The objective of the analysis was achieved ie the random forest predicted the arrest flag at an accuracy of 89% and an f1 score above 75%.


<h3>Recommendation</h3>

Despite achieving the desired accuracy,the best model ie random forest classifier performed poorly in terms of the f1 score.For predicting if a terry stop would lead to an arrest or not the f1 score is the best metric to be considered.XGboost model can be modeled and performance evaluated.









