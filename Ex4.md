# (Week 5) Ex4: Neural Networks Learning

This assignment is a little bit tricky while dealing with the matrix/vector calculation. Checking the dimension carefully will be quite helpful for it.

`nnCostFunction.m`

- Part 1.3 aims to implement the cost function and it requires recoding the labels as vectors. The 1st part of the code below has done this through a for loop, yet I wonder whether it can be replaced by a one-line code using some indexing skills. I have tried something pythonic like `label(:, y)=1` but it didn't work for Octave.
- Part 2.3 focuses on backpropagation, which can be implemented through the 2nd part of the code below. The guideline reminds us to skip or remove $\delta_0^{(2)}$ in step 4. But you should actually do that earlier in step 3, or the dimension of matrices involved would not be compatiable.

```matlab
% ====================== YOUR CODE HERE ======================

% Part 1
a1 = [ones(m, 1), X];
a2 = [ones(m, 1), sigmoid(a1 * Theta1')];
h = sigmoid(a2 * Theta2');
label = zeros(m: num_labels);
for i = 1:m
  label(i, y(i)) = 1;
end
J = 1 / m * sum(sum(-label .* log(h) - (1 - label) .* log(1 - h))) ...
    + lambda / 2 / m * (sum(sum(Theta1(:, 2:end) .^ 2)) ...
		+ sum(sum(Theta2(:, 2:end) .^ 2)));


% Part 2
Delta1 = zeros(size(Theta1_grad));
Delta2 = zeros(size(Theta2_grad));
for i = 1:m
  a1 = [1, X(i, :)];
  z2 = Theta1 * a1';
  a2 = [1; sigmoid(z2)];
  z3 = Theta2 * a2;
  a3 = sigmoid(z3);
  delta3 = a3 - label(i, :)';
  delta2 = Theta2(:, 2:end)' * delta3 .* sigmoidGradient(z2);
  Delta1 = Delta1 + delta2 * a1;
  Delta2 = Delta2 + delta3 * a2';
end

Theta1_grad = 1 / m * Delta1;
Theta2_grad = 1 / m * Delta2;


% Part 3
Theta1_grad(:, 2:end) = Theta1_grad(:, 2:end) + lambda / m * Theta1(:, 2:end);
Theta2_grad (:, 2:end) = Theta2_grad(:, 2:end) + lambda / m * Theta2(:, 2:end);

% =========================================================================
```

`sigmoidGradient.m`

```matlab
% ====================== YOUR CODE HERE ======================

g = sigmoid(z) .* (1 - sigmoid(z));

% =============================================================
```
