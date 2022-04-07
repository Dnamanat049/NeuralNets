# NBAI Project

## INTRODUCTION

"$10 the Knicks lose." Watching an NBA game with others, questions like this about small-scale betting frequently appear as a means of making the event more entertaining for the group. Even if you are not particularly disposed to either of the teams, it is easy to pick one and become enamored with the game to the point where you are genuinely sad or upset if "your" team loses. While not always safe or ethical, it certainly draws you into the event in a way that few other sports-adjacent activites can. Taken on a larger scale, this small-scale betting has become a phenonemon with companies like DraftKings and FanDuel that enable this behavior on a countrywide scale becoming worth billions of dollars. Given how popular this subculture has become, our team believes it would be a fun challenge to create a model that is able to win at this "game."

For this project, we would like to create a neural network model that takes information about two NBA teams, the Vegas betting odds for that matchup, and decides whether or not to make a bet on one of the teams. This model will be trained on data that includes information about indidivual players, the stadium, the coach, and other factors relevant to a team's performance in a game. The model would output a % chance that one of the teams will win, and then a separate, simpler model will evaluate whether to make a bet on that team given the over/under on the odds.

One of the most difficult parts of this problem is factoring in the odds portion to find mispriced bets. Unlike other sports prediction algorithms, we are not aiming to simply predict the outcome of the game based on historical data. We are attempting to factor in odds that bookmakers have placed on games into the prediction algorithm to see if bets are worth placing or not. The main goal of a bookie is to make money by expanding their margins to the point where they know they will make money regardless of how many bets are placed on one team or the other. We are first going to have to figure out what the odds are of each team winning and then compare this to what the betting odds are to see which bets have the most hidden value. Doing this would allow users of our algorithm to exploit mispriced bets at a higher rate than normal.

From a top-down view, this is a very difficult task. For one, sports betting companies have their own data science teams, and use ML algorithms to generate odds. The challenge is to create a model that performs with higher accuracy than the those owned by the betting companies. There are two directions we can take to beat their models: one is to get more accurate or extensive data, the other to develop a model that is more advanced than theirs (as in one that is constructed better). Since we do not know the approaches of sports betting companies, it is difficult to know what their weaknesses are. Therefore, we will plan on accruing/using as much data as we can, and use every tool at our disposal to train our model accurately. 

From a details-oriented view, we will also be facing several challenges. In terms of data, while the gathering process will be fairly straightforward with so many online resources, choosing which statistics and averages to use as inputs will not be so simple. There is potential for noise amongst these troves of data, and so we want to isolate inputs that actually have predictive power. In addition, the values that are important could change from season to season, month to month, or even game to game. Take three pointers, which has become progressively more important to a team's success since they first debuted in 1979 (dramatically so over the past decade). Consider as well injuries, which might make it difficult to rely heavily on individual players' stats given that the makeup of teams has the potential to change from day to day. Apart from data, another challenge we will face is in the form of choosing proper hyperparameters and the right activation function to achieve optimal accuracy. The best past projects have plateaued around the ~75% mark. While this may be the best that is achievable with the data we have due to the randomness of sports, we believe that we can push this upper limit by choosing proper hyperparameters and an activation function that is well-suited for this particular problem. To validate our results, we will set aside a validation set of the data on which to test our model. In the long run, we would ideally like to see how the model performs on games that have yet to been played, given that that is its purpose.

We ultimately would like our model to be able to predict matchups with at least 50% accuracy, and one that is able to pinpoint price mismatches in Vegas odds. Fundamentally, we want our model to be able to generate winnings. We also hope to create an intuitive interface for the application.

## Methods

For accomplishing this task, we will break down our methods into three categories: our applicable software, our datasets, and our methods of analysis. In terms of software, we will use Beatiful Soup and Selenium to scrape datasets from basketballreference.com. Utilizing these packages will smooth the scraping process, and it is a technique that prior researchers have followed. To construct the neural network, we will be using the robust library PyTorch to enhance our model's learning capabilities. In terms of datasets, we will use the scraped data from basketballreference.com, along with historical betting data from Kaggle.com and historical ELO ratings constructed by fivethirtyeight.com.

In terms of building the actual model, prior research points towards using a feed-forward neural network to achieve the hightest accuracy ratings, and as such that is the model that we have chosen for this task. Our input data will be structured with the observational unit being a single game, with that game being analogous to a vector of floating-point values comprised of the data we have scraped, the betting data, and the team's ELO rating. Our output will be a floating-point number representing a percentage chance of the home team winning a given game. 

## Results

PUT RESULTS HERE. QUESTIONS TO CONSIDER:

- What was the training accuracy that we achieved? What was the test accuracy that we achieved? We should break this down by different types of neural networks that we tried, and different input data that we used. What were our results with and without our optimization techniques?

## Discussion

- What data you will present:
 - Data is presented in the results section
- Interpretation/evaluation of data
 - We should break this down both by accuracy of model and potential for profit. We should consider shortcomings of the model (ex. if a star player gets injured, the model likely won't pick up on that for a few games). We should consider why certain models did better than others (feed-forward is likely the best performer because it is suited for input data with a vector shape). 
- How does your work compare to others:
 - Compare the accuracy of our results to non-machine learning approaches, like expert opinion or betting odds. We should also compare our results to the other papers that we reviewed. We should talk about what we did differently (used different data, different models, incorporated a betting aspect).
- How to prove your point
 - Don't fully understand this one
- Important concepts learned/implemented
 - Maybe talk about how we tried to implement several different models, walk through how we did each of them in a tutorial style?


## Related Works

 The problem of NBA prediction is a topic that has already been extensively explored. In research by the Air Force Institute of Technology, [Loeffelholz, Bednar, and Bauer](https://www.degruyter.com/document/doi/10.2202/1559-0410.1156/html), used 4 different types of neural networks to predict NBA outcomes, feed-forward, radial basis, probabilistic, and generalized regression networks. In addition, a fusion neural network was used that combined the results of the aforementioned networks via a Bayesian belief network and probabilistic neural network fusion. The database consisted of box scores from the 2007-8 season, including 620 games in the training set and 30 in the validation set. The feed-forward neural network performed best, achieving a 74.33% accuracy rating based on just 4 predictors: FG% and FT% for the home and away teams. This incredible result based on just a tiny set of predictors is incredible and gives us high confidence that we will be able to improve on this model.
 
 In perhaps a more relevant project, a [group of undergraduate students](https://towardsdatascience.com/predicting-the-outcome-of-nba-games-with-machine-learning-a810bb768f20) at the University of Pennsylvania created a random forest model to predict the outcome of NBA games. With similar experience, resources, and time, we thought this project to be particularly relevant to our endeavors in terms of gauging what we might be able to accomplish. This team scraped their data from BasketballReference.com and engineered five features: 1. ELO rating; 2. Average team stats over past 10 games; 3. Average player stats over past 10 games; 4. Player season performance; 5. Player Efficiency Ratings (PER). Upon analysis of the features, they decided to train the model on ELO ratings and recent average team stats. The model they generated ended up performing with a test accuracy rating of 67.15%, which our group would like to use as a benchmark to surpass.
 
In a similar [project](https://towardsdatascience.com/building-my-first-machine-learning-model-nba-prediction-algorithm-dee5c5bc4cc1), an independent data scientist created a sports analysis betting algorithm, which he later tranformed into a service allowing subscription-based access to the NBA prediction API's he created. This model serves as an interesting contrast to the use of neural nets, as Fayad (the creator of the model) used an entirely different method, namely a support vector machine, for predictions. The relevant aspect to our project was namely the process of collecting data, which is of course integral to any succesful model. Fayad used data web-scraped using the package Selenium from the website [basketball-reference.com](basketball-reference.com). The model ended up with a 72% accuracy. 

Another interesting [paper](https://ieeexplore.ieee.org/abstract/document/4492661) used back-propagation and conjugate-gradient methods on data including (but not limited to) game location, players present, team ranking, performance in previous games, total points scored so far in the season for and against. They actually trained the algorithms on four different sports, including Australian rugby, football, Super Rugby, and English football. Their results, while beggining with low accuracy, improved quickly. Prediction of results in the 2007 Super 14 season reached about 68%, exceeding professional expert prediction. The algorithm was also entered into the "TopTipper" competition in the same year, and ended the season as the best predictor entered. 

One final [article](https://www.thesportsgeek.com/sports-betting/strategy/understanding-value/) helped provide a basis for the more betting-oriented aspects of our project, specifically understanding the mechanics of betting and setting up an algorithm to determine when is most ideal to bed. This article explains how to decide whether or not you should bet on a given sports game, once you have calculated (or guessed!) a percentage likelihood that a team will win. Using the mathematical concept of implied probability, the article explains how to take gambling odds and convert them into a percentage chance that the bookmaker is assuming a given team has to win. If the percentage likelihood that you have calculated on your own is higher than the bookmaker's implied percentage, then you should place a bet and will theoretically make money. If your odds are lower, you should not place the bet (or you should take the other side of the bet!).
 

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

 
## Dataset(s)
 
 There are currently two datasets that we are deciding between using for our model.
 
### Dataset #1
 
  The first dataset we found that could possibly be used for our model is one that includes NBA data from the regular season and playoff games as well as odds for the past decade. This data has been scraped from various sources on the internet.
  
  Link: https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2018-19
  
### Dataset #2
 
  The second dataset we found that could be used for our model is very similar to the first dataset in the sense that it also includes results from several years of regular season and playoff results from the NBA. It also includes the betting data in various formats, such as money line and spread as well as the betting totals in for the various books in the dataset.
  
  Link: https://www.kaggle.com/ehallmar/nba-historical-stats-and-betting-data?select=nba_betting_totals.csv
  
 ### References
 
 https://towardsdatascience.com/building-my-first-machine-learning-model-nba-prediction-algorithm-dee5c5bc4cc1?gi=ab8c91263c91
 
 https://www.cs.dartmouth.edu/~lorenzo/teaching/cs174/Archive/Winter2013/Projects/FinalReportWriteup/michelle.w.shu/
 
 https://www.degruyter.com/document/doi/10.2202/1559-0410.1156/html
 
 https://ieeexplore.ieee.org/abstract/document/4492661

https://towardsdatascience.com/predicting-the-outcome-of-nba-games-with-machine-learning-a810bb768f20

https://www.thesportsgeek.com/sports-betting/strategy/understanding-value/

https://pypi.org/project/beautifulsoup4/

https://pytorch.org/

https://www.selenium.dev/

https://www.kaggle.com/erichqiu/nba-odds-and-scores?select=2013-14

https://www.basketball-reference.com

https://datahub.io/five-thirty-eight/nba-elo



