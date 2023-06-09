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
6. Imporant genders are:  [(48, 'Gender_M'), (51, 'Gender_F')]


## Conclusion

For full report, click here: https://docs.google.com/document/d/1d0aC3nWJsbeSsorGsuivbOfUzP14ThwWDh8WhhcaxbQ/edit?usp=sharing
