# (Week 9) Ex8: Anomaly Detection and Recommender Systems

`estimateGaussian.m`

```matlab
% ====================== YOUR CODE HERE ======================

mu = (sum(X) / m)';
mu_dup = repmat(mu', m, 1);
sigma2 = sum((X - mu_dup) .^ 2) / m;

% =============================================================
```

`selectThreshold.m`

```matlab
% ====================== YOUR CODE HERE ======================

predict = pval < epsilon;
tp = sum(predict & yval);
prec = tp / sum(predict);
rec = tp / sum(yval);
F1 = 2 * prec * rec / (prec + rec);

% =============================================================
```

`cofiCostFunc.m`

```matlab
% ====================== YOUR CODE HERE ======================

diff = X * Theta' .* R - Y;
J = sum(sum(diff .^ 2)) / 2 + lambda / 2 * (sum(Theta(:) .^ 2) + sum(X(:) .^ 2));
X_grad = diff * Theta + lambda * X;
Theta_grad = diff' * X + lambda * Theta;

% =============================================================
```
