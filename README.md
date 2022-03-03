# Ordinal probit model for ratings data
This is a python-, numpy-, jupyter-, and scipy-based re-implementation of the ordinal probit model described in "Analyzing ordinal data with metric models: What could possibly go wrong?" (Torrin M. Liddell and John K. Kruschke, 2018; https://www.sciencedirect.com/science/article/abs/pii/S0022103117307746). This has been implemented in R by the authors at https://osf.io/53ce9/.

The rational for using such a model is that models making metric assumptions about ordinal data (for example, ratings or Likert-type responses) often model the underlying data distribution poorly, and give non-trivial erroneous results after compression or hypothesis testing techniques that rely on metric assumptions.

In order to model the data better, latent Gaussians are fit for each response item, and thresholds fit along the domain of this Gaussian to define regions of probability mass that, when integrated, give the probability of a particular response. The means and standard deviations of these Gaussians are fit for each question, but the thresholds are fit across questions and take into account all data (the "meaning" of the scale is taken as independent of any particular question). 

In order to estimate the posterior distribution over these parameters, a simple MCMC approximation is taken. Here, we use Metropolis-Hastings.

This is a basic re-implementation, and does not contain the hierarchical model described in the paper. Almost all choices of distribution and hyperparameters are taken from the original paper, and all further details can be found there.

A basis example, fitting the model to the survey data, is provided in the `demo.ipynb` notebook. 

Ruairidh McLennan Battleday
-------------------------


TODO:
1. The posterior predictive probabilities for the movie data do not match those depicted in the original paper. Investigate.
2. Extend the repo to include the hierarchical model described in the paper and implemented in the R repo. 
