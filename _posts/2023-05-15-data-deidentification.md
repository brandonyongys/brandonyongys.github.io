---
date: 2023-05-15

layout: post
title: Data de-identification
description: How to utilize data while protecting privacy?

comments: true
published: false

# ORIGINAL 
# Data is an important aspect in any data science work. Without data, tasks like modelling and feature extraction could not be done. But it need not be de-identified as the identifiers often serve little to no purpose in a data science project except at the initial stage where multiple datasets are stitched together to form a more holistic picture. 

# However, as an individual, I would love to have my data de-identified as much as possible so as to protect my own privacy and confidential information such as personal health information (PHI). Such data would definitely need to be de-identified as it could expose extremely sensitive information such as HIV and AIDS status. Other than that, stolen identifiable data could be used for malicious intent. Hence, there are rules and regulations across countries to ensure PHI is fully de-identified before any work could be done including research work. In Singapore, all personal data is protected by the PDPA law, which serves as the base law, and all health records are subjected to HBRA on top of PDPA. 

# De-identification is not mainly applied in the healthcare sector. It is also applied in other sectors such as financial institutions or e-commerce where the analysts could access personal information and cause financial losses to either the clients or company, or worse both, if it is not managed well.

---

Data is a critical component in any data science project, as it serves as the foundation for tasks such as modeling and feature extraction. However, in some cases, it is essential to de-identify data to protect the privacy of individuals and sensitive information, such as personal health information (PHI). In such instances, identifying information such as names and addresses may serve little to no purpose, except during the initial stage where multiple datasets are combined to form a more comprehensive picture.

In Singapore, the Personal Data Protection Act (PDPA) serves as the base law protecting personal data, while the Healthcare Services Act's (HSA) provisions safeguard the confidentiality of medical records. Such regulations are necessary to ensure that PHI is adequately de-identified before any research work or data analysis is performed. This is particularly crucial in the healthcare sector, where identifying data could expose sensitive information such as HIV and AIDS status, leading to stigmatization and discrimination.

However, de-identification is not only applicable in the healthcare industry but also other sectors such as finance and e-commerce. Analysts who access personal information without proper management could cause significant financial losses to clients and the company. As such, it is crucial to adhere to regulatory requirements and best practices when handling sensitive data.

In summary, de-identification is an essential practice for protecting personal information and sensitive data in various industries, including healthcare, finance, and e-commerce. Regulatory frameworks such as the PDPA and HSA provide guidelines and rules that companies and individuals must follow when dealing with personal information to ensure compliance and mitigate risks.


# Personally Identifiable Information (PII)
According to ChatGPT, below are some of the common PII that are typically de-identified, which overlaps with the list found [here](https://www.immuta.com/blog/what-is-data-de-identification/#:~:text=There%20are%20two%20primary%20de%2Didentification%20methods%3A%20generalizing%20and%20randomizing). The list is not exhaustive and it may vary depending on the context, sensitivity of the data as well as the regulatory requirements.
<ul>
    <li>Names (including first, middle, and last names)</li>
    <li>Addresses (including street address, city, state/province, and postal code)</li>
    <li>Phone numbers (including mobile, home, and work numbers)</li>
    <li>Email addresses</li>
    <li>Social Security Numbers (or equivalent national identification numbers)</li>
    <li>Driver's license numbers</li>
    <li>Passport numbers</li>
    <li>Health insurance policy numbers</li>
    <li>Medical record numbers</li>
    <li>Biometric identifiers (such as fingerprints or facial recognition data)</li>
</ul>

None of these common identifiers came as a surprise as having any one of these would directly identify the individuals. There are other identifiers such as race and age which could identify the individual. However, such identifiers would need to exist in a particular set in order to identify the individual with high confidence.

# De-identification techniques

De-identification can be achieved through pseudonymization, which involves replacing the individual's set of identifiers with another set of identifiers that may or may not be random or nonsensical. For instance, a name like `Brandon` could be replaced with `Michael` or even a random alphanumeric string such as `b295d117135a9763da282e7dae73a5ca7d3e5b11`. However, pseudonymization may not be appropriate for other identifiers, such as dates, that are required to study the temporal or spatial effects. Furthermore, pseudonymization alone may not be sufficient to protect against re-identification if there are specific unique characteristics that can be linked back to the individual.

To provide further privacy protection, the k-anonymization technique can be employed. This method ensures that any subset of individuals sharing a set of specific unique characteristics includes at least k individuals. For example, if there are very few individuals aged 95 and above, they could be grouped together with a subgroup of individuals aged 80 to 94 years old to protect their identities. Any analysis conducted on this group would not reveal the identity of any specific individual.

# Simple de-identification codes
In order to de-identify strings or numbers, one could simply use the `hashlib`. A sample code is as shown below:
~~~
import hashlib

# Create a hash object for SHA-256
hash_object = hashlib.sha1()

# Convert the string to bytes and update the hash object
original_string = "Hello, World!"
original_string += "salt"
hash_object.update(original_string.encode('utf-8'))
# Update is needed to update the state of the hash object with the input bytes, which will be used to compute the final hash value
# Additional string (termed as 'salt') may be added to the string to add security so that could not try to re-identify the original string

# Get the hashed value as a hexadecimal string
hashed_string = hash_object.hexdigest() # cae017a3404068bde266528e0187c79a86d95baf
~~~
To enhance the security of the de-identification framework, a 'salt' term is introduced into the original string. This additional layer of protection reduces the risk of re-identification, particularly through brute-force methods that test all possible strings. Omitting the salt would always result in a consistent hashed string, such as `0a0a9f2a6772942557ab5355d76af442f8f65e01` for 'Hello, World!' string, but adding the salt ensures that the output differs each time. Additionally, the lack of salt could result in multiple datasets sharing the same de-identified identifiers, which could enable malicious users to combine and analyze the data for a more comprehensive view of individuals.

One could always use the above technique to de-identify dates as well. However, the hashed dates are of no use if the analyst wants to track the individuals over time and space in order to study the temporal effect. One way is to systematically shift the dates for each individual randomly by using the `hashlib` and `random` libraries.

~~~
import datetime
import hashlib
import random

salt = "34535"
original_date = datetime.date(2022, 4, 1)

# Use a cryptographic hash function to generate a unique hash value for the input
hash_value = hashlib.sha1(str(salt).encode()).hexdigest()

# Set the random seed to the hash value
random.seed(hash_value)

# Generate a random number between 0 and 1
random_number = random.random()*2 - 1

# Scale the random number to the desired range
fixed_random_number = int(random_number * 3650)

offset_n = datetime.timedelta(days=fixed_random_number)
shifted_date = original_date + offset_n # datetime.date(2029, 10, 29) 
~~~
Again, the same salt and original string could be combined to generate a unique hash value for each individual. The hash value is then used to generate a random fixed value before shifting all the dates for a particular individual. For more information, please refer to my [deidentification github](https://github.com/brandonyongys/deidentification)

# Limitations
The techniques mentioned earlier are effective for de-identifying data that is structured in a tabular form, such as in a dataframe. However, when dealing with free text data, the task of de-identification becomes more challenging. One approach to de-identify free text data is to use a Large Language Model (LLM) to perform Part-of-Speech (POS) tagging. This involves identifying and labeling the different parts of speech in the text, such as nouns, verbs, and adjectives.

However, using an LLM for de-identification may result in over-generalization, where more information than necessary is removed, ultimately rendering the data unusable. This is because LLMs are designed to generate language based on patterns they have learned from large datasets. In some cases, they may generalize too much and remove information that is actually relevant to the data. Therefore, it's important to carefully evaluate the results of using an LLM for de-identification and adjust the approach as needed.


# Conclusion
In conclusion, de-identification is an important step when it comes to protecting the individual's private information. Direct identifiers may be de-identified using the `hashlib` library and dates could be shifted using a combination of `hashlib` and `random` packages. 
