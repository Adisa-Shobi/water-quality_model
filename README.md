# Water Quality Model

This repository contains three separate notebooks, each representing a different group member’s model with unique combinations of regularization, optimization, dropout rates, and early stopping strategies


## Summary Table

A summary table is included, presenting the results and performance comparison of all models

| Train Instance | Engineer Name  | Regularizer  | Optimizer  | Early Stopping  | Dropout Rate | Accuracy  | F1 Score  | Recall  | Precision  |
|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|------------|
| Model 1 | Shobi | L2 | Adam | Yes | 0.2 | 70% | 0.559 | 0.451 | 0.736 |
| Model 2 | Chrisostome | L2 | RMSprop | Yes | 0.4(1st layer) & 0.3(2nd layer) | 66.8% | 0.3401 | 0.2258 | 0.6885 |
| Model 3 | Josiane | L1 | Adam | Yes | 0.3 | 62% | 0.55 | 1.0 | 0.37 |

## Model Evaluations

### Shobi's Model

My model shows some interesting trade-offs in its performance. With a precision of 0.736 (meaning 73.6% of samples it identified as potable were actually potable), recall of 0.451 (meaning it only caught about 45% of the safe-to-drink water samples - imagine missing more than half of the good water!), and F1 score of 0.559 (a balanced measure combining precision and recall), it was great at avoiding false positives but missed quite a few potable water samples.

A. Two main design choices led to these results. First, I used a larger network (512→256→128→64) with Adam optimizer and a lower learning rate of 0.0005. I picked this learning rate after seeing convergence issues in early tests - higher rates made the model unstable. While this made the model very precise, it was perhaps too cautious compared to my teammates' models using RMSprop.

B. Second, I went with a dropout rate of 0.2 and L2 regularization (0.05) on specific layers. This came from early tests showing overfitting problems without dropout, especially given how noisy water quality data can be. While this helped maintain high precision, my teammates' different approaches to regularization achieved a better balance between precision and recall, reflected in their higher F1 scores.

### Chrisostome's Model

Chrisostome's model used layer-wise dropout, preventing overfitting better us. but it had the lowest F1 score (0.3401) and recall (0.2258), showing poor generalization.  due to using RMSprop, which maintains per-weight learning rates, might not have been optimal for this dataset compared to Adam. Early stopping prevented excessive training, and also the high dropout on the first layer might have removed too many features, limiting learning capacity.

### Josiane's Model

Josiane's model prioritized recall (1.0), meaning it successfully identified all actual potable water samples, but this came at the cost of precision (0.37), meaning it misclassified some non-potable samples as drinkablehad  due to using L1 regularization which encouraged sparsity, potentially causing instability and early stopping privented overfitting but it might have halted training early, preventing the model from reaching its full potential and fully learned from the data.

## Video Recording
Link to video: https://drive.google.com/file/d/1iXWgWj-3j65yy0a2oy0JNoHL0ruR0e4T/view?usp=sharing 
