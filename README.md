# NLP project - Toxic Comments Classification
![cover!](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/blob/main/assets/cover%20image.png)

Online bullying and violence are phenomena we hear about more and more in recent years.
This project deals with this issue with the aim of analyzing and classifying user comments and identifying toxic comments of different types.

In this small project I'll classify an online comment to its levels of toxicity using an LSTM architecture.
More info down below.

* [Data](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#data)
* [The flow](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#the-flow)
* [The tested models](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#the-flow)
* [Files in the repository](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#files-in-the-repository)
* [Results](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#results)
* [Further Work](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#further-work)
* [References](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/new/main?readme=1#references)

## Data
I found relevant data on Kaggle, this data was published as part of a challenge to classify toxic comments.
The data contains 159,571 samples of Wikipedia comments which had been labeled by human raters for toxic behavior.
The types of toxicity are:
* Toxic
* Severe-toxic
* Obscene
* Threat
* Insult
* Identity-hate

#### Preprocessing
Below are some of the operations I performed to clean the data:
* Change letters to lowercase
* Remove text within brackets, special characters,newline characters, extra space, stopwords
* Lemmatization - spacy

After cleaning the data I did a train-test-validation split using a function based on an algorithm from an academic article from 'Sechidis K., Tsoumakas G., Vlahavas I. (2011) On the Stratification of Multi-Label Data' , that deals well with a multi-label case and does both shuffle & stratify.
This method creats a train-test-validation split that represents in the best way the original data.

## The flow
Thinking about the project as a product, we decided on the following flow:
1. User sends a comment.
2. Classification of the comment as a toxic or non-toxic - binary problem.
3. If it's toxic, we'll check the comments' type of toxicity - Multilabel problem.

## The tested models
| Stage  | Problem type | Model |
| ------------- | ------------- | ------------
| 1 | Binary Classification - toxic / not toxic   | Random Forest Classifier |
| 1 | Binary Classification - toxic / not toxic   | 1D CNN |
| 2 | Classification toxicity level | CNN dedicated to multi-label classification problem |
| 2 | Classification toxicity level | NN LSTM model |

## Files in the repository

## Results
* 1st stage models:

![result1!](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/blob/main/assets/result%201st%20stage%20models.JPG)

Both models reached a high level of accuracy and were quite close, 
but the CNN model has a higher score and is a lot faster than the random forest classifier.

* 2nd stage models:

![result2!](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/blob/main/assets/result%202nd%20stage%20models.JPG)

* Both models reached a high level of accuracy of 85% or higher
* The LSTM model yields a better result.
* Despite this, the results show that both models had difficulty identifying the same two levels of toxicity - threat, and identity hate.

![trainvalscore!](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/blob/main/assets/train%20validation%20acc%20score%20per%20epoch.JPG)

* The CNN model seems to underfit - Probably because the imbalanced dataset. 
* A possible solution for that would be to train for less epochs. But I decided that two epochs is not long enough to the learning stage.
* Both models learn quite fast, probably due to imbalanced dataset

## User interface

Finally, I created a user interface where a user could enter a comment and get its classification in real time.

Below is an example

![interface!](https://github.com/Brit771/NLP-project---Toxic-Comment-Classification/blob/main/assets/interface.JPG)

## Further Work
1. To develope the model further I suggest to perform data augmenattion for the unrepersented labels.

2. Transformers & BERT - while examining different models, I experimented with BERT but had many issues implementing it due to computing power.
I recommend trying to find a suitable BERT model and fine-tuning it in order to get better results.

3. Train the 2nd stage models on a data set that has major\only toxic comments and check if this solves the problem of identifying the levels of toxicity that the models failed to learn.

4. Additional evaluation metrics can be examined.

## References
* [On the Stratification of Multi-Label Data article](http://lpis.csd.auth.gr/publications/sechidis-ecmlpkdd-2011.pdf)
