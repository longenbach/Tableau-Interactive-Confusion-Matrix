# Interactive Confusion Matrix

### What:

A confusion matrix or error matrix is a tabular visualization to access the performance of a classification model. In the binary case, it allows us to examine the number of false positives and negatives. In the multi-class case, it allows us to examine more generally which classes the model is mixing up. 


### Why:

In classification problems where features are numeric (ex. age, weight, or shoe size) distribution plots can be used to further visualize the feature differences between false positives and true positives. However, in cases where features are a single string of text (ex. blog post, a question, a review), visualizing the cause of misclassification can prove to be challenging. 

In text classification, first you have to decide on how to encode the text based information. Bag of words, Tf-Idf, Word2Vec, or more advanced embeddings (ELMo & BERT) are commonly used to represent text as numerical features. Once feature engineering is complete, secondly you have to decide on what classification model to test. 

Test accuracy and statistics can be used when evaluating combinations of 1) method to encode text numerically and 2) architecture of classification model. However, sometimes simply chasing accuracy isn’t the best choice or even the initial goal. Instead modeling testing can be used to evaluate the strength of the data. Machine learning is not magic as it is only as good as the data we put in. 

When recently working on a semi-supervised text classification project for United Technolgies (UTC), we were using confusion matrices to evaluate models like discussed above. To better understand our data and text misclassifications sometimes the best thing you can do is look at your data. In general, it can also be helpful to look at which tokens are associated with predicting a certain class. Inspecting your data gets at the question could a human manually label this text correctly? While a confusion matrix allows for counting the number of misclassifications, it doesn’t allow for viewing the misclassifications itself. 

The new interactive Tableau confusion matrix solves tries to solve this issue.

