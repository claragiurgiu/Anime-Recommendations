# Anime-Recommendation-Systems
<p align="center">
    <img width="460" height="300" src="https://api.time.com/wp-content/uploads/2020/12/best-anime-series-on-netflix-2.jpg">
</p>

**Author**: Clara Giurgiu


## Overview

This project aims to build an anime recommendation system for new members and current subscribers of an anime streaming service. New members can use a content-based approach to receive recommendations based on a show they may have watched or heard of previosuly. For current subscribers, collaborative filtering is used by comparing the users' ratings and returning shows similar users have rated similarly. 

## Business Understanding

The anime industry is a rapidly growing market, with new shows being released all the time. This can make it difficult for anime fans to find new shows to watch that they will enjoy. Additionally, most streaming services do not offer personalized recommendations, which can lead to users wasting time scrolling through an endless list of shows that they are not interested in.
With this project, I aim to build a recommendation system that will help anime fans discover new shows that they will enjoy. The recommendation system will use a variety of factors to make recommendations, including the user's past viewing history, the user's ratings of other shows, and the user's genre preferences. 
This recommendation system  will give a curated list to its users based on content preference and similar user's pick that will save time and provide a superb experience both novel and familiar to users. 

## Data Understanding

I used data scraped from MyAnimeList.net, which includes several features of the anime show, as well as user ratings. The data is available for download from [Kaggle.com](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database/versions/1?resource=download). The main dataset is a CSV file containing a list of 12,294 shows with features such as title, genre, and number of episodes. The second dataset has 7,813,737 rows of users rating different anime shows.

## Data Preparation

The datasets used for this project were sourced from Kaggle and there was not a significant amount of cleaning needed before modeling. 
Most of the cleaning and preparation consited of removing nulls, duplicate entries and removing irrelevant columns. 

## Methods and Models

For the recommendation systems in this project, I used a content-based approach and a collaborative filtering approach. 
One of the drawbacks of recommendation engines is the cold-start issue for new users. To overcome this, I built two content-based systems. One uses the genre of a show to return shows with similar genre and the second option uses other features of the show such as genre, number of episodes and score to return similar shows. 

**Content Based - Synopsis**

![Content Based 1](./Images/content_based_sy.PNG)

**Content Based - Similarities**

![Content Based 2](./Images/content_based_sim.PNG)

The choice of model based on content will depend on what the user is more interested in. Option one can be used if the user wants to watch more of the same show they enjoyed, such as sequels if there are any, or movies that fill the gaps between seasons. 
If the user is looking for something new, but in the same vein as a comfort show such as Naruto, option 2 will recommend different shows that share some of the themes and elements in the show but with new characters and stories. 

**Collaborative Filtering**

For collaborative filtering, I established a baseline using a normal predictor that predicts a random rating based on the distribution of the dataset. I then iterated through several Singular Value Decomposition (SVD) models, from which the final model was chosen. 
Singular value decomposition (SVD) is a matrix factorization technique that decomposes a matrix into two matrices of non-negative values. The first matrix, called the basis matrix, represents the underlying factors that explain the data. The second matrix, called the coefficient matrix, represents the weights of each factor in each data point.

SVD can be used to generate latent features by decomposing the sparse user-item interaction matrix into two smaller and dense matrices of user and item entities. The basis matrix represents the latent features of the users, while the coefficient matrix represents the weights of each latent feature for each item.

The latent features can then be used to make predictions. For example, if a user has not rated an item, the model can use the latent features of the user and the item to predict how the user would rate the item.
I also tried a non-negative matrix factorization (NMF) model, but it was not very successful. NMF is another dimensionality reduction technique that decomposes a matrix into two matrices of non-negative values. However, NMF is not as effective as SVD for collaborative filtering.

Finally, I tried a Singular Value Decomposition plus plus (SVD++) model. SVD++ is an extended version of SVD that works mostly on users' implicit and explicit ratings for the item. SVD++ was more successful than NMF, but it was not as successful as SVD.

The final model was chosen based on its accuracy and performance. 

In conclusion, the SVD model was the most successful model for collaborative filtering. The model was able to generate latent features and make accurate predictions for a wide range of users and items.

![Model Comparison](./Images/model_comparison.png)




### Conclusions

In conclusion, the collaborative filtering recommendation system is able to predict estimated ratings with an error of 1.5 and return recommendations that a user will most likely rate highly based on their previous rating patterns and similar users' ratings of the recommendations.
Overall, collaborative filtering is a powerful technique that can be used to recommend anime to users. However, it is important to be aware of the limitations of the approach and to use it in conjunction with other techniques, such as content-based filtering, to provide the best possible recommendations.
Some of the limitations of collaborative filtering:
 - Data sparsity: Collaborative filtering algorithms rely on users having rated a large number of items. However, in practice, many users only rate a small number of items. This can lead to inaccurate recommendations.
    -  One way to overcome data sparsity is to use content-based filtering in conjunction with collaborative filtering. Content-based filtering algorithms recommend items to users based on the content of the items that the user has rated. This can help to fill in the gaps in the data that is available for collaborative filtering.
 - Cold start: Collaborative filtering algorithms cannot recommend items to users who have not yet rated any items. This can be a problem for new users or users who have recently changed their interests.
    -  A potential solution to the cold start problem is to use a hybrid approach that combines collaborative filtering with content-based filtering. In this approach, the algorithm first uses content-based filtering to recommend items to the new user. The algorithm then uses collaborative filtering to refine the recommendations by taking into account the ratings of other users.
 - Bias: Collaborative filtering algorithms can be biased by the ratings of other users. For example, if a user only rates popular items, the algorithm will recommend other popular items to that user, even if the user might prefer less popular items.
    - One way to overcome bias is to use a variety of collaborative filtering algorithms and to combine their results. This can help to reduce the impact of any individual algorithm's biases.

## Next Steps
* Scrape more recent data
* Improve the algorithms by trying new search parameters
* Hybrid system
* Use differrent modeling algorithms


## Repository Structure
```
├── Data
├── Images
├── .gitignore
├── Collaborative_Filtering.ipynb
├── Content_Based.ipynb
├── EDA_notebookipynb
├── LICENSE
├── README.md
└── Recommendation_System_Presentation.pdf