# humana_fall2019
###### humana case competition - fall 2019


# Analysis Plan
********

# Data Exploration and feature identification

> Events in a patient's therapy can be broadly categorized into -
###  Diagnosis/Surgery events
        * How frequently is a patient diagnosed? What is the average gap between Dx for a patient?
        * How much does a patient spend on Dx?
        * What kind of surgeries involve opioid therapy?
        * ...
###  Claims/prescription events
        * How frequently a patient on opioid therapy takes opioid claims?
        * How much does a patient spends on opioid claims? Actual and OOP cost both...
        * Who are the payors in market? How's HUMANA doing in the market? Any close competitors?
        * What is the rejection ratio in the market? Across Payors?
        * What physician segments are prescribing opioids? Any specialization required to prescribe opioids?
        * ...
###  Promotional events
        * What do these calls mean, Mbr? Prov? Other?
        * How frequently a patient is being reached through these calls?
        * Are LTOT patients reached more frequently through these calls?
        * ...
        
# Feature selection
> Idea is to create a patient level feature matrix which will be used to predict LTOT patients. Features identified in previous stage can be used to build the feature matrix...

# Model fitting
> Classification problem
>> Logistic regression, KNN, Trees, Ensemble methods...

# Model validation and final results
> Based on model accuracy...

********
********


# Data related questions
******
> * What is the definition of 'on hand'? Any identifier in data to identify opioid medication from other medication?
#####  If a patient is taking opioids, he is 'on-hand'. "Rx Claim - Paid" with a valid MME defines an opioid Rx claim. 
> * What is the market basket for the given data? What all drugs other then opioids are included in the given data? 
Is entire diagnosis history of a patient who has taken opioid in the analysis timeframe available in the data?
##### Kind of Yes, the data captures events that are not related to opioids too.
> * What is difference between Rx cost, Net Paid amount (attr 4), Member responsible amount (attr 9) and Payble quantity? --to calculate cost related KPIs
##### Rx cost = Total cost ; Net paid amount = Amount paid by HUMANA (payor) = (Total cost - OOP)
> * What is 'New diagnosis top 5'?
##### Something regarding the other Dx patient went through apart from the ones listed. Not so important
> * In case of multiple initiation events for a patient, which event is reference point for #days given in 'days' column?
##### Initiation event  = Opioid Naive claim with a valid MME
##### Opiod Naive claim = No Opioid taken in 90 days lookback
> * what is the difference between event 'Fully Paid Claim' and 'RX Claim-Paid'?
##### Fully paid claim are medical claims where as Rx claim paid are pharmacy claims
> * Definition of LTOT - 
##### Patient >=162 days ‘on hand’ within 180 days after qualifying claim/Initiation event
##### A patient needs to be tagged as LTOT or not after every initiation event i.e. everytime a patient is decleared a new opioid patient, he/she needs to be tagged as LTOT or not.
##### Patient can have more than 1 initiation event which means patient has returned to the therapy and considered as new opioid patient. We have to predict about every new patients whether they will be on LTOT or not.
> * ...
