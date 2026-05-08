# Ridge Regression L2 - Homework Assignment 1

## Academic Context

This project was developed as part of the *Programming for FinTech* course at the Shanghai Advanced Institute of Finance (SJTU).


## Assignment Instructions

- Try out the polynomial Ridge regression using some function other than \( y = \sin(x) + \epsilon \) or \( y = x^3 + \epsilon \).
- Use GridSearchCV or manually try several different values for the regularization strength parameter \( \lambda \) (alpha in Ridge), also try different polynomial degrees.
- Write a brief report about what you find.


# I/ Methodology

To try out the polynomial Ridge regression, I started by creating my own dataset. I used a simple
quadratic formula, y = 15x² + x, and then added a layer of realistic randomness (noise) to mimic
real-world data. I generated 200 data points and split them into a training set (70% of the data)
to teach the model and a testing set (the remaining 30%) to see how well it could generalize to
new, unseen information. I manually tested several different values for the regularization
strength parameter α (0.0002, 0.002, 0.02, 0.1, 0.5, 0.95, 2.5, 5) alongside various polynomial
degrees (1, 2, 3, 5, 8, 9, 10) to identify the optimal model configuration.


# II/ Results and analysis

The results showed that simple models were too basic because they systematically underfit the
data and couldn't capture the underlying curve. The most complex models, as expected, overfit
because they performed brilliantly on the training data but poorly on the test data, meaning they
had memorized the noise instead of learning the true pattern.

After all my testing, the optimal model configuration was identified as polynomial of degree 8
with a very small regularization strength (α = 0.0002). This model achieved a training MSE of
89.4089 and a test MSE of 108.6612, corresponding to an R² score of 0.9555 on the training set
and 0.9222 on the test set.

The fact that the performance on the test set was only slightly worse than on the training set
(the test error was about 21% higher) is a strong sign that the model generalized well. It learned
the real quadratic relationship without being tricked by the noise I had added.


# III/ The role and effect of regularization in Ridge regression

This project really highlighted the power of regularization. Ridge regression works by gently
penalizing the model for having overly large coefficients, which is what causes overfitting. In
this case, the optimal regularization was very weak because the degree 8 polynomial was
already a good fit for the underlying quadratic pattern. The regularization's main job was just
to keep the model stable without holding it back.

I also saw the downside of being too cautious. When I set the regularization strength (α) too
high, it made the model too simple, causing it to underfit and fail to capture the curve, regardless
of the polynomial degree I used.


# IV/ Conclusion

This exercise confirmed that there's no substitute for carefully tuning a model's parameters. By
methodically testing different options, I found a Ridge Regression model that successfully
identified the hidden quadratic trend in a noisy dataset. Overall, the study highlights Ridge
regression as a powerful tool enabling accurate and generalizable models even with noisy data.


## Technologies Used
- Python
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
