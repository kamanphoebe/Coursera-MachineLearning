# (Week 3) Ex2: Logistic Regression


`plotData.m`

```matlab
% ====================== YOUR CODE HERE ======================

plot(X(y==0, 1), X(y==0, 2), 'ko', 'MarkerFaceColor', 'y', 'MarkerSize', 7);
plot(X(y==1, 1), X(y==1, 2), 'k+', 'LineWidth', 2, 'MarkerSize', 7);
xlabel('Exam 1 score');
ylabel('Exam 2 score');

% =========================================================================
```

`sigmoid.m`

```matlab
% ====================== YOUR CODE HERE ======================

sz = size(z);
if sz(1) == 1 && sz(2) == 1,
  g = 1 / (1 + exp(-z));
else,
  g = 1 ./ (1 + exp(-z));
end;

% =============================================================
```

`costFunction.m`

```matlab
% ====================== YOUR CODE HERE ======================

h = sigmoid(X * theta);
J = 1 / m * (-y' * log(h) - (1 - y)' * log(1 - h));
grad = 1 / m * X' * (h - y);

% =============================================================
```

`predict.m`

```matlab
% ====================== YOUR CODE HERE ======================

p = sigmoid(X * theta);
p(p >= 0.5) = 1;
p(p < 0.5) = 0;

% =========================================================================
```

`costFunctionReg.m`

```matlab
% ====================== YOUR CODE HERE ======================

last_idx = size(theta, 1);
h = sigmoid(X * theta);
J = 1 / m * (-y' * log(h) - (1 - y)' * log(1 - h)) ...
      + lambda / 2 / m * theta(2: last_idx)' * theta(2: last_idx);
grad(1) = 1 / m * X(:, 1)' * (h - y);
grad(2: last_idx) = 1 / m * X(:, 2: last_idx)' * (h - y) ...
                      + lambda / m * theta(2: last_idx);

% =============================================================
```
