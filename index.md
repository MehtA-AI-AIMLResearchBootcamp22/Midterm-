## Predicting the Gender of the Author of a Text

## Problem
Given a dataset of eleven scientific texts written by both male and female authors, we were tasked with building a machine learning model that was capable of predicting the gender of the author of a similar book. We not only aimed to create a model with high accuracy, but also endeavored to find which features contributed most to the prediction of the model, which would reveal the inherent difference between male and female writing. 

## Preprocessing
We had a dataset of six books with female authors given to us by the professors and five books with male authors taken from Project Gutenberg. We had to make the data as clean as possible in order for the model to work best. 
These are our preprocessing steps:
1. Remove irrelant text (footnotes, website formatting, etc.)
2. Split the books into groups of ten sentences each, to greatly increase the size of our dataset
3. Make all words lower case 
4. Remove stopwords
5. Remove punctuation
6. Lemmatize all words

## Features
First, we needed to vectorize our text data into numbers so the model would be able to run on it. We tried several vectorizing techniques, such as Bag of Words, which finds the frequency of each word, and TF-IDF, which combines the frequency of each word with the inverse frequency across all documents. Ultimately, the TF-IDF gave better results, so we used that in the end. This is probably because Bag of Words does not take into account common words which occur across many documents and have no importance.

We now had several huge vectors of TF-IDF, but we also decided to use the length of each sentence, since women tend to write more than men, and part of speech, since men tend to use more determiners and adjectives, as our features. To find the sentence length, we simply took the length of each document (each of which consists of ten sentences). To find the part of speech amounts, we first chose which part of speech components we wanted to include. We included most of them, only excluding the ones that would seem useless (particles, cardinal numbers, etc.) We then went through each document to find the number of times each of these parts of speech  occured.

Ultimately, our training and testing datasets consisted of TF-IDF vectors, sentence length, and number of parts of speech.

## Model
We tested several different models including SVM(support-vector-machine), neural network, and logistic regression. In the end, we decided to use the SVM because it yielded the highest accuracy. The linear SVM is widely regarded as one of the best text-classification algorithms, and this is because it can handle the huge number of features given by the vectorization and it works well with sparse matrices. 

## Results
Accuracy: 90% - 96% 

Important features:

  Specific words (female) - "child", 
                            "creature", 
                            "exterior", 
                            "figure", 
                            "god", 
                            "madam",
                            "make",
                            "onely",
                            "sensitive",
                            "woman"
                            
   Specific words (male) - "begin",
                           "diver",
                           "experiment",
                           "faculty",
                           "find",
                           "knowledge",
                           "mind",
                           "ought",
                           "self",
                           "virtue"
                   
   Parts of speech (female) - pronouns,
                              interjections (hey, oh, yikes, etc.),
                              modals (can, should, must, etc.),
                              adjectives,
                              adverbs,
                              proper nouns
                              
   Parts of speech (male) - comparative adverbs (bigger, better),
                            superlative adverbs (biggest, best),
                            prepositions,
                            nouns

## Analysis
Looking at the most important words for both female and male authors, it seems as if the female writers use more words pertaining to the human, such as "child", "madam", "god", and "woman". The men, on the other hand, seem to focus more on providing information and education, with words like "knowledge", "mind", "virtue", and "experiment". This raises an important point as to the subject of the books - although all of the books are scientific texts, women mostly wrote books about more abstract and humanly concepts, such as philosophy and midwifery, while the men generally wrote more rigorous books about mathematics and science.

The model observed some specific differences in part of speech usage between men and women, such as women using more interjections, modals, adjectives, and proper nouns, while men use more comparative adverbs and superlative adverbs. All of these can be used to tell the gender of the author of a book. Although I expected men to write shorter, more concise sentences, the length of the sentence appeared to not matter too much, only leaning slightly towards the female side.

In general, based on these features, I suspect that an important part of the difference between male and female writing is influenced heavily by the scarcity of female authors at that time. As I observed when looking through the female texts, almost all the books contained a section explaining why and how they recieved education and wrote the book as a female, as well as addressing their female audience and in general making many references to genderl. Because female writers were so scarce back then, these authors probably were compelled to justify their writing by making references to their gender in the book. On the other hand, the male authors' books usually did not contain any part or reference to the author's gender, or gender in general. This is supported by the use of the female authors of the words "woman" and "madam", as well as their use of pronouns. 


## Code
<script src="https://gist.github.com/OliviaG1/92f9aaaa7bebfa75f7fef4d7550b83b0.js"></script>
