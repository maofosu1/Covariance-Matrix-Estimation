Shrinkage Covariance Estimation: LedoitWolf vs OAS vs OASD and Max-Likelihood
When working with covariance estimation, the usual approach is to use a maximum likelihood estimator, such as the EmpiricalCovariance. It is unbiased, i.e., it converges to the true (population) covariance when given many observations. However, it can also be beneficial to regularize it, in order to reduce its variance; this, in turn, introduces some bias. This example illustrates the simple regularization used in shrunk_covariance estimators. In particular, it focuses on how to set the amount of regularization, i.e., how to choose the bias-variance trade-off.

Here, we compare four approaches:

Cross-Validation: Setting the parameter by cross-validating the likelihood on three folds according to a grid of potential shrinkage parameters.
Ledoit-Wolf: A close formula proposed by Ledoit and Wolf to compute the asymptotically optimal regularization parameter (minimizing an MSE criterion), yielding the LedoitWolf covariance estimate.
OAS (Oracle Approximating Shrinkage): An improvement of the Ledoit-Wolf shrinkage, proposed by Chen et al. Its convergence is significantly better under the assumption that the data are Gaussian, particularly for small samples.
OASD (Oracle Shrinkage Approximation to Diagonal Target): A variant of the OAS method that shrinks the covariance matrix towards a diagonal target instead of the identity matrix.
To quantify estimation error, we plot the likelihood of unseen data for different values of the shrinkage parameter. We also show the choices by cross-validation, or with the LedoitWolf, OAS, and OASD estimates.

Note that the maximum likelihood estimate corresponds to no shrinkage and thus performs poorly. The Ledoit-Wolf estimate performs really well, as it is close to the optimal and computationally inexpensive. In this example, the OAS estimate is a bit further away. Interestingly, both approaches outperform cross-validation, which is significantly more computationally costly.

Results
The results will be displayed as a plot showing the negative log-likelihood on the test data for different values of the shrinkage parameter. The vertical lines indicate the choices made by the different methods (cross-validation, Ledoit-Wolf, OAS, and OASD). The real covariance likelihood is also shown as a reference.

By comparing the log-likelihood values, you can assess the accuracy and performance of each method. Generally, higher log-likelihood values indicate better accuracy on the test data.
