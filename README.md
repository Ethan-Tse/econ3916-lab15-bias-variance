# econ3916-lab15-bias-variance
The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be
Objective

I used a simulated world with a known true curve to see how model flexibility trades bias against variance, and how to choose a polynomial degree without spare data.

Methodology
Split prediction error into bias squared and variance, using 200 fresh samples at each of six polynomial degrees.
Compared training error with error on 2,000 new points for degrees 1 to 15, and found the degree where the held-out error was lowest.
Chose a degree by 5-fold cross-validation and looked at how much the error varied from fold to fold.
Used nested cross-validation to check whether the smallest cross-validation error is a fair estimate of the error on new data.
Wrote a function, kfold_mse(), that gives the k-fold cross-validation error for any degree and number of folds, and used it with 10 folds.
For the take-home challenge, fitted a degree-40 polynomial and then a minimum-norm fit with far more coefficients than points.
Key Findings
Variance was 0.0180 at degree 5 and 0.0994 at degree 15, while bias squared had already fallen to 0.0036 at degree 5.
The held-out error was lowest at degree 5.
5-fold cross-validation chose degree 4, with a CV MSE of 0.1401, and the spread across folds was small only at degrees 4 and 5.
The nested cross-validation estimate was 0.2070, which is larger than 0.1401, so the smallest CV error was too optimistic.
With 10 folds, the CV MSE was 0.1409 for degree 4 and 0.1457 for degree 5.
Challenge: a degree-40 fit had a held-out MSE of 155.0326. With the minimum-norm fit, the held-out error was huge near the point where coefficients equal points (degree 51 on my grid), then fell to 0.3185 at degree 991, which is still above the 0.2202 of the degree-5 fit.
