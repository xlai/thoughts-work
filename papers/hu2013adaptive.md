---
aliases: hu2013adaptive
tags: adi
title: Adaptive dose insertion in early phase clinical trials
date created: Tuesday, October 18th 2022, 10:22:14 pm
date modified: Wednesday, October 19th 2022, 9:13:58 am
---
# [Adaptive dose insertion in early phase clinical trials](https://ascopubs.org/doi/full/10.1200/JCO.21.02493)

## Summary

The ADI method is developed to insert new doses during a dose-finding trial when none of the pre-specified doses are 'acceptable'. The concept is based on calculating an activation rule for invoking dose insertion for each pre-specified dose, and extrapolating a new dose based on a dose-toxicity response model.

## Formulation

### Compute activation rules

Given $\mathbf{n} = (n_1, \dots, n_d)$ and $\mathbf{y} = (y_1, \dots, y_d)$, where $n_i$ and $y_i$ are the number of treated patients and number of [[DLT]] events at dose $i, i = 1,\dots,d$, including pre-specified and newly-inserted doses, we define indicators as
$$
m_i = \mathbf{I}[Pr\{p_i < p_T < p_{i+1} | \mathbf{y}, \mathbf{n}\} > C], i = 0,\dots, d
$$
where $\mathbf{I}(.)$ is the indicator function and $C\in(0,1)$ is a cut-off value controlling how stringent should the dose-insertion be. In other words, a value close to zero leads to higher chance of dose insertion; whereas a value close to one would indicate a lower probability.

### Estimate new dose(s)

If $m_i = 1$ for some $i$, implement the inverse dose-toxicity model to calculate the new dose $\hat{x}$. If $m_i = 1$ for more than one dose, assign the next cohort to the lowest estimated new dose for safety and discard the other estimates.

## Statistical consideration

### Posterior distribution of $p_i$
The dose-insertion method is independent of the statistical model being implemented in the trial 
for estimating the posterior distribution of the toxicity probabilities. 
The author suggested a Bayesian approach, assuming the likelihood function is in the form of 
$\prod_i^{d} p_i^{y_i} (1 - p_i)^{n_i - y_i}$ given observed $(\mathbf{n}, \mathbf{y})$ . 
If $p_i \sim^{i.i.d} Beta(0.5, 0.5)$ a priori, the posterior of $p_i$ is given by $p_i \sim^{i.i.d} Beta(0.5 + y_i, 0.5 + n_i - y_i)$.

The author also recommended a quadratic logistic regression model for calculating the new dose claiming that it allows for more flexible dose-reponse curves.

### Choice of cut-off

Regarding the choices of C, the author carrried out a sensitivity analysis and recommended a cut-off between 0.5 and 0.8 for practical guidance.

### Model mis-specification

Simulation studies are granted when the dose-response model is misspecified. However the activation function acts as a safeguard in case the proprosed dose is too toxic: ADI would quickly insert a lower dose or switch to prespecified dose for the subsequent cohort. In practice, *a maximum dose increment in dose extrapolation should be set* to ensure safety. 
