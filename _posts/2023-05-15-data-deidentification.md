---
date: 2023-05-15

layout: post
title: How well perceived is Marina Bay Sands?
description: Sentiment analysis of MBS reviews

comments: true
published: true

---
Data is an important aspect in any data science work. Without data, tasks like modelling and feature extraction could not be done. But it need not be de-identified as the identifiers often serve little to no purpose in a data science project except at the initial stage where multiple datasets are stitched together to form a more holistic picture. 

However, as an individual, I would love to have my data de-identified as much as possible so as to protect my own privacy and confidential information such as personal health information (PHI). Such data would definitely need to be de-identified as it could expose extremely sensitive information such as HIV and AIDS status. Other than that, stolen identifiable data could be used for malicious intent. Hence, there are rules and regulations across countries to ensure PHI is fully de-identified before any work could be done including research work. In Singapore, all personal data is protected by the PDPA law, which serves as the base law, and all health records are subjected to HBRA on top of PDPA. 

De-identification is not mainly applied in the healthcare sector. It is also applied in other sectors such as financial institutions or e-commerce where the analysts could access personal information and cause clients financial losses if it is not managed well.

List of identifiers
https://www.immuta.com/blog/what-is-data-de-identification/#:~:text=There%20are%20two%20primary%20de%2Didentification%20methods%3A%20generalizing%20and%20randomizing.

Below is the list of identifiers that would need to be de-identified based on the link above:
Names
Dates, except the year
Telephone numbers
Geographic data
Fax numbers
Social Security numbers
Email addresses
Medical record numbers
Account numbers
Health plan beneficiary numbers
Certificate/license numbers
Vehicle identifiers and serial numbers, including license plates
Web URLs
Device identifiers and serial numbers
Internet protocol addresses
Full face photos and comparable images
Biometric identifiers
Any unique identifying number, characteristic, or code

De-identification techniques
1) pseudonymization 
- individuals are given another set of identifiers (e.g. Brandon is renamed to Michael, all dates are shifted by n days). This helps the user to track the individuals across time. However, this step alone does not prevent the user from re-identifying the individual if there are specific unique set of characteristics. 

2) k-anonymization
- this is when data is dealt in such a way that any subset of data would contain at least k individuals sharing the same characteristics. E.g. there may be many individuals below the age 80 with positive HIV and not many individuals aged 80 and above with positive HIV. Instead, the age threshold may be lowered 80-> 40 so that there are more individuals in the 40+HIV subset. This makes re-identification effort by chance significantly less likely. 


Sample codes to de-identify

Conclusion