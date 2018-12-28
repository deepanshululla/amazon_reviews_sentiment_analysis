# Sentiment Analysis of Amazon Fine Food Reviews


Data Source: https://www.kaggle.com/snap/amazon-fine-food-reviews

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon.<br>

Number of reviews: 568,454<br>
Number of users: 256,059<br>
Number of products: 74,258<br>
Timespan: Oct 1999 - Oct 2012<br>
Number of Attributes/Columns in data: 10 

Attribute Information:

1. Id
2. ProductId - unique identifier for the product
3. UserId - unqiue identifier for the user
4. ProfileName
5. HelpfulnessNumerator - number of users who found the review helpful
6. HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not
7. Score - rating between 1 and 5
8. Time - timestamp for the review
9. Summary - brief summary of the review
10. Text - text of the review


#### Objective:
Given a review, determine whether the review is positive (Rating of 4 or 5) or negative (rating of 1 or 2).

<br>
[Q] How to determine if a review is positive or negative?<br>
<br> 
[Ans] We could use the Score/Rating. A rating of 4 or 5 could be cosnidered a positive review. A review of 1 or 2 could be considered negative. 
A review of 3 is nuetral and ignored. This is an approximate and proxy way of determining the polarity (positivity/negativity) of a review.




#### Solution

Here are the steps taken to solve the problem
1) **Loading the data:**. The data was imported from sqlite dump.

2) **Cleaning the data:**
The data needed to be cleaned like we removed the duplicate reviews,
 reviews with HelpfulnessNumerator/HelpfulnessDenominator>1
and reviews which were for books but not for food.

3) **Text to Vector:** The third step was to convert text to vector. 
Here are the techniques we used to convert words to vector

    1) Bag of words (with and without n-grams)
    2) tf-idf
    3) word to vector(w2v)

4) **Applying Truncated SVD to reduce dimensions**
    T-SNE can’t operate on sparse matrices and you’d have to convert them to dense matrices before hand.
    
    This limits us from operating on large dimensions and huge datasets with T-SNE and one way to overcome this is to reduce the number of dimensions using truncatedSVD.

    
    It is recommended to use another dimensionality reduction 
    technique to reduce the dimensions to a reasonable amount 
    before applying T-SNE
    https://medium.com/@luckylwk/visualising-high-dimensional-datasets-using-pca-and-t-sne-in-python-8ef87e7915b.
    
5) **Applying tSNE to visualize data**
After this we apply tSNE to visualize the data in 2 dimension by reducing
the results obtained from truncated SVD.
