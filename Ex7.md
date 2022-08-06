# (Week 8) Ex7: K-means Clustering and Principal Component Analysis

`findClosestCentroids.m`

```matlab
% ====================== YOUR CODE HERE ======================

for i = 1:size(X, 1)
  diff = zeros(K, 1);
  for j = 1:K
    currdiff = X(i, :) - centroids(j, :);
    diff(j) = currdiff * currdiff';
  endfor
  [val, idx(i)] = min(diff);
endfor

% =============================================================
```

`computeCentroids.m`

```matlab
% ====================== YOUR CODE HERE ======================

for i = 1:K
  count = 0;
  for j = 1:m
    if idx(j) == i
      centroids(i, :) += X(j, :);
      count += 1;
    endif
  endfor
  centroids(i, :) /= count;
endfor

% =============================================================
```

`pca.m`

```matlab
% ====================== YOUR CODE HERE ======================

Sigma = X' * X / m;
[U S V] = svd(Sigma);

% =========================================================================
```

`projectData.m`

```matlab
% ====================== YOUR CODE HERE ======================

U_reduce = U(:, 1:K);
Z = X * U_reduce;

% =============================================================
```

`recoverData.m`

```matlab
% ====================== YOUR CODE HERE ======================

X_rec = Z * U(:, 1:K)';

% =============================================================
```
