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
