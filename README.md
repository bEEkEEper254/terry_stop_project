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



