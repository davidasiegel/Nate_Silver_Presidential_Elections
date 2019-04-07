# Nate_Silver_Presidential_Elections

I wanted to know if the predicted win probability matches the actual win rate, as a function of time.  If Nate Silver's results are well-calibrated, then any prediction with a 60% win probability will have roughly 60% wins.  Ideally, not 70% and not 50%.

How well do his predictions work?

First, let me apologize.  This is basically the first time I'm using github and my data formatting also isn't ideal.  Feel free to contact me with suggestions.

## I'll walk you through the python notebook:

At the top, I load the data.  I decided to only look at the 2018 election between Trump and Hilary.  And because Trump and Hilary's results were anticorrelated, I decided to look only at Trump's predicted win probability.  At the bottom of the file I looked at both.

I want to compare the actual win *rate* to the predicted win rate, so I can't look at individual predictions -- I have to look at *groups* of predictions.  To do that, I set up tranches of predicted win probabilities.  Any state for which a candidate is predicted to have a win probability between say 0.1 and 0.2, I put those predictions in one tranch and computed the win rate.  I decided to keep all forecast types because I couldn't make a decision.  There are only 50 states, so most of these tranches don't have too many data points; I show a histogram in In[8], and there's a peak near 10 measurements per tranche but remember that most of these have multiple forecast types with the same result.  So the data will be noisy.  I continued on.

If you scroll down through the python notebook, the first graph at In[13] titled ("Win Rate vs Predicted Rate") shows the predicted win rate on the x-axis and the actual win rate on the y-axis.

