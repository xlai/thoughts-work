---
aliases: devlin2021
tags: adi
title: Phase I clinical trials in adoptive T-cell therapies
date created: Monday, October 17th 2022, 10:13:17 pm
date modified: Monday, October 17th 2022, 10:13:45 pm
---
# [Phase I clinical trials in adoptive T-cell therapies](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9400039/)

## Summary 

This manuscript presents three solutions to account for the information obtained from patients receiving a fraction of the assigned dose. 
The motivation of this work arises from T-cell therapies, whereby it is normal to have patients receiving doses that are less than the assigned doses due to manufacturing process.

In order to avoid unnecessary replacement of patients not receiving the assigned doses, they showed three solution involving around weighting the received doses by its two adjacent doses $x_j^{-}$ and $x_j^{+}$.  In particular, solution 3, coined _fractionated dose level attribution_ (FDLA-CRM), has theoretical support from large sample theory. 

## Formulation

The idea is similar to [[TITE-CRM]] that, for each patient $j$ receiving dose $d_j$, weights $w_j = (x_j^+ - x_j)/(x_j^+ - x_j^-)$  and $1 - w_j$ were used to re-assign the contribution of $x_j$ to $x_j^{+}$ and $x_j^{-}$ respectively, and the likelihood after observing patient $j$ can be written as
$$
\begin{align}
&L(\beta; \Omega_j) = L^{+}(\beta; \Omega_j)\cdot L^{-}(\beta; \Omega_j) \quad \text{where}\\
&L^{+}(\beta; \Omega_j) = \prod_{i=1}^{j} \{ \psi(x_i^+, \beta ) \}^{w_i Y_i} \{ 1-\psi(x_j^+,\beta) \}^{w_i(1-Y_{i,n+1})} 
\end{align}
$$
and where $L^-(\beta; \Omega_j)$ is of the same form as $L^+(\beta; \Omega_j)$ but with $1 - w_i$ in place of $w_i$ and $x_i^-$ in place of $x_i^-$.
