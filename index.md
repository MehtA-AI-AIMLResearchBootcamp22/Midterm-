## Predicting the Gender of the Author of a Text

## Problem
Given a dataset of eleven scientific texts written by both male and female authors, we were tasked with building a machine learning model that was capable of predicting the gender of the author of a similar book. We not only aimed to create a model with high accuracy, but also endeavored to find which features contributed most to the prediction of the model, which would reveal the inherent difference between male and female writing. 

## Preprocessing
We had a dataset of six books with female authors given to us by [insert professor names] and five books with male authors taken from Project Gutenberg. We had to make the data as clean as possible in order for the model to work best. 
These are our preprocessing steps:
1. Remove irrelant text (footnotes, website formatting, etc.)
2. Split the books into groups of ten sentences each, to greatly increase the size of our dataset
3. Make all words lower case 
4. Remove stopwords
5. Remove punctuation
6. Lemmatize all words

## Features
First, we needed to vectorize our text data into numbers so the model would be able to run on it. We tried several vectorizing techniques, such as Bag of Words, which finds the frequency of each word, and TF-IDF, which combines the frequency of each word with the inverse frequency across all documents. Ultimately, the TF-IDF gave better results, so we used that in the end. This is probably because Bag of Words does not take into account common words which occur across many documents and have no importance.

We now had several huge vectors of TF-IDF, but we also decided to use the length of each sentence and part of speech as our features. To find the sentence length, we simply took the length of each document (each of which consists of ten sentences). To find the part of speech amounts, we first chose which part of speech components we wanted to include. We included most of them, only excluding the ones that would seem useless (particles, cardinal numbers, etc.) We then went through each document to find the number of times each of these parts of speech  occured.

Ultimately, our training and testing datasets consisted of TF-IDF vectors, sentence length, and number of parts of speech.

## Model
We tested several different models including SVM(support-vector-machine), neural network, and logistic regression. In the end, we decided to use the SVM because it yielded the highest accuracy. The linear SVM is widely regarded as one of the best text-classification algorithms, and this is because it can handle the huge number of features given by the vectorization and it works well with sparse matrices. 

## Results


## Analysis
We decided to use the length of each feature, part of speech tagging, and tf-idf to determine if the author of a text is male or female. Because men tend to use more abbreviations and write more concisely than women, we thought that that could be reflected in the length of sentences the authors used. Also, men used more determiners (words like "the", "a", and "as") and more adjectives than women, which is why we thought part of speech tagging would be useful. Finally, because men and women have different writing styles (women try to create a relationship between the reader and the writer, while men are more focused on giving facts), we decided to use tf-idf, which determines how important a word is to the document, since in different styles of writing, different words would be important.

When the length of each sentence was used as the only feature, it gave an accuracy of around 60%, meaning the model is learning, but it's not learning much, which is why we decided to include it. After running our model, we determined that both part of speech and determining the importance of words were most important to our model.

Another feature that we tested was Bag of Words, which finds the frequency of each word. This gave an accuracy of around 75%, but we ultimately decided not to use it because most likely, the words that showed up the most, like determiners, would already be covered with part of speech tagging.


## Code
<script src="https://gist.github.com/OliviaG1/92f9aaaa7bebfa75f7fef4d7550b83b0.js"></script>
