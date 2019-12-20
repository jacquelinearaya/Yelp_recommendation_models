# Personalization, Fall 2019, Final Project
## Contributors
### Jacqueline Araya - ja3076@columbia.edu - ja3076
### Oscar Jasklowski - ovj2101@columbia.edu - ovj2101

<br>

## How to review the contents of this repository:
1. We recommend starting with this README file. Here, we present our business objectives, outline our technical approach, and summarize our results for all models.
2. Next, we encourage the reader to review the attached iPython notebooks. They are organized as follows:

    1. Data Pipeline - Code for preparing raw data, analyzing various user- and business-attributes, and code for comparing the performance of all models side-by-side.
    2. Recommendation Models - Implementations (many from scratch) of all our recommendation algorithms. This is divided into "Baseline Models" (simpler models from early in the semester, intended to serve as benchmarks) and "Proposed Models" (more sophisticated models based on content presented later in the semester).

<br>

## Background and Project Objective

Recommendation systems are quickly gaining popularity with companies seeking a way to predict user preferences based on past experience. Specifically, these recommendation systems typically aim to maximize the chance that a user will engage with a recommended product. Recommendation tasks appear in a wide range of business contexts, from e-commerce to social networking. 

In the scope of this report we present and compare several solutions for the specific challenge of building a production-grade recommendation system using the Yelp Open Dataset from the 2019 challenge. 

More precisely, the Yelp Dataset is a vast dataset of business reviews left by users of the Yelp platform. We’ll use this data to develop an array of models that aim to predict the last review of a business for each user in the dataset (on a scale of 1 to 5 stars). To evaluate the performance of our models, we will compare the ratings our models predict against the actual rating the user left for that business. Depending on the business objective, there are a number of ways to define a successful prediction (and a successful model). We present our business objective and model evaluation framework below.

## Business Problem and High-Level Objectives

Building an effective recommendation system is challenging because, in addition to requiring a familiarity with algorithmic recommendation techniques, making good predictions depends on business domain knowledge. Knowing the specifics of your product and its users is key to designing and building an effective recommendation system for all subsets of users and businesses in the dataset.

To that end, there is a tremendous variety of users and businesses in the dataset. For example, there are thousands of businesses categories, and each business can fall into several categories. Additionally, we have users with over one thousand reviews, and users with a single review, and these users are scattered across thousands of cities. Intuition suggests that a one-size-fits-all solution will not provide effective recommendations for this variety of users and businesses. 

With these diversity considerations in mind, our main business objective is to understand which models work well for various subsets of our users and businesses. That is, if model A performs well for new users, model B performs well for businesses from niche categories, and model C performs well for popular users and items, we can devise a model switching strategy to serve optimal recommendations for as many users as possible. 

Of course, this begs the secondary question: what exactly is a “good” recommendation? In this context, we define a good business recommendation for a user as one that has a similar rank (relative to other businesses) as the user’s actual rank for that business. In other words, we hypothesize that we risk losing users if we recommend a business that the user really dislikes, but we can retain a user if a tolerable (even if mediocre) business is recommended. Our “coverage” metric seeks to minimize these terrible recommendations. We will compare models on the basis of this metric.

In summary, aim to segment users and businesses, evaluate the performance of our models with respect to these segments on a meaningful metric, and ultimately propose a model-switching strategy for our business.

## Detailed Objectives

The general objective of this project is to design, build and evaluate recommendation models that predict the stars a Yelp user gives to business. More accurately, to predict the stars for the last business the user went, considering only active users (users with 5 or more reviews in the dataset).

Our specific objective, as outlined above, is to evaluate the performance of several models on various subsets of the data, optimizing for “coverage” (defined as avoiding a highly negative recommendation experience for a user). This metric is more meaningful for our business case.

Finally, some of the models we test will incorporate contextual data from business and users in the Yelp dataset, including business categories. From the second half of the semester, we will experiment with the following categories of models:
Deep-learning-based recommendation models
Content-based recommendation models

## Data Exploration
