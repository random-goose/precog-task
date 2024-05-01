# Precog Recruitment Task - Ruthwik Alamuru

## Task 1: Checking for bias in NLP (BERT)
I used an NLP inference from the huggingface "🤗" transformer's pipeline, which gave me access to the distilbert pre-trained model to perform sentiment analysis.

I gave it numerous prompts which included a mention of an unnamed person associated with a unique identity term, such as "Hindu man", "Muslim person", "Pandit woman", or "man from Arunachal Pradesh".

Together with the situation and a person with their identity term, I used a Python script to generate sentences like " I saw a Sikh person at the airport.", "My best friend got married to a man from Chattisgarh.", "I saw a Jain man across the street.", "My best friend got married to a Modi woman.". After generating the sentences, I performed sentence classification to get the required result.

The returned tokens were processed automatically due to the library, and the result was a dictionary containing two key-value pairs, one for the label, which in this case is either negative or positive, and a confidence level score, ranging between 0 and 1.

I processed that output further because I wanted a score ranging between -1 and +1. To achieve this, for every prediction, I conditionally checked the label to find out if it was positive or negative, for which I multiplied the values with a -1 if they were found to be negative. After this multiplication, I negated the label because it was not needed anymore as the sign on the score will serve as the indicator for a positive or negative sentiment. The newly modified scores serve another purpose, which is to make processing the data easier.

Once I obtained the sentiment values, I used a Google Sheets API built into Google Gemini to import the data into sheets, and then copied that data to Microsoft Excel for no particular reason, I just prefer it. Once in Excel, I performed some rudimentary calculations and formatting to make the data easier to understand.

Once we take a look at the data gathered, we can reach an *obvious* conclusion that NLP Models (at least the ones based on BERT) are very biased and unfair. When we analyze it, it is apparent that the NLP model discriminates purely based on the identity terms used, which in this case are Religious affiliations, Geographical locations and the Last Name of the person, indicating the caste of the person. We can confidently conclude that the sentiment difference boils down to the different identity terms because that is the only difference between all the different sentences that were classified.

When we look at the outliers, which are indicative of the identity terms the model has a positive or negative bias towards, we can gather conclusions about which social or societal groups the model is biased for or against.

### 1. Religious Bias
When we take a look at the scores generated by the model when presented with differing religious identity terms, we can see that the model discriminates heavily against Muslim people, and is slightly biased against Sikh, Buddhist and Hindu people. The model seems to be biased towards Christian and Jain people.

When quantified, the order of bias would be:
Muslim < Sikh < Buddhist < Hindu < Jain < Christian
(sometimes the model would be more biased against Buddhists and less towards Sikhs, but the above-mentioned is the general trend observed)

### 2. Geographical Bias
When we quantify and analyze the sentiment scores when we give the NLP prompts with differing Geographical identity terms, we can identify the bias present based on the location identity of the person.

Instead of using the identity term associated with the states (like Himachali or Keralite), I generated the prompt with a structure of "... < state name > < man, woman, or person >. This was done because the researchers at Google already performed analysis using those words, so to try a different methodology I used the full state name followed by a pronoun. To make the analysis easier, I divided the states into three groups, based on the geographical location: Northern States, North Eastern States, and Southern States.

After we quantify and analyze the scores, we can conclude that the given NLP model is biased against North-Eastern states and slightly biased towards South Indian states. 
If we were to express it in an order, we would get:
North Eastern < Northern < Southern

### 3. Caste Bias