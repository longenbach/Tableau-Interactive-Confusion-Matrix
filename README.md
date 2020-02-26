# Interactive Confusion Matrix

<p float="center">
  <img src="imgs/Tableau_Demo.mov"/>
  <em>image_caption</em>
</p>



### What:

A confusion matrix or error matrix is a tabular visualization to access the performance of a classification model. In the binary case, it allows us to examine the number of false positives and negatives. In the multi-class case, it allows us to examine more generally which classes the model is mixing up. 

<p align="center">
  <img src="imgs/Binary_CM.jpg" width="400"/>
  [Confusion Matrix](https://manisha-sirsat.blogspot.com/2019/04/confusion-matrix.html)
</p>

### Why:

In classification problems where features are numeric (ex. age, weight, or shoe size) distribution plots can be used to further visualize the feature differences between false positives and true positives. However, in cases where features are a single string of text (ex. blog post, a question, a review), visualizing the cause of misclassification can prove to be challenging. 

In text classification, first you have to decide on how to encode the text based information. Bag of words, Tf-Idf, Word2Vec, or more advanced embeddings (ELMo & BERT) are commonly used to represent text as numerical features. Once feature engineering is complete, secondly you have to decide on what classification model to test. 

Test accuracy and statistics can be used when evaluating combinations of 1) method to encode text numerically and 2) architecture of classification model. However, sometimes simply chasing accuracy isn’t the best choice or even the initial goal. Instead modeling testing can be used to evaluate the strength of the data. Machine learning is not magic as it is only as good as the data we put in. 

When recently working on a semi-supervised text classification project for United Technolgies (UTC), we were using confusion matrices to evaluate models like discussed above. To better understand our data and text misclassifications sometimes the best thing you can do is look at your data. In general, it can also be helpful to look at which tokens are associated with predicting a certain class. Inspecting your data gets at the question could a human manually label this text correctly? While a confusion matrix allows for counting the number of misclassifications, it doesn’t allow for viewing the misclassifications itself. 

The new interactive Tableau confusion matrix solves tries to solve this issue.

### How:

I use a straightforward dataset to show the structure of this new confusion matrix. The dataset used are text posts from Google each with an associated code tag (Python, C, Java, HTML). The text classification model was copied from Github user  to generate predicted tags for each of these posts. To create the new interactive confusion matrix we just need a few more fields.  

1) Assign each label/tag to an integer value. Using a LabelEncoder in Sklearn is an easy way to accomplish this. 

2)  For each text post give it a random (x,y) coordinate based on its true and predicted label.
```python
def random_xyPredicted(label_num,eps=0.05):
    label_num = int(label_num)
    return np.random.uniform(label_num+eps,label_num+1-eps,1)[0]

def random_xyTrue(label_num,number_classes=len(encoder.classes_),eps=0.05):
    label_num = int(label_num)
    r = np.random.uniform(label_num+eps,label_num+1-eps,1)[0]
    return (r-number_classes)*-1
```

3)  Write to data frame to google sheets for example and connect with Tableau. 








