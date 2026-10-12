# Homework 3 Analysis

`Bowen Zhao`

`UNI: bz2594`

**Which optimizer converged fastest?**

Momentum converged the fastest with Adam being slightly slower. SGD was the third fast and Batch GD performed worst in terms of training convergence speed.

**How did L1/ L2 affect the weights?**

L1 favors sparse weights and L2 penalizes weights being too big. In the training results, near-zero weights ratio is 40.72% and 21.14% respectively for L1 and L2. 

**How did dropout affect training vs. validation?**

Dropout's training loss was the greatest, and its accuracy was the lowest. However, its performance in validation loss and accuracy both presented robust results. This showed that dropout makes training harder but it also reduces overfitting. 

**Which activation function performed differently and why?**

Sigmoid performed differently. Its loss and accuracy performances were less ideal than ReLU and Tanh in both training and validation. This is due to the fact that Sigmoid's derivative is at most 0.25, and this slows the process of gradient descent, ultimately leading to inferior performance. 

**Which configuration generalized best, and why?**

Adam + ReLU + Dropout performed the best. Adam accelerated the process of training, ReLU avoids the vanishing of gradient, and dropout makes the performance of the model more robust. 