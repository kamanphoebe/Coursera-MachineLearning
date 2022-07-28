# (Week 7) Ex6: Support Vector Machines

`gaussianKernel.m`

```matlab
% ====================== YOUR CODE HERE ======================

sim = exp(-1 * (x1 - x2)' * (x1 - x2) / 2 / sigma / sigma);

% =============================================================
```

`dataset3Params.m`

```matlab
% ====================== YOUR CODE HERE ======================

% The optimal value I found.
C = 1;
sigma = 0.1;

% The cross validation for searching the optimal value of C and sigma.
%{
all_C = [0.01; 0.03; 0.1; 0.3; 1; 3; 10; 30];
all_sigma = [0.01; 0.03; 0.1; 0.3; 1; 3; 10; 30];
min_error = 1;

for i = 1:size(all_C, 1)
  curr_C = all_C(i);
  for j = 1:size(all_sigma, 1)
    curr_sigma = all_sigma(j);
    model = svmTrain(X, y, curr_C, @(x1, x2) gaussianKernel(x1, x2, curr_sigma));
    predict = svmPredict(model, Xval);
    error = mean(double(predict ~= yval));
    if error < min_error
      min_error = error;
      C = curr_C;
      sigma = curr_sigma;
    endif
  endfor
endfor
%}

% =========================================================================
```

`processEmail.m`

```matlab
% ====================== YOUR CODE HERE ======================

for i = 1:length(vocabList)
  if strcmp(str, vocabList{i})
    word_indices = [word_indices; i];
  endif
endfor

% =============================================================
```

`emailFeatures.m`

```matlab
% ====================== YOUR CODE HERE ======================

x(word_indices) = 1;

% =============================================================
```
