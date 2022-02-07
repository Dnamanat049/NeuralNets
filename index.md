## NBAI Project

# Introductory Paragraph

Watching an NBA game with others, the first question that usually comes up is "who are you rooting for?". Even if you are not particularly disposed to either of the teams, it is easy to pick one and become enamored with the game to the point where you are genuinely sad or upset if "your" team loses. While not always safe or ethical, many tend to enhance this enjoyment by making small bets among friends. Taken on a larger scale, this small-scale betting has become a phenonemon with companies like DraftKings and FanDuel that enable this behavior on a countrywide scale becoming worth billions of dollars. Given how popular this subculture has become, our team believes it would be a fun challenge to create a model that is able to "win" at this game.

For this project, I would like to create a neural network model that takes information about two NBA teams, the Vegas betting odds for that matchup, and decides whether or not to make a bet on one of the teams. This model would be trained on data that hopefully would include information about indidivual players, the stadium, the coach, and other factors relevant to a team's performance in a game. The model would output a % chance that one of the teams will win, and then (possibly a separate, simpler model) will evaluate whether to make a bet on that team given the over/under on the odds.

The project is similar to the past project FIFAI, however it adds the element of betting and changes the perspective to NBA teams, where the feasibility of prediction might be entirely different. As a fan of the NBA, a lifelong basketball player, and an utter novice to the world of betting, I believe this would be a fun project to undertake and apply my newfound knowledge of neural networks.

# Background Paragraph

- Difficult part: factoring in the odds portion of it (the model would determine where there was mispricings)

# Transition Paragraph

- Hypothetical shortcomings:

# Details Paragraph

- Technical: it will be difficult to get the data to fit into our model

# Assessment Paragraph

- Model that is more than 50% accurate in predicting matchups
- Can pinpoint price mismatches
- Can generate winnings

# Ethics Sweep

Should we even be doing this?

We believe that this project is largely safe and ethical—in fact our team views our mission as a means to level a gambling playing field that is unfairly biased in favor of bookies and gambling organizations that have robust resources and statistical methods, and one that is biased against the average bettor. However, we recognize a handful of problems that might arise from this project: 
1. An individual with a gambling problem might see the win % predictions as a justification for their gambling behavior. Given the numbers behind their bet, they might see their actions as "reasonable" and "logical" rather than a random, intuition based gamble. We by no means endorse this behavior—while this model is able to output a number and dollar amount for betting, it is really just another form of "intuition" that is the result of amalgamating our team members' biases in choosing what data to train the model on, what variables to choose, and what the process for making bets should be. This system is no more robust or objective than the average bettor's intuition, given that it has our own biases included.
2. This model could be used by bookies and gambling organizations to generate even more accurate odds than they already offer, further tilting the scale against the average bettor. We recognize that bookies and gambling organizations are much more likely than a casual bettor to be actively searching for cutting-edge methods to improve their profits, and as such this model may end up being used for the opposite of its intentions.

What might be the accuracy of a simple, non-ML alternative?

Bookies calculate odds using a combination of sports analysts, mathematical models, and a variety of adjacent data (how much money is being bet on the underdog, for example, might affect the odds by forcing bookies to balance the spread so that they can protect their downside). Much of this work is outsourced to third-party odds-generating firms, hence the uniformity of the odds that one tends to see between sports betting sites. Average bettors rely on much simpler methods, often intuition, to make their bets. However, a selection of bettors specialize in sports gambling and have their own sophisticated models and methods to predict outcomes.

On the accuracy of bookies' odds, lead gambling expert Professor Leighton Vaughan Williams of the Betting Research Unit at Nottingham Trent University reports that odds shorter than 2-1 are frequently accurate. However, the long-shot bets that reflect true underdogs become progressively more unreliable as the odds drop below ~14-1, with the true chances of a win being either much lower than the odds would suggest (https://www.sciencefocus.com/science/how-accurate-are-the-odds-quoted-by-bookmakers/).

What processes will we use to handle appeals/mistakes?

In a betting model like the one proposed, an appeal/mistake will result in a loss of money and as such we take this scenario very seriously. Firstly, we will suggest betting small amounts so as to not encourage risky behavior that would lead to dangerous losses. Secondly, we would like to factor our appeals/mistakes back into the model so as to make it more accurate. The wonderful element of sports is that games are almost always happening, and so even our incorrect guesses will become part of a valuable treasure trove of data that will be replenished everyday. Finally, if the model is consistently creating losses at any point, our team will reexamine the data used to train the model to see if it is still valid. For example, the game of basketball has changed dramatically over the past 20 years as the 3-pointer has become the centerpoint of many teams offenses. A model from 20 years ago would not take this into account, and as such it would be much less accurate.

How diverse is our team?

Our team is diverse in athletic background, gambling knowledge, career interests, life backgrounds, and so much more. In terms of demographics, we recognize that while we are racially and culturally diverse, we are all men and as such are lacking a key component of any truly diverse team. However, we will strive to make a product and interface that is attractive and user-friendly to bettors of all identities.



# Goals:
Create a model that is more than 50% accurate.

Have the model be able to pinpoint mispriced matchups.

Make a model that can generate winnings.

Create an inuitive interface for the application.


