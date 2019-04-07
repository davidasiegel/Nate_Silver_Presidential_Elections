# Nate_Silver_Presidential_Elections

I wanted to know if the predicted win probability matches the actual win rate, as a function of time.  If Nate Silver's results are well-calibrated, then any prediction with a 60% win probability will ideally have roughly 60% wins.

How well do his predictions work?

First, let me apologize.  This is basically the first time I'm using github and my python notebook is poorly formatted.  Deal with it.  :)

## I'll walk you through the python notebook:

To see the results, click on "election_nate_silver.ipynb".  It's a python notebook with code and graphs, made very quickly without much editing.  It might take a couple seconds to load but it should be visible on any computer.

At the top, I load the data, downloaded from here: https://github.com/fivethirtyeight/checking-our-work-data.  I decided to only look at the 2018 election between Trump and Hilary.  And because Trump and Hilary's results were anticorrelated, I decided to look only at Trump's predicted win probability.  At the bottom of the file I looked at both.

I want to compare the actual win *rate* to the predicted win rate, so I can't look at individual predictions -- I have to look at *groups* of predictions.  To do that, I set up tranches of predicted win probabilities.  Any state for which a candidate is predicted to have a win probability between say 0.1 and 0.2, I put those predictions in one tranch and computed the win rate.  We're judging Nate on his forecasting ability so I threw out the "now-cast" data, which measures something different.  There are only 50 states, so most of these tranches don't have too many data points; I show a histogram in In[8], and there's a peak near 5 measurements per tranche but remember that many of these have two forecast types with the same result.  So the data will be noisy.  I continued on.

## Win Rate vs Predicted Rate

If you scroll through the python notebook, the graph at In[14] titled ("Win Rate vs Predicted Rate") shows the predicted win rate on the x-axis and the actual win rate on the y-axis.  Each data point is one probability tranche on one day.

I notice two trends here:

One, the outcome win rate was higher than the predicted win rate.  So there's bias -- Trump did better than predicted throughout the course of the polling data.  That's interesting but it's not really what I'm looking for right now.

Two, it seems as if the pink data is more narrowly distributed than the blue or orange, which would mean the early predictions did better than the later predictions.  Is this really true?

To check this, I made figure 2:

## R$^2$ Between Predicted and Win Probability as a Function of Time

This is really the graph I care about (at In[15]).  Each data point is the R^2 of a linear regression of actual vs predicted win rate, for each date in the graph above.  The x-axis is days from the election.  The y-axis is the R^2.  What we see is that the predictions actually get *worse* as we get closer to the election (further to the right on the graph)!  

I'm not sure why this happened here.  Maybe it's a Trump effect (everything became more predictable closer to the election date).  Maybe, the data became sparser in most tranches on later dates, which led to more noise.  If I combine a few more datasets I might get better statistics.  Maybe I made a dumb mistake somewhere in the code.

## Combining Data From All Candidates Gives Me Similar Results

I don't know what else to say about this, I was planning to leave it out because their results are highly correlated but I figured I'd throw it in at the end.  The bias in the win rate vs predicted rate graph appears to be lower because Clinton's bias points in the opposite direction and the two appear to cancel.  This is misleading, but it's also not really a problem.

## Concluding Thoughts

At first glance, it looks like Nate's predictions are pretty good, even as you go back in time.  However, there are definitely some weird things going on here so I don't totally trust my analysis.  I did this as quickly as I could, over the course of a couple hours on 4/6/19, so there are likely to be errors.

I would like to see Nate or Nassim or someone else make a more careful analysis along these lines.  The data is out there, you can see the data is nicely cleaned.  Get out there and do it.  I want to know if Nate's predictions are more accurate or less accurate as you go back in time.  They should be less accurate.  Maybe this election was an anomaly.

The glaring omission in the data posted by Nate Silver is that it doesn't provide confidence intervals.  It's fine if your predictions fluctuate wildly as long as your confidence intervals reflect that.  Ideally I would be checking the variance of the data against the confidence intervals.
