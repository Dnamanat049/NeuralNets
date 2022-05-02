# NBAI Project

## INTRODUCTION

"$10 the Knicks lose." Watching an NBA game with others, questions like this about small-scale betting frequently appear as a means of making the event more entertaining for the group. Even if you are not particularly disposed to either of the teams, it is easy to pick one and become enamored with the game to the point where you are genuinely sad or upset if "your" team loses. While not always safe or ethical, it certainly draws you into the event in a way that few other sports-adjacent activites can. Taken on a larger scale, this small-scale betting has become a phenonemon with companies like DraftKings and FanDuel that enable this behavior on a countrywide scale becoming worth billions of dollars. Given how popular this subculture has become, our team believes it would be a fun challenge to create a model that is able to win at this "game."

For this project, we would like to create a neural network model that takes information about two NBA teams, the Vegas betting odds for that matchup, and decides whether or not to make a bet on one of the teams. This model will be trained on data that includes information about indidivual players, the stadium, the coach, and other factors relevant to a team's performance in a game. The model would output a % chance that one of the teams will win, and then a separate, simpler model will evaluate whether to make a bet on that team given the over/under on the odds.

One of the most difficult parts of this problem is factoring in the odds portion to find mispriced bets. Unlike other sports prediction algorithms, we are not aiming to simply predict the outcome of the game based on historical data. We are attempting to factor in odds that bookmakers have placed on games into the prediction algorithm to see if bets are worth placing or not. The main goal of a bookie is to make money by expanding their margins to the point where they know they will make money regardless of how many bets are placed on one team or the other. We are first going to have to figure out what the odds are of each team winning and then compare this to what the betting odds are to see which bets have the most hidden value. Doing this would allow users of our algorithm to exploit mispriced bets at a higher rate than normal.

From a top-down view, this is a very difficult task. For one, sports betting companies have their own data science teams, and use ML algorithms to generate odds. The challenge is to create a model that performs with higher accuracy than the those owned by the betting companies. There are two directions we can take to beat their models: one is to get more accurate or extensive data, the other to develop a model that is more advanced than theirs (as in one that is constructed better). Since we do not know the approaches of sports betting companies, it is difficult to know what their weaknesses are. Therefore, we will plan on accruing/using as much data as we can, and use every tool at our disposal to train our model accurately. 

From a details-oriented view, we will also be facing several challenges. In terms of data, while the gathering process will be fairly straightforward with so many online resources, choosing which statistics and averages to use as inputs will not be so simple. There is potential for noise amongst these troves of data, and so we want to isolate inputs that actually have predictive power. In addition, the values that are important could change from season to season, month to month, or even game to game. Take three pointers, which has become progressively more important to a team's success since they first debuted in 1979 (dramatically so over the past decade). Consider as well injuries, which might make it difficult to rely heavily on individual players' stats given that the makeup of teams has the potential to change from day to day. Apart from data, another challenge we will face is in the form of choosing proper hyperparameters and the right activation function to achieve optimal accuracy. The best past projects have plateaued around the ~75% mark. While this may be the best that is achievable with the data we have due to the randomness of sports, we believe that we can push this upper limit by choosing proper hyperparameters and an activation function that is well-suited for this particular problem. To validate our results, we will set aside a validation set of the data on which to test our model. In the long run, we would ideally like to see how the model performs on games that have yet to been played, given that that is its purpose.

We ultimately would like our model to be able to predict matchups with at least 50% accuracy, and one that is able to pinpoint price mismatches in Vegas odds. Fundamentally, we want our model to be able to generate winnings. We also hope to create an intuitive interface for the application.

## Related Works

 The problem of NBA prediction is a topic that has already been extensively explored. In research by the Air Force Institute of Technology, [Loeffelholz, Bednar, and Bauer](https://www.degruyter.com/document/doi/10.2202/1559-0410.1156/html), used 4 different types of neural networks to predict NBA outcomes, feed-forward, radial basis, probabilistic, and generalized regression networks. In addition, a fusion neural network was used that combined the results of the aforementioned networks via a Bayesian belief network and probabilistic neural network fusion. The database consisted of box scores from the 2007-8 season, including 620 games in the training set and 30 in the validation set. The feed-forward neural network performed best, achieving a 74.33% accuracy rating based on just 4 predictors: FG% and FT% for the home and away teams. This incredible result based on just a tiny set of predictors is incredible and gives us high confidence that we will be able to improve on this model.
 
 In perhaps a more relevant project, a [group of undergraduate students](https://towardsdatascience.com/predicting-the-outcome-of-nba-games-with-machine-learning-a810bb768f20) at the University of Pennsylvania created a random forest model to predict the outcome of NBA games. With similar experience, resources, and time, we thought this project to be particularly relevant to our endeavors in terms of gauging what we might be able to accomplish. This team scraped their data from BasketballReference.com and engineered five features: 1. ELO rating; 2. Average team stats over past 10 games; 3. Average player stats over past 10 games; 4. Player season performance; 5. Player Efficiency Ratings (PER). Upon analysis of the features, they decided to train the model on ELO ratings and recent average team stats. The model they generated ended up performing with a test accuracy rating of 67.15%, which our group would like to use as a benchmark to surpass.
 
In a similar [project](https://towardsdatascience.com/building-my-first-machine-learning-model-nba-prediction-algorithm-dee5c5bc4cc1), an independent data scientist created a sports analysis betting algorithm, which he later tranformed into a service allowing subscription-based access to the NBA prediction API's he created. This model serves as an interesting contrast to the use of neural nets, as Fayad (the creator of the model) used an entirely different method, namely a support vector machine, for predictions. The relevant aspect to our project was namely the process of collecting data, which is of course integral to any succesful model. Fayad used data web-scraped using the package Selenium from the website [basketball-reference.com](basketball-reference.com). The model ended up with a 72% accuracy. 

Another interesting [paper](https://ieeexplore.ieee.org/abstract/document/4492661) used back-propagation and conjugate-gradient methods on data including (but not limited to) game location, players present, team ranking, performance in previous games, total points scored so far in the season for and against. They actually trained the algorithms on four different sports, including Australian rugby, football, Super Rugby, and English football. Their results, while beggining with low accuracy, improved quickly. Prediction of results in the 2007 Super 14 season reached about 68%, exceeding professional expert prediction. The algorithm was also entered into the "TopTipper" competition in the same year, and ended the season as the best predictor entered. 

One final [article](https://www.thesportsgeek.com/sports-betting/strategy/understanding-value/) helped provide a basis for the more betting-oriented aspects of our project, specifically understanding the mechanics of betting and setting up an algorithm to determine when is most ideal to bed. This article explains how to decide whether or not you should bet on a given sports game, once you have calculated (or guessed!) a percentage likelihood that a team will win. Using the mathematical concept of implied probability, the article explains how to take gambling odds and convert them into a percentage chance that the bookmaker is assuming a given team has to win. If the percentage likelihood that you have calculated on your own is higher than the bookmaker's implied percentage, then you should place a bet and will theoretically make money. If your odds are lower, you should not place the bet (or you should take the other side of the bet!).

## Methods

For accomplishing this task, we will break down our methods into three categories: our applicable software, our datasets, and our methods of analysis. In terms of software, we will use [Beautiful Soup](https://beautiful-soup-4.readthedocs.io/en/latest/) and [Selenium](https://www.selenium.dev) to scrape datasets from basketballreference.com. Utilizing these packages will smooth the scraping process, and it is a technique that prior researchers have followed. To construct the neural network, we will be using the robust library [PyTorch](https://pytorch.org) to thoroughly train our model and enhance its predictive capabilities. In terms of datasets, we will use the scraped data from basketballreference.com, along with historical betting data from [kaggle](https://www.kaggle.com) and historical ELO ratings constructed by [fivethirtyeight.com](fivethirtyeight.com).

In terms of building the actual model, prior research points towards using a feed-forward neural network to achieve the hightest accuracy ratings, and as such that is the model that we have chosen for this task. A feed-forward neural network is one in which there are several layers consisting of nodes where the information only moves forward through the network from input nodes to the output nodes with no cycles present throughout the network. We chose to use this type of model because of its ability to process non-linear, tabular data and create approximation functions for predicting values based on historical data. Our input data will be structured with the observational unit being a single game, with that game being analogous to a vector of floating-point values consisting of the data we have scraped, the betting data, and the team's ELO rating. The data that we have trained the model on comprises betting odds from various websites for regular season NBA games from 2012 through 2018. In total there are roughly 13,000 games that are in the training data alone. In order to predict if it is worth it to place a bet on a game, we decided that the best prediction to make would be for one of the betting websites and compare what our prediction is to what the original odds they placed on the game were. The variable we ended up attempting to predict with our model was Bovada_ML, or the money line odds set by bovada.lv. Because it would be difficult to get our predictions to be exactly correct each time, we set a range so that if our prediction was within 10 of the desired value (in either direction), it would be deemed as correctly set by the oddsmakers. However, if the prediction and the desired output did not line up, then we know the line was incorrectly set by the oddsmakers and therefore is a bet that should be taken advantage of by bettors. For example, if the line was set at -300 for one team to win and our model predicted anything from -290 to -310, it would be considered a correctly set line. If our model predicts a value outside of this range though, we would notify the user that this line has not been set properly and is therefore a bet that should be taken to exploit an error made by the oddsmakers. With this in mind, we determined that the best format for the output of our model would be a yes/no indication of whether or not the bet is a good one to make, as well as the desired and predicted values.

## Results

In our first model, we trained our model for 200 epochs, used 2 hidden layers with 6 neurons in the first layer and 7 in the second, a Tanh activation function, SGD optimizer, and had an adaptive learning rate so as to soften feedback as the loss converges. We were able to achieve an analog prediction error, or loss, of 2.477 which is decent, but in order to attain better prediction accuracy, we would need to get this down to a lower value.

When we ran our model on our testing data, which was seperate from the data we trained the model with, we adjusted the comparison between the desired and prediction value to not check if they are exactly the same, but to see if the difference between the prediction and desired value were within 10 of each other. If they ended up being within this range, this prediction was classified as a correct prediction.

The results from this first model yielded 61.26% accuracy, which was higher than the initial threshold of 50% we set for our model. The reason the inital threshold was set at this level was that we wanted our model to perform better than simply flipping a coin to choose the winner of a game based on pervious data. We figured that acheiving anything greater than a predictive accuracy of 50% would be a success in terms of our goals for this project.

![tanh+sgd](https://user-images.githubusercontent.com/60167964/166334510-686f3e4a-07cb-48e0-9133-737a216de423.png)

In the next trial, we made some slight adjustments to the specifications of our model. Instead of using the SGD optimizer, we use the Adam optimizer. All of the other specifications of the model are kept the same. Our loss converges to 2.879, which is not much higher than our first model. We also reduced the maximum number of training iterations to 70 because the value for loss was converging after this amount of repetitions. However, we see that this is much less accurate than the first model because this model achieves an overall predictive accuracy of 35.54%.

![adam+tanh](https://user-images.githubusercontent.com/60167964/166334546-6f506d24-93fa-442e-8445-75bbe1fa1536.png)

In our third model, we adjust the specifications of the model to have the ReLU activation function and the SGD optimizer. This yields the best results so far, as the loss comes in at 1.755 and the prediction accuracy is a robust 76.98%, which is much higher than both of the other variations of this model before.

Here is a plot that shows the loss per iteration of our most successful classifier:

![final_loss_plot](https://user-images.githubusercontent.com/60167964/165652609-def8b4b3-165c-4a9a-93ee-b4a697474908.png)

In the fourth variation of the model that we tested, we used the ReLU activation function and the Adam optimizer. We were able to achieve a loss of 2.469, but our prediction accuracy was approximately 59.7%, which is not quite as good as some other variations of the model. In this model, we had to reduce the number of iterations that we trained our model for to 60 because the optimization was converging after this amount of time.

![adam+relu](https://user-images.githubusercontent.com/60167964/166334591-cd79d38f-fa99-418c-91b9-efe9b5636701.png)


Overall, the third model definitely performed the best of ones that we tried. The ReLU and SGD optimizers seem to be the best two options for activation function and optimizer when running the model with the settings that we ran it with. We did not try adding any dropout or batch normalization laters, but this could be done in the future to optimize our model even further for heightened performance.

## Discussion

The main purpose of this project was to see if we could build a model that would give bettors any sort of advantage over bookies when placing bets on NBA games based off of historical betting data from previous NBA games. We succeeded in creating a model that is able to make predictions based on this data by predicting the Bovada ML for a game based on betting lines set by other websites, meaning there is potential for profit if this model is utilized appropriately. There are currently two datasets that we are deciding between using for our model.
 
### Dataset #1
 
  The first dataset we found that could possibly be used for our model is one that includes NBA data from the regular season and playoff games as well as odds for the past decade. This data has been scraped from various sources on the internet.
  
  Link: [https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2018-19](https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2018-19)
  
### Dataset #2
 
  The second dataset we found that could be used for our model is very similar to the first dataset in the sense that it also includes results from several years of regular season and playoff results from the NBA. It also includes the betting data in various formats, such as money line and spread as well as the betting totals in for the various books in the dataset.
  
  Link: [https://www.kaggle.com/ehallmar/nba-historical-stats-and-betting-data?select=nba_betting_totals.csv](https://www.kaggle.com/ehallmar/nba-historical-stats-and-betting-data?select=nba_betting_totals.csv)

However, there are some shortcomings to the model we have created.

First off, our model is only taking into account data from NBA seasons between 2012 and 2018. Despite there being thousands of games worth of data that our model has been trained on from these years, performances of teams from year to year vary greatly in a sport like basketball. Realistically, previous years of data may not have the most significant impact on the current year’s betting odds or predictions for games, but to include them in the data can be valuable because trends can be spotted in how lines are being set by oddsmakers.

Additionally, the only prediction that our model is making is on the money line odds for a game. On one hand, this provides good inside into the accuracy of the oddsmakers because our program can make a prediction about the Bovada money line and compare it to the desired value. However, with there being several different ways to bet on a game, such as the spread, over/under, teasers, and several others. Since we are only predicting the money line, it is not going to be very useful for individuals placing bets on other types of lines that are set by odds makers.

In comparison to related works that attempted to create similar programs, our model performed about the same. At our model’s best, we were able to achieve approximately 76% accuracy for predictions, but that was within a range that our prediction fell according to what the desired output was supposed to be. It seems that it is difficult to outperform the oddsmakers at an extremely high rate because despite there being trends in basketball, there are still factors that are unpredictable when attempting to create a model such as we have.

As our results suggest, the ReLU activation function seems to outperform Tanh in almost all scenarios. The advantages of the ReLU function when compared to the Tanh function lie in the fact that there are no negative values available when using ReLU due to them being converted to 0’s if they happen to be negative, the maximum threshold values are infinity allowing the output prediction accuracy to be its absolute maximum value, and the overall speed is quicker than other activation functions. Overall, the ReLU function is a better activation function to use in terms of our model, and such is proven in our results.

## Reflection

If we were to do this project again, one thing we would do differently would be to make it so our model can predict any of the possible lines that the user wants to predict based on their input. This would make the model more applicable to all kinds of bettors, including those that are interested in more than just the Bovada money line. Also, it would be interesting to incorporate other kinds of data into our model to see if that would have any effect on the prediction accuracy and overall results of our model.

One way we could continue our work from this project in the future to expand upon what we've already done would be to have this model run daily on current NBA statistics. To do this, we would need to make a web scraper that collects the most current betting odds on basketball games happening every day, feeding these into the model we created, running the model based on what type of line the bettor wants to bet on, then finally notifying the bettor whether or not they should place said bet based on the prediction that our model makes. Being able to turn this project into an app would be ideal as well, making it readily available for consumers everywhere.

## Ethics Sweep

### Should we even be doing this?

We believe that this project is largely safe and ethical—in fact our team views our mission as a means to level a gambling playing field that is unfairly biased in favor of bookies and gambling organizations that have robust resources and statistical methods, and one that is biased against the average bettor. However, we recognize a handful of problems that might arise from this project: 
1. An individual with a gambling problem might see the win % predictions as a justification for their gambling behavior. Given the numbers behind their bet, they might see their actions as "reasonable" and "logical" rather than a random, intuition based gamble. We by no means endorse this behavior—while this model is able to output a number and dollar amount for betting, it is really just another form of "intuition" that is the result of amalgamating our team members' biases in choosing what data to train the model on, what variables to choose, and what the process for making bets should be. This system is no more robust or objective than the average bettor's intuition, given that it has our own biases included.
2. This model could be used by bookies and gambling organizations to generate even more accurate odds than they already offer, further tilting the scale against the average bettor. We recognize that bookies and gambling organizations are much more likely than a casual bettor to be actively searching for cutting-edge methods to improve their profits, and as such this model may end up being used for the opposite of its intentions.

### What might be the accuracy of a simple, non-ML alternative?

Bookies calculate odds using a combination of sports analysts, mathematical models, and a variety of adjacent data (how much money is being bet on the underdog, for example, might affect the odds by forcing bookies to balance the spread so that they can protect their downside). Much of this work is outsourced to third-party odds-generating firms, hence the uniformity of the odds that one tends to see between sports betting sites. Average bettors rely on much simpler methods, often intuition, to make their bets. However, a selection of bettors specialize in sports gambling and have their own sophisticated models and methods to predict outcomes.

On the accuracy of bookies' odds, lead gambling expert Professor Leighton Vaughan Williams of the Betting Research Unit at Nottingham Trent University reports that odds shorter than 2-1 are frequently accurate. However, the long-shot bets that reflect true underdogs become progressively more unreliable as the odds drop below ~14-1, with the true chances of a win being either much lower than the odds would suggest (https://www.sciencefocus.com/science/how-accurate-are-the-odds-quoted-by-bookmakers/).

### What processes will we use to handle appeals/mistakes?

In a betting model like the one proposed, an appeal/mistake will result in a loss of money and as such we take this scenario very seriously. Firstly, we will suggest betting small amounts so as to not encourage risky behavior that would lead to dangerous losses. Secondly, we would like to factor our appeals/mistakes back into the model so as to make it more accurate. The wonderful element of sports is that games are almost always happening, and so even our incorrect guesses will become part of a valuable treasure trove of data that will be replenished everyday. Finally, if the model is consistently creating losses at any point, our team will reexamine the data used to train the model to see if it is still valid. For example, the game of basketball has changed dramatically over the past 20 years as the 3-pointer has become the centerpoint of many teams offenses. A model from 20 years ago would not take this into account, and as such it would be much less accurate.

### How diverse is our team?

Our team is diverse in athletic background, gambling knowledge, career interests, life backgrounds, and so much more. In terms of demographics, we recognize that while we are racially and culturally diverse, we are all men and as such are lacking a key component of any truly diverse team. However, we will strive to make a product and interface that is attractive and user-friendly to bettors of all identities.

### Is our data valid for its intended use?

We are assuming that our data will be valid for its intended use because it will include results of games as well as what the betting odds were on those games in the first place.

### What bias could be in our data?

One of the main biases that could exist in our data would be in the odds themselves. Bookmakers attempt to balance all the bets places on every outcome so as to ensure that they are making profit no matter what the outcome of the game is. This process is know as the vig, or vigorish. Overrounding also takes place, which is the actual percentage over 100% that a book is for a certain event that is taking place. Leading up to certain sporting events, bookmakers will adjust the lines to make bets look more attractive so as to maximize profits. This is where the bias comes in because a teams odds of winning a game are not accurately reflected in the betting odds placed on the game.

### How could we minimize bias in our data and model?

One way we could minimize the bias in our data would be to take only the initial odds that were released on an event, not any of the odds that were altered leading up to the start of it, so as to obtain the most accurate betting odds for that event. This way, we know exactly what bookmakers initially thought the odds would be when releasing them to the public.

### How should we “audit” our code and data?

The best way to audit our code/data would be to make sure that all of the odds we are using in our model are those that were the first to come out about the event (reflecting the most accurate initial impression of the event from bookmakers) and removing and altered odds from the data. This way we know we are not including any data that could be used to entice various bettors into making unwise bets.

### Do we expect different errors rates for different sub-groups in the data?

In this case, it is possible we encounter different error rates for different sub-groups, as a result of imperfect data. Our data will revolve around many factors, including individual player history, team statistics, prior game outcomes, stadiums, etc., and unfortunately, this data is uneven between men and women's sports. As a result, it is likely that error rates will be higher for women's sports betting. This is an unfortunate and frustrating possbility. It illustrates that the betting and sport industry is highly gendered. We will attempt to alleviate these issues by collecting as much data is available for underrepresented groups, however, we acknowledge that this will not neccessarrily ammend the issue. 

### What are likely misinterpretations of the results and what can be done to prevent those misinterpretations?

A possible misinterpretation of the results may be that our generated accuracy predictions are better than betting companies. Another possible misinterpretation is that the accuracies suggest a bet. For instance, if we predict the chances team A wins as 75%, it might be interpreted that someone should take that bet. However, the decision to bet must take into account the difference in predicted chances between our algorithm and the betting company. If we publish this algorithm in any locations, we will prevent this misinterpretation by including descriptions of the algorithm and its intended implementations, as well as disclaimers surrounding its efficacy. 

### How might we impinge individuals' privacy and/or anonymity?

We do not forsee this impinging individuals' privacy or anonymity. Since it will use information provided publicly, which team members consent to, it will not utilize information not previously consented to.
  
## References
 
[https://towardsdatascience.com/building-my-first-machine-learning-model-nba-prediction-algorithm-dee5c5bc4cc1?gi=ab8c91263c91](https://towardsdatascience.com/building-my-first-machine-learning-model-nba-prediction-algorithm-dee5c5bc4cc1?gi=ab8c91263c91)
 
 [https://www.cs.dartmouth.edu/~lorenzo/teaching/cs174/Archive/Winter2013/Projects/FinalReportWriteup/michelle.w.shu/](https://www.cs.dartmouth.edu/~lorenzo/teaching/cs174/Archive/Winter2013/Projects/FinalReportWriteup/michelle.w.shu/)
 
 [https://www.degruyter.com/document/doi/10.2202/1559-0410.1156/html](https://www.degruyter.com/document/doi/10.2202/1559-0410.1156/html)
 
 [https://ieeexplore.ieee.org/abstract/document/4492661](https://ieeexplore.ieee.org/abstract/document/4492661)

[https://towardsdatascience.com/predicting-the-outcome-of-nba-games-with-machine-learning-a810bb768f20](https://towardsdatascience.com/predicting-the-outcome-of-nba-games-with-machine-learning-a810bb768f20)

[https://www.thesportsgeek.com/sports-betting/strategy/understanding-value/](https://www.thesportsgeek.com/sports-betting/strategy/understanding-value/)

[https://pypi.org/project/beautifulsoup4/](https://pypi.org/project/beautifulsoup4/)

[https://pytorch.org/](https://pytorch.org/)

[https://www.selenium.dev/](https://www.selenium.dev/)

[https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2013-14](https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2013-14)

[https://www.basketball-reference.com](https://www.basketball-reference.com)

[https://datahub.io/five-thirty-eight/nba-elo](https://datahub.io/five-thirty-eight/nba-elo)



