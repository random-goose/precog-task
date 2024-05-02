# Precog Recruitment Task - Ruthwik Alamuru
I have completed all the tasks assigned, in this repository are all the necessary files, along with a google colab notebook.

A detailed report of these files are available in the file tak-report at https://github.com/random-goose/precog-task/blob/main/task-report.md

A smaller TL;DR is also available at TLDR.md at https://github.com/random-goose/precog-task/blob/main/TLDR.md
(WARNING: this TL;DR is AI Generated)

## Task 1
I did not use the dataset to compare the stereotypes to the NLP output, but I measured, analysed and quantified the bias present in NLP in an Indian Context.

For this, the huggingface tranfroemers library was used which gave me access to the distilibert pre-trained NLP model.

Google Colab Notebook: https://colab.research.google.com/drive/1nrXGomiAtbHtl71Qr9XOO5wXoQx9T0t0?usp=sharing

It was the only library sued and I inpirted that data into excel to perform visualizaion to present that data better.

The data is available on the spreadsheet at: https://github.com/random-goose/precog-task/blob/main/bias-data.xlsx

## Task 2 & Bonus Task
I analyzed the prompts first manually to udnerstand the crux of the matter, to gather infromation about the structure of the prompts and the different identity terms. 

I then used a python script to identify the bias present in the models, in this script the re (Regular expressions) library was used as it aided me in searching.

The script can be accessed at: https://github.com/random-goose/precog-task/blob/main/bonus.py

The data from this script was also improted to excel and processed to access the bias present.

The data is available on the spreadsheet at: https://github.com/random-goose/precog-task/blob/main/bias-data.xlsx
(go to the sheet marked LLM)

Structure of the task report:
    Task 1: Checking for bias in NLP (BERT)
        1. Religious Bias
        2. Geographical Bias
        3. Caste Bias
    Task 2: Analyzing Prompts and Replies for Fairness in Legal AI
        Prologue
        Analysis of prompts
        Cohere Command r+
    Bonus Task
        Bias analysis
    Paper Reading
        Summary
        Report
        Strengths
        Weaknesses
        Improvements
    Footnotes