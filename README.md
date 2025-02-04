# Water Quality Model

This repository contains three separate notebooks, each representing a different group member’s model with unique combinations of regularization, optimization, dropout rates, and early stopping strategies


## Summary Table

A summary table is included, presenting the results and performance comparison of all models

| Train Instance | Engineer Name  | Regularizer  | Optimizer  | Early Stopping  | Dropout Rate | Accuracy  | F1 Score  | Recall  | Precision  |
|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|------------|
| Model 1 | Shobi | L2 | Adam | No | 0.2 | 69% | 0.465 | 0.338 | 0.746 |
| Model 2 | Chrisostome | L2 | RMSprop | Yes | 0.4(1st layer) & 0.3(2nd layer) | 0.6687 | 0.3401 | 0.2258 | 0.6885 |
| Model 3 | Josiane | L1 | Adam | Yes | 0.3 | 62% | 0.55 | 1.0 | 0.37 |


Shobi's model  performed best in terms of accuracy and precision, likely due to L2 regularization and extended training without early stopping,  L2 regularization helps reduce weight magnitude, making the model more stable and No early stopping allowed longer training, improving accuracy.

Chrisostome's model used layer-wise dropout, preventing overfitting better us. but it had the lowest F1 score (0.3401) and recall (0.2258), showing poor generalization.  due to using RMSprop, which maintains per-weight learning rates, might not have been optimal for this dataset compared to Adam. Early stopping prevented excessive training, and also the high dropout on the first layer might have removed too many features, limiting learning capacity.

Josiane's model had the best recall (1.0), meaning it captured all positive cases. However, it suffered from low precision (0.37), indicating many false positives due to using L1 regularization which encouraged sparsity, potentially causing instability and early stopping might have halted training early, preventing the model from reaching its full potential and fully learned from the data.
