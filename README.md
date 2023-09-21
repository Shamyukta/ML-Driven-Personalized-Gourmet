# ML-driven-Personalized-Gourmet

This project is aimed at easing out the user experience of a customer who seems to be indecisive about what they want and also help business owners ameliorate their businesses.

<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/Restaurants-in-Brewster-MA.png" width = 700><p>
  
  ## Table of Contents

- [Problem Statement](#problemstatement)
- [Understanding the  Data](#understandingthedata)
- [Solution Architecture](#architecture)
- [Data Exploration](#EDA)
- [Features that constitute the solution](#features)
- [Algorithms Used](#algo)
- [Results](#results)
- [Evaluation metrics](#evaluation)
- [Challenges Faced](#challenges)
- [Future Scope](#futurescope)
- [References](#references)
- [Contact Me](#contact)  
  

***
<a id='problemstatement'></a>
## Problem Statement
In a world where food delivery is done within minutes, finding the right restaurant based on a user’s taste takes a lot more time with the plethora of options. In addition, every restaurant is judged by the customer reviews and ratings. The intention of this project is to build a recommendation system for restaurants in Philadelphia, based on the past experiences and reviews of a particular user. **The hybrid recommendation engine which is a combination of matrix factorization and cosine similarity will be used to solve this problem. This project also aims at providing the restaurant owners, the insights into what is working well and what can be improved which could help the restaurant retain the good services and improvise on the flawed ones**. Also a technique called sentiment analysis is used to provide insights about the social sentiment pertaining to the restaurant.

<a id='understandingthedata'></a>  
## Understanding the data
I have pulled the datasets using the Yelp API endpoint https://api.yelp.com/v3/businesses/search. 
The datasets that I designed for this project are:
  
1) Restaurant information dataset
  
2) Restaurant reviews dataset
  
3) Users dataset

Below are the Schemas of the JSON structure of each of the dataset that I have prepared:
  
**Restaurant Information Dataset**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/restaurant_new.png" width = 700><p>  
  
**Restaurant Reviews Dataset**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/reviews_new.png" width = 700><p>
  
**Users Dataset**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/users.png" width = 700><p>
  
<a id='architecture'></a>
## Solution Architecture
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/architecture.png" width = 700><p>  

1) Data Retrieval - Python API programming from the Yelp API endpoint.
2) Business logic - Pyspark SQL, Pyspark MLlib, Pandas,Pymongo.
3) Storage mechanisms - MongoDB Atlas Cloud, HDFS.
4) Data visualization - Matplotlib, Seaborn, Recmetrics, Folium, Wordcloud.
5) Hyper Parameter Tuning - Pyspark Grid Search feature.
  
<a id='EDA'></a>
## Data Exploration
  
Let’s start with some basic yet useful data exploration and see what business value they can add. We will start of with,
1) The distribution of ratings in a particular city
2) The long tail plot
3) Most active users of the system
4) The restaurants with most customer traffic
5) The most valuable patrons of a particular restaurant
6) Categories of dishes to avoid in the city
  
**Distribution of Ratings in a particular city**

<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/Ratings%20distribution'.png" width = 700><p>
  
Ratings are a good calibration of the quality of a restaurant. The ratings distribution for each city can improve the confidence of people who are looking to move to the city and tourists as well. 
  
**Long Tail Plot**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/longtailplot.png" width = 700><p>
  
The long tail plot is often underestimated and can be very useful for recommender systems.
It indicates that most of the customer traffic is centralized to the most popular restaurants in the city. 

**Business value:**

While recommending we should be wary of the fact that users already know these restaurants and are expecting to try something new. Recommendations that avoid these restaurants can be more personalized and clever. 
It can also improve the business of “New to the Market” restaurants.
  
**Most Active Users of the System**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/top_10_reviewers_byreviews.png" width = 700><p>
  
**Business Value:**

Encouraging users who review and contribute to the system using special offers and freebies can really contribute to better performance of the recommendation engine. 
The user-business interaction matrix used in the recommendation algorithm is extremely sparse. In our case 99.4% sparse. Which means there are several million restaurants and several million orders happening everyday. But only a very small percentage of users rate their experience. So there is basically a lot of fill in the blanks. As reviews start pouring in, the model can learn better and achieve better performance and personalization.
  
**The Restaurants with the Most Customer Traffic**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/top10restaurantsbyrating.png" width = 700><p>
  
This is usually not very useful during modeling. But can be very useful during hypothesis and A/B testing.

**Most Valuable Patrons of a Particular Restaurant**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/mvp.png" width = 700><p>
  
**Business Value:**
Insights like these can help  business owners reinvent the aspect of customer relationship.
  
<a id='features'></a>
## Features that constitute the solution
  
**Features for Patrons:**
1) Every user in the system will be provided with the recommendations from the hybrid engine.
2) The users will also be able to locate these recommendations on the map to filter further based on the location.
3) The users will also be provided with insights such as best rated restaurants, dishes to avoid etc.
4) A new user who has currently logged into the system will be provided the top 10 trending restaurants nearby based on their coordinates.

 **Features for the business owners:**
1) The business owners will also be provided with insights such as most valuable patrons, their current rating and reviews.
2) What is doing well and what people are not satisfied about, using the sentiment analysis technique.
  
<a id='algo'></a>

## Algorithms Used

I have taken separate efforts to explain my experience with these algorithms in the following medium post. Please check out if interested.  

**https://medium.com/@rs7671/generating-business-value-using-als-cosine-similarity-and-linear-svm-part-1-daad41825030**
  
 <a id='results'></a> 
 ## Results

 **Set of 10 recommendations for the user_id "mNCd6ctHcY0ueistbprTwg" using the ALS model**
  
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/recusingALS.png" width = 700><p>
   
 **The Table containing the predictions of ratings made for all users, business combination in the test set**
 
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/table.png" width = 700><p>
     
 **Table containing the Top 10 Restaurant recommendations for the same User but using Cosine Similarity**
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/cosinerec.png" width = 700><p>
   
 **Sentiment Analysis - Table showing trigrams of the text**
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/trigrams.png" width = 700><p>
   
 **Sentiment Analysis - trigrams with svm coefficients (weights)**
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/svmcoeff.png" width = 700><p>
   
 **Sentiment Analysis - Positive and Negative word clouds**
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/wordcloud.png" width = 700><p>  
   
 <a id='evaluation'></a>  
 ## Evaluation Metrics
   
 We will be evaluating the performance of our model based on the following techniques,
 1) Straightforward accuracy calculation
 2) Precision, Recall, F score @ k
 3) ROC and AUC curve
 4) RMSE trends with various hyperparameters
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/accuracy.png" width = 700><p>  
  
 Is this a good estimate? No it isn’t. Why?

 Let’s find how skewed the dataset is,
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/skewedness.png" width = 700><p> 
   
 Since the training data contains 69% positive labels. Even if we classify every restaurant in the system as a possible recommendation(positive label) then the      accuracy will go up to  69 %. So usually its not a good idea to evaluate a skewed training set using accuracy. Thats why we move towards precision, recall and F0.5    score.
   
 <p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/prf_wr_thresholds.png" width = 700><p>
   
I was able to achieve a precision of about 83%. For a recommendation system precision is a lot more important than recall. This is because the precision tries to reduce the false positivity and recall tries to reduce the false negativity. False positives are basically restaurants that the user did not like but the model predicted that he would. And so these restaurants will be displayed as recommendations to the user. However, false negatives ( restaurants that the user liked but the model missed it) are never shown to the users and there is no way that the users would even encounter false negatives in a recommendation system. That is why we emphasize more on precision over recall.
The above plot basically shows the values of precision and recall for different classification threshold values ranging from 0 to 5 just as the scale of the ratings. Usually the point where the F0.5 score is maximum is chosen as the threshold and it can be seen that the F0.5 score( green line) is maximum for a threshold value 3.5.
   
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/ROC%20curve.png" width = 700><p>
  
Usually on the ROC curve, a significant part of the area under the curve (AUC) should be above the straight line. The straight line indicates equiprobability. Random guesses basically.

It’s good to see that it’s a perfect curve predominantely above the line indicating the model is definitely doing well.

**Regularization parameter VS RMSE**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/regparam.png" width = 700><p> 
  
As it is usually seen in a RMSE VS Regularization parameter plot, for small values of lambda the model tends to overfit and gradually as we increase lambda the error shoots down and after a point, for continuously increasing lambda the model tends to underfit.
  
**Maxiters for Gradient Descent VS RMSE**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/maxiters.png" width = 700><p>
  
This is quite unusual. Usually the error is high during the initial iterations and the error goes down and plateaus after a certain number of iterations and after a period starts to increase again. But since this algorithm only has few values to learn from (sparse matrix) a small number of iterations of gradient descent are more than sufficient.
  
**Number of Features VS RMSE**
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/rankrmse.png" width = 700><p>
  
This clearly indicates that there are not many latent factors among the various restaurants considered in the dataset and trying to introduce more factors only leads to overfitting of data.
  
<a id='challenges'></a>  
## Challenges Faced
  
<p align="center"><img src = "https://github.com/Rahul-Vasan/ML-driven-Personalized-Gourmet/blob/main/img/hyperparam.png" width = 700><p>  
  
The biggest challenge was during the hyper parameter tuning phase. The model basically takes 4 parameters to fit the model, the regularization parameter, number of latent features, learning rate and the maxiterations for gradient descent. We used the gridsearch feature of pyspark to tune the model. What it does basically is fit the model for all possible combinations of values of these 4 parameters. So since we have 4 different parameters it would be a O(n^4) algorithm. As picture indicates the job ran for around 32 hours, and in the meantime we were facing all kinds of out of memory, out of java heap space and stackoverflow errors. Then after storing intermittent results and restricting the number of disk shuffles by checkpointing previously computed values into HDFS we were finally able to tune our model successfully.  
  
<a id='futurescope'></a>   
## Future Improvements
  
There is some scope for improvements in the project as listed:
1) Creation of a front end and back end to make this project a full fledged, modular and  fully functional dynamic application for users and businesses that would include personalization for the individual parties.
2) Adding a business statistics module for improvisation of the business and visualizations of  the trend over time.
3) A module to identify the most valuable customer to extend some kind of customer benefits that would be beneficial for the business growth.
4) Extending the sentiment analysis technique to remove abusive comments to ensure a safe space for the customers of all age groups and the mental health of the business owners.
5) Also the algorithm can be modified for faster and more personalized recommendations.
6) Technologies like ETL, Kafka, and effective caching mechanisms such as Redis and popular text search engines such as ElasticSearch can be introduced to handle dynamically changing data.
  
<a id='references'></a>
## References

1) https://link.springer.com/chapter/10.1007/978-3-642-01187-0_3
2) https://journalofbigdata.springeropen.com/articles/10.1186/s40537-017-0083-6
3) https://engineeringblog.yelp.com/2018/05/scaling-collaborative-filtering-with-pyspark.html
4) https://towardsdatascience.com/an-exhaustive-list-of-methods-to-evaluate-recommender-systems-a70c05e121de
5) https://www.proquest.com/docview/2656424902?pq-origsite=gscholar&fromopenview=true
6) https://github.com/statisticianinstilettos/recmetrics
7) https://www.researchgate.net/publication/221607379_Improving_the_Performance_of_Recommender_System_by_Exploiting_the_Categories_of_Products
8) https://link.springer.com/article/10.1007/s11257-021-09302-x
  
<a id='contact'></a>
## Contact Me

  Please feel free to contact me for anything in pertinance to the project. 
  
| Contact Method |  |
| --- | --- |
| Personal Email | rahulvasan30@gmail.com |
| School Email |   rs7671@nyu.edu |
| LinkedIn | https://www.linkedin.com/in/rahul-vasan/ |  
  
  
   
   
   
   
  
  
  
  
  

  
  
  
  
  
  
  
  
  

  
  
  
 
