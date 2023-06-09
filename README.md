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
2. The top 15 variables when you take out opioids are: ['AMOXICILLIN', 'Specialty_Emergency Medicine', 'GABAPENTIN', 'PREDNISONE', 'LEVOTHYROXINE.SODIUM', 'MELOXICAM', 'OMEPRAZOLE', 'CIPROFLOXACIN.HCL', 'CEPHALEXIN', 'IBUPROFEN', 'Specialty_Orthopedic Surgery', 'METFORMIN.HCL', 'Specialty_General Surgery', 'LISINOPRIL', 'Specialty_Psychiatry']
    * Emergency Medicine stood out among other specialties, like Orthopedic Surgery, General Surgery, and Psychiatry, to be an important characteristic when it came to predicting frequent opioids prescribers. 

3. These are the important drug variables in descending order [(0, 'AMOXICILLIN'), (2, 'GABAPENTIN'), (3, 'PREDNISONE'), (4, 'LEVOTHYROXINE.SODIUM'), (5, 'MELOXICAM'), (6, 'OMEPRAZOLE'), (7, 'CIPROFLOXACIN.HCL'), (8, 'CEPHALEXIN'), (9, 'IBUPROFEN'), (11, 'METFORMIN.HCL')]
    * Subject matter expertise might be necessary to gain a deeper understanding of what these drugs might be used for and why they are considered important.

4. Imporant speciaties are:  [(1, 'Specialty_Emergency Medicine'), (10, 'Specialty_Orthopedic Surgery'), (12, 'Specialty_General Surgery'), (14, 'Specialty_Psychiatry'), (34, 'Specialty_Physician Assistant'), (38, 'Specialty_Optometry'), (46, 'Specialty_Oncology'), (47, 'Specialty_Dentist'), (69, 'Specialty_Internal Medicine'), (70, 'Specialty_Nurse')]
    * After Psychiatry (being number 15 most important), specialty falls off the radar.

5. Imporant speciaties are:  [(40, 'State_NY'), (45, 'State_FL'), (50, 'State_CA'), (61, 'State_TX'), (68, 'State_PA'), (77, 'State_MI'), (84, 'State_IL'), (87, 'State_OH'), (95, 'State_GA'), (100, 'State_NC')]
    * State and Gender did not appear to be that important when it came to predicting opioids prescribers.
    * Note that only Pennsylvania and Ohio were among the top 10 variables for states. Those two states were also among the highest overdose from opioids. New York, Florida, California were not on that list. Perhaps where the frequent prescribers are might not be important when it comes to opioids abuse. This might also be because the states listed above are among more populous states.
    * Top 10 states for having the most number of frequent opioids prescribers are identical to the list above, except some of the orderings.
6. Imporant genders are:  [(48, 'Gender_M'), (51, 'Gender_F')]

Best performing model out of Logistic Regression, SVM, KNN, RF, and XGBoost - TBD

## Conclusion

The recommendation for any governmental agency interested in investigating opioid prescribing patterns is to use k-nearest neighbor model paired with feature selection or dimensionality reduction.

The 5 opioids worth closer monitoring are oxycodone acetaminophen, hydrocodone acetaminophen, acetaminophen codeine, oxycodone hcl, and tramadol hcl, as those 5 opioids were not only considered important features by random forest, but also contributed significantly in improving model accuracy.

Interestingly, 6 antibiotics are featured heavily on the important features list, which are amoxicillin, ciprofloxacin hcl, cephalexin, azithromycin, clindamycin hcl, and levofloxacin. Among all the drugs in the dataset, amoxicillin was noteworthy, since it was considered the important by random forest. It is a penicillin antibiotic. It is used to treat bacterial infections, such as chest infections (including pneumonia) and dental abscesses. It can also be used together with other antibiotics and medicines to treat stomach ulcers. It would be very interesting to do a deeper dive into these drugs in terms of subject matter to gain a better understanding of who prescribes these drugs the most.

Specialties with high importance in our model, namely emergency medicine, general surgery, orthopedic surgery, and Psychiatry might benefit from further efforts in educating prescribers on the dangers of over-prescribing opioids, and perhaps closer monitoring of their prescribing pattern. It is also possible that individual drugs that are strong detectors may indicate specialties or sub-specialties of individual prescribers that could be of interest, or perhaps even reveal hidden avenues of illegitimate drug access.
