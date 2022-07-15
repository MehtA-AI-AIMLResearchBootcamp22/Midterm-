# Midterm Project: Predicting the Gender of the Author of a Text

## Problem
Given a dataset of eleven scientific texts written by both male and female authors, we were tasked with building a machine learning model that was capable of predicting the gender of the author of a similar book. We not only aimed to create a model with high accuracy, but also endeavored to find which features contributed most to the prediction of the model, which would reveal the inherent difference between male and female writing. 

## Methods
Our methods contain several important steps.
1. Preprocessing
2. Features
3. Model
4. Analysis

## Analysis
We decided to use the length of each feature, part of speech tagging, and tf-idf to determine if the author of a text is male or female. Because men tend to use more abbreviations and write more concisely than women, we thought that that could be reflected in the length of sentences the authors used. Also, men used more determiners (words like "the", "a", and "as") and more adjectives than women, which is why we thought part of speech tagging would be useful. Finally, because men and women have different writing styles (women try to create a relationship between the reader and the writer, while men are more focused on giving facts), we decided to use tf-idf, which determines how important a word is to the document, since in different styles of writing, different words would be important.

When the length of each sentence was used as the only feature, it gave an accuracy of around 60%, meaning the model is learning, but it's not learning much, which is why we decided to include it. After running our model, we determined that both part of speech and determining the importance of words were most important to our model.

Another feature that we tested was Bag of Words, which finds the frequency of each word. This gave an accuracy of around 75%, but we ultimately decided not to use it because most likely, the words that showed up the most, like determiners, would already be covered with part of speech tagging.


## Code
<script src="https://gist.github.com/OliviaG1/92f9aaaa7bebfa75f7fef4d7550b83b0.js"></script>
