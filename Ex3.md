# (Week 4) Ex3: Multi-class Classication and Neural Networks

`lrCostFunction.m`

```matlab
% ====================== YOUR CODE HERE ======================

h = sigmoid(X * theta);
J = 1 / m * (-y' * log(h) - (1 - y)' * log(1 - h)) ...
      + lambda / 2 / m * theta(2: end)' * theta(2: end);
grad(1) = 1 / m * X(:, 1)' * (h - y);
grad(2: end) = 1 / m * X(:, 2: end)' * (h - y) ...
                      + lambda / m * theta(2: end);

% =============================================================
```

`oneVsAll.m`

```matlab
% ====================== YOUR CODE HERE ======================

initial_theta = zeros(n+1, 1);
options = optimset('GradObj', 'on', 'MaxIter', 50);
for i = 1:num_labels
  all_theta(i, :) = fmincg(@(t)(lrCostFunction(t, X, (y == i), lambda)), ...
                          initial_theta, options);
end

% =========================================================================
```

`predictOneVsAll.m`

```matlab
% ====================== YOUR CODE HERE ======================

[val, p] = max(X * all_theta', [], 2);

% =========================================================================
```

`predict.m`

```matlab
% ====================== YOUR CODE HERE ======================

X = [ones(m, 1), X];
a2 = [ones(m, 1), sigmoid(X * Theta1')];
[val, p] = max(sigmoid(a2 * Theta2'), [], 2);

% =========================================================================
```
