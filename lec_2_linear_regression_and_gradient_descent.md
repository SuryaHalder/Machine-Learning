This lecture covers the fundamental mechanics of **Linear Regression**, focusing on how to represent models and the specific algorithms used to fit them to data.

---

## 1. Model Representation

In linear regression, we represent the relationship between input features ($x$) and the target output ($y$) using a **Hypothesis ($h$)**.

For a house price prediction problem with multiple features (like size and number of bedrooms):

* **Features:** Let $x_1, x_2, \dots, x_n$ be the input variables.
* **Parameters:** Let $\theta_0, \theta_1, \dots, \theta_n$ be the weights (parameters) the algorithm learns.
* **Hypothesis:** $h_\theta(x) = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_nx_n$.

To simplify math, we define a "dummy" feature $x_0 = 1$, allowing us to write the hypothesis as a vector product:


$$h_\theta(x) = \sum_{j=0}^{n} \theta_j x_j = \theta^T x$$

### ### The Cost Function

To find the best $\theta$, we minimize the **Mean Squared Error**. We define the **Cost Function $J(\theta)$**:


$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$$


The goal of the learning algorithm is to $\min_\theta J(\theta)$.

---

## 2. Gradient Descent

Gradient Descent is an iterative optimization algorithm that tweaks $\theta$ to reduce $J(\theta)$ by taking small steps in the direction of the steepest descent.

### ### Update Rule

For every $j$, we simultaneously update:


$$\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta)$$


Where $\alpha$ is the **Learning Rate**. If $\alpha$ is too small, the algorithm is slow; if it is too large, it may overshoot the minimum.

### ### Variations of Gradient Descent

| Type | Process | Pros/Cons |
| --- | --- | --- |
| **Batch Gradient Descent** | Uses **all** training examples in every step. | Stable, but very slow for massive datasets. |
| **Stochastic Gradient Descent (SGD)** | Updates $\theta$ using only **one** example at a time. | Much faster; can handle "Big Data" but "oscillates" near the minimum. |

---

## 3. The Normal Equation

While Gradient Descent is iterative, the **Normal Equation** provides a closed-form solution to find the optimal $\theta$ analytically in one step.

By setting the derivative of the cost function to zero and using matrix algebra (specifically the "Design Matrix" $X$), we derive:


$$\theta = (X^T X)^{-1} X^T y$$

* **Advantage:** No need to choose a learning rate $\alpha$ or iterate.
* **Disadvantage:** Calculating the inverse of $(X^T X)$ is computationally expensive ($O(n^3)$) if you have a very large number of features (e.g., $n > 10,000$).

---

## 4. Summary of Terms

* **$m$:** Number of training examples (rows in the dataset).
* **$n$:** Number of features (columns).
* **$x^{(i)}, y^{(i)}$:** The $i^{th}$ training example.
* **Design Matrix ($X$):** A matrix where each row represents a training example.
