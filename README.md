# Study of Prescription Patterns among Physicians in the US to Combat the Opioids Overdose Epidemic

## Motivation
Opioid-related overdoses/deaths have increased exponentially in the United States (US) for their misuse other than for pain relief. As shown in Figure 1, the US has experienced three distinct waves of opioid overdose-related deaths since 1999. 
- The first wave starting in 1999 was attributed to a rise in prescription- related opioid overdoses/deaths. 
- The second wave starting in 2010 was attributed to a rise in heroin-related opioid overdoses/deaths. 
- The third wave starting in 2013 was attributed to the rise in synthetic opioid-related overdoses/deaths. The overdoses/deaths caused from commonly prescribed opioids remain consistently elevated along with overdoses/deaths from heroin.

<p align="center">
  <img src="https://www.cdc.gov/drugoverdose/images/3Wave_OverdoesDeathRates_LineGraph_2020-large.png" width="700" height="400" alt="my alt text"/>
</p>

<h5 align="center">Figure 1 Source: CDC: https://www.cdc.gov/opioids/basics/epidemic.html</h5>

Understanding the prescriber characteristics and practices leading to prescription of various drugs may be instrumental in forming a systematic strategy to prevent opioid-related overdoses/deaths. This project aims to study the opioids prescribing patterns among physicians across the US using a [U.S. Opiate Prescriptions Kaggle dataset from 2014](https://www.kaggle.com/datasets/apryor6/us-opiate-prescriptions). The primary research question is predicting frequent opioid prescribers based on a combination of physician characteristics and their prescribing patterns. This can highlight which medical treatments have the highest likelihood of being prescribed opioids and may put patients at risk of developing addiction to opioids.

The main goals of the project are:
1. To find important features of medical practitioners who prescribe opioids. This will be a challenge due to the number of drugs and medical specialties included in the prescribing data.
2. Develop a classifier to predict if a given medical practitioner frequently prescribes opioids (defined as more than 10 times a year).

For Exploratory Data Analysis, click on this file: [EDA prescribers by state and specialty.ipynb](https://github.com/djeong95/Opioids-Prescription-Pattern-Analysis/blob/main/EDA%20prescribers%20by%20state%20and%20specialty.ipynb)

For Modeling, click on this file:

## Discussions from EDA

Notable findings:
1. Family Medicine, Internal Medicine, Nurse, Physician Assistant, Dentist, Emergency Medicine, Orthopedia Surgery, General Surgery, Oncology, Neurology were top 10 speciaties in terms of having the most number of frequent opioids prescribers.

2. California, New York, Florida, Texas, Pennsylvania, Illinois, Ohio, Michigan, North Carolina, and Massachusetts were top 10 states in terms of having the most number of frequent opioids prescribers.

3. West Virginia, New Mexico, New Hampshire, Kentucky, Ohio, Rhode Island, Pennsylvania, Utah, Delaware, and Oklahoma were top 10 states in terms of having the most overdose deaths from opioids.

4. ['HYDROCODONE.ACETAMINOPHEN', 'LISINOPRIL', 'OMEPRAZOLE', 'AMLODIPINE.BESYLATE', 'GABAPENTIN', 'ATORVASTATIN.CALCIUM', 'FUROSEMIDE', 'LEVOTHYROXINE.SODIUM', 'SIMVASTATIN', 'METOPROLOL.TARTRATE', 'HYDROCHLOROTHIAZIDE'] are among the most prescribed drugs out of the 250 drugs in the dataset. Only 1 is an opioid - HYDROCODONE.ACETAMINOPHEN.

## Discussions from Modeling

Notable findings:
1. These are the important drugs in descending order [(0, 'HYDROCODONE.ACETAMINOPHEN'), (1, 'OXYCODONE.ACETAMINOPHEN'), (2, 'TRAMADOL.HCL'), (3, 'OXYCODONE.HCL'), (4, 'ACETAMINOPHEN.CODEINE')]. 
    * Random Forest's Variable Importance revealed that all of the opioids in the dataset (which are the listed 5) are top 5 most important variables.
      
2. The top 15 variables when you take out opioids are: ['GABAPENTIN', 'LEVOTHYROXINE.SODIUM', 'AMOXICILLIN', 'Specialty_Emergency Medicine', 'MELOXICAM', 'PREDNISONE', 'METFORMIN.HCL', 'OMEPRAZOLE', 'CIPROFLOXACIN.HCL', 'Specialty_Orthopedic Surgery', 'Specialty_Psychiatry', 'CEPHALEXIN', 'Specialty_General Surgery', 'IBUPROFEN', 'TAMSULOSIN.HCL']
    * Emergency Medicine stood out among other specialties, like Orthopedic Surgery, General Surgery, and Psychiatry, to be an important characteristic when it came to predicting frequent opioids prescribers. 

3. These are the important drug variables in descending order [(0, 'AMOXICILLIN'), (2, 'GABAPENTIN'), (3, 'PREDNISONE'), (4, 'LEVOTHYROXINE.SODIUM'), (5, 'MELOXICAM'), (6, 'OMEPRAZOLE'), (7, 'CIPROFLOXACIN.HCL'), (8, 'CEPHALEXIN'), (9, 'IBUPROFEN'), (11, 'METFORMIN.HCL')]
    * Subject matter expertise might be necessary to gain a deeper understanding of what these drugs might be used for and why they are considered important.

4. Imporant speciaties are:  [(3, 'Specialty_Emergency Medicine'), (9, 'Specialty_Orthopedic Surgery'), (10, 'Specialty_Psychiatry'), (12, 'Specialty_General Surgery'), (25, 'Specialty_Physician Assistant'), (29, 'Specialty_Oncology'), (35, 'Specialty_Optometry'), (46, 'Specialty_Dentist'), (51, 'Specialty_Oral Surgery'), (58, 'Specialty_Nurse')]
    * After General Surgury (being number 12 most important), specialty falls off the radar.

5. Imporant states are:  [(33, 'State_NY'), (34, 'State_FL'), (40, 'State_CA'), (50, 'State_TX'), (52, 'State_PA'), (59, 'State_MI'), (61, 'State_IL'), (67, 'State_OH'), (71, 'State_GA'), (79, 'State_NC')]
    * State and Gender did not appear to be that important when it came to predicting opioids prescribers.
    * Note that only Pennsylvania and Ohio were among the top 10 variables for states. Those two states were also among the highest overdose from opioids. New York, Florida, California were not on that list. Perhaps where the frequent prescribers are might not be important when it comes to opioids abuse. This might also be because the states listed above are among more populous states.
    * Top 10 states for having the most number of frequent opioids prescribers are identical to the list above, except some of the orderings.
6. Imporant genders are:  [(44, 'Gender_M'), (45, 'Gender_F')]

Best performing model out of Logistic Regression, SVM, KNN, RF, and XGBoost

| Model                                   | Accuracy | Precision | Recall | F1 Score | AUC   |
|-----------------------------------------|----------|-----------|--------|----------|-------|
| Feature-selected Logistic Regression    | 0.867   | 0.847     | 0.784  | 0.814    | 0.794 |
| PCA Logistic Regression                 | 0.809   | 0.842     | 0.817  | 0.829    | 0.802 |
| Feature-selected Support Vector Machine | 0.792   | 0.838     | 0.806  | 0.822    | 0.795 |
| PCA Support Vector Machine              | 0.730   | 0.729     | 0.860  | 0.789    | 0.709 |
| Feature-selected K-Nearest Neighbors    | 0.871   | 0.839     | 0.779  | 0.808    | 0.786 |
| PCA K-Nearest Neighbors                 | 0.85    | 0.819     | 0.777  | 0.798    | 0.77  |
| Feature-selected Random Forest          | 0.791   | 0.809     | 0.839  | 0.824    | 0.782 |
| PCA Random Forest                       | 0.815   | 0.826     | 0.864  | 0.845    | 0.806 |
| Feature-selected XGBoost                | 0.834   | 0.869     | 0.840  | 0.854    | 0.832 |
| PCA XGBoost                             | 0.827   | 0.848     | 0.855  | 0.852    | 0.821 |


## Conclusion

The recommendation for any governmental agency interested in investigating opioid prescribing patterns is to use k-nearest neighbor model paired with feature selection or dimensionality reduction because the model training time was a fraction for that model compared to those of other models. However, for model performance, feature-selected Logistic Regression, PCA Random Forest, or Feature-selected XGBoost are recommended. XGBoost took about 7 hours to compute on average.

The 5 opioids worth closer monitoring are oxycodone acetaminophen, hydrocodone acetaminophen, acetaminophen codeine, oxycodone hcl, and tramadol hcl, as those 5 opioids were not only considered important features by random forest, but also contributed significantly in improving model accuracy.

Interestingly, 6 antibiotics are featured heavily on the important features list, which are amoxicillin, ciprofloxacin hcl, cephalexin, azithromycin, clindamycin hcl, and levofloxacin. Among all the drugs in the dataset, amoxicillin was noteworthy, since it was considered the important by random forest. It is a penicillin antibiotic. It is used to treat bacterial infections, such as chest infections (including pneumonia) and dental abscesses. It can also be used together with other antibiotics and medicines to treat stomach ulcers. It would be very interesting to do a deeper dive into these drugs in terms of subject matter to gain a better understanding of who prescribes these drugs the most.

Specialties with high importance in our model, namely emergency medicine, general surgery, orthopedic surgery, and Psychiatry might benefit from further efforts in educating prescribers on the dangers of over-prescribing opioids, and perhaps closer monitoring of their prescribing pattern. It is also possible that individual drugs that are strong detectors may indicate specialties or sub-specialties of individual prescribers that could be of interest, or perhaps even reveal hidden avenues of illegitimate drug access.
