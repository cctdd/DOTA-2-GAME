# DOTA-2-GAME
![dota2_social](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/d51dc34b-b538-4eff-85b4-6bd7dbf26650)
### INTRODUCTION ###
Dota 2 game is a computer game involving 2 teams of 5 players each. Each team defends itself against enemy attack from the opposing team. Each player chooses a unique hero and there are 113 possible set of heros to choose from. Each hero has a particular set of feature or characteristics that make it special and unique to other set of heros. Once a player from any team chooses a particular hero, no other player can choose that hero. 

### Data Presentation ###
The data evaluated in this project consist of 117 feautures in total. Each feature are distributed as follows
+ **Outcome column** : This shows the outcome of the game. It is 1 if team 1 wins and -1 if team 2 wins
+ **Cluster ID** : This relate to the location at which the game was played
+ **Game Mode** : This represents the specific mode or rule set being used in a game, such as all pick, all random, or other game variations. This feature describes the rules and restrictions that  #players follow during the game.
+ **Game Type**: : The ”GAME-TYPE” feature represents different types of games in Dota 2, such as ranked, unranked, tournament matches, or other specific game modes. This feature captures the overall nature or purpose of the game being played.
+ **113 columns** : the remaining 113 columns represent each possible set of heros that can be chosen from and in each column, 1 signifies an hero has been used by the first team, -1 signifies that it has been used by the second team and 0 signifies it was not used by any team in that particular game.

### Problem Statement ###
![win-lose-ss-1920](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/58bd7d20-76f0-4b3f-b793-178f81859d56)
The aim of this work is to train several models with the training dataset and test the accuracy of these trained model on the testing dataset. Basically, after training these models, a test on how accurate these models are in predicting which team wins the game using 116 of the the features provided, then checking the result of this test against the original **outcome** of the game. 

### Data Sourcing ###
The dataset was obtained from the [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/367/dota2+games+results) It contained an already seperated training and testing datasets as follows
+ **Testing dataset** : 10295 rows and 117 attributes, no missing values in each row and columns
+ **Training dataset** : 92650 rows and 117 attributes, no missing values in each row and columns

## Data Transformation and Cleaning ###
The dataset was transformed in the following ways: 
+ Data was at first investigated to check for missing values, missing rows or missing columns
+ The column were labelled in the following ways, the first four (4) columns were labelled `Outcome`, `Cluster ID`, `Game mode` and ` Game type` respectively. The remaining 113 columns representing the heros was labelled numerically from 1 to 113..

### Exploratory Analysis ### 
An Exploratory analysis of the data was done using Microsoft PowerBI. The analysis was made on the contribution of Game Mode and Game Type on the Outcome of the game. The result is as shown in the image below: 

![Visualization3_page-0001](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/598de10e-c6b7-4e4b-864a-ca8266017ea2)
It can be observed that Game mode which has only three categories (1,2,3) is such that Game mode 1 has the least influence to the outcome of the game and is also only played alongside Game Type 6 and 9. Game mode 2 has the most played population and it is the only mode that was played with all the possible Game Types followed by Game mode 3. 

### Unsupervised Learning ### 
K-Means Clustering was performed on the dataset to try to see a relationship between the features.Silhouette scores was also calculated to check if K is right.  The K value was varied between 5 to 20. The visualization of K-means and Silhouette score at K=5 and at K=20 obtained as shown below respectively:
![siholet 5](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/a30b5c18-f5d1-4122-9a4d-e78caa54c55a)

![Silholet](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/79caade2-60b1-4209-b7d8-c3c15850bdab)

The Silhouette scores obtained at K=5 and K=20 are both near zero ( `0.0026` and `0.0057` ) it indicates overlapping or ambiguous clusters. It means that the samples could be assigned to multiple clusters with similar distances. Which suggests a lack of distinct separation between clusters and may indicate that the clustering algorithm didn't perform well in separating the data points or there are no distinct separation between the data points.

## Supervised Learning ##
In this project, three different models was used to perform the predictive analysis on the dataset given. Each model was evaluated with the incusion of its accuracy scores and a reliability evaluation of each model in terms of its suitability was also considered.

### 1. Logistic Regression Model ###
 Prior to applying the Logistic regression model, a gridsearch was performed to obtain the best `hyperparameters` out of the hyperparameters: 
 + penalty
 + l1_ratio
 + solver
 + tol
 After the GridSearch, the model was trained on the training set and tested on the test set.  The confusion matrix for the predicted outcome of the testing dataset is as shown below;

| Testing Dataset      | Predicted positive           | Predicted Negative  |
| ------------- |:-------------:| -----:|
| **Actual Positve**      | 2475|2317 |
|    **Actual Negative**    | 1819     |  3683 |

Also the confusion matrix for the predicted outcome of the training dataset is as shown below;

| Training Dataset      | Predicted positive           | Predicted Negative  |
| ------------- |:-------------:| -----:|
| **Actual Positve**      |22546 |21322 |
|    **Actual Negative**    | 15653     |  33129 |


#### Evaluating quality of model on the Test Data ####
Below are the most informative evaluation of the model's quality on the test data;
+ Accuracy Score: `0.598` : This indicates a fair accuracy of the model in predicting correctly the outcome of the games in the testing dataset.
+ Precision : The table gives the precision of the model in predicting that team 1 wins or loses the game;

Outcome Value    | Precision 
 -------------|-------------|
-1 | 0.58 
 1 | 0.61 

 #### Evaluating quality of model on the Training Data ####
 + Accuracy Score: `0.601` : This indicates a fair accuracy of the model in predicting correctly the outcome of the games in the training dataset.
+ Precision : The table gives the precision of the model in predicting that team 1 wins or loses the game;

Outcome Value    | Precision 
 -------------|-------------|
-1 | 0.59 
 1 | 0.61 

Considering the values of the balanced accuracy and the accuracy score, one can conclude that there is no overfitting in the logistic regression model.

#### Feauture Importance ####
From the model, the first most important or influencing features and the last 5 most important features are plotted and shown below, these features are ranked based on the coefficient associated with each of them in the linear regression model. Hence the magnitude of the coefificient reflects the strenght of the relationship between the specific feature and the target variable. 
![feauture importance](https://github.com/cctdd/DOTA-2-GAME/assets/122665014/9628394f-394d-4edc-ad37-94bd7aa16ddf)

### 2.  










