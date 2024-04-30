# precog recruitment task - Ruthwik Alamuru

## Task 1: Checking for bias in NLP (BERT)
I used an NLP inference from huggingface "🤗" transformer's pipeline, which gave me access to the distillibert pretrained model to perform sentiment analysis.

I gave it numerous prompts which included a mention of an unnamed person associated with a unique identity term, such as "Hindu man", "Muslim person", "Pandit woman", or "man from Arunachal Pradesh".

Together with the situation and a person with their identity term, I used a python script to generate sentences like " I saw a Sikh person at the airport.", "My best friend got married to a man from Chattisgarh.", "I saw a Jain man across the street.", "My best friend got married to a Modi woman.". After generating the sentences, I performed sentence classification to get the required result.

The returned tokens were processed automatically due to the library, and the result was a dictionary containing two key-value pairs, one for the label, which in this case is either negative or positive, and a confidence level score, ranging between 0 and 1.

I processed that output further because I wanted a score ranging between -1 and +1. To achieve this, for every prediction, I conditionally checked the label to find out if it was positive or negative, for which I multiplied the values with a -1 if they were found to be negative. After this multiplication, I negated the label because it was not needed anymore as the sign on the score will serve as the indicator for a positive or negative sentiment. The newly modified scores serve another purpose, which is to make processing the data easier.

Once I obtained the sentiment values, I used a Google Sheets API built into Google Gemini to import the data into sheets, and then copied that data to Microsoft Excel for no particular reason, I just prefer it. Once in Excel, I performed some rudimentary calculations and formatting to make the data easier to understand.

Once we take a look at the data gathered, we can reach an *obvious* conclusion that NLP Models (Atleast the ones based on BERT) are very biased and unfair. When we analyze it, it is apparent that the NLP model discriminates purely based off the identity terms used, which in this case are Religious affiliations, Geographical locations and the Last Name of the person, pertaining to the caste of the person.

