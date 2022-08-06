# (Week 2) Ex1: Linear Regression

The first assignment is an easy one :)

`computeCost.m` / `computeCostMulti.m`

```matlab
% ====================== YOUR CODE HERE ======================

J = 1 / 2 / m * (X * theta - y)' * (X * theta - y);

% =========================================================================
```

`gradientDescent.m` / `gradientDescentMulti.m`

```matlab
% ====================== YOUR CODE HERE ======================

theta = theta - alpha / m * ((X * theta - y)' * X)';

% ============================================================
```

`featureNormalize.m`

```matlab
% ====================== YOUR CODE HERE ======================

mu = mean(X, 1);
sigma = std(X);
X_norm = (X - mu) ./ sigma;

% ===========================================================
```

`normalEqn.m`

```matlab
% ====================== YOUR CODE HERE ======================

theta = pinv(X' * X) * X' * y;

% ============================================================
```

`ex1_multi.m`

```matlab
%% ================ Part 2: Gradient Descent ================

% Estimate the price of a 1650 sq-ft, 3 br house
% ====================== YOUR CODE HERE ======================

price = [1, ([1650 3] - mu) ./ sigma] * theta;

% ============================================================

%% ================ Part 3: Normal Equations ================

% Estimate the price of a 1650 sq-ft, 3 br house
% ====================== YOUR CODE HERE ======================

price = [1 1650 3] * theta; 

% ============================================================
```
