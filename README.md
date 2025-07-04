# Optimization and Data Science Notebooks

## Homework

`Homework.ipynb` explores semi-supervised learning through a custom framework:

- Discusses design considerations such as label thresholding, objective normalization, similarity metrics and label initialization.
- Generates example datasets and visualizes performance.
- Defines an abstract learner class with formulas for the objective, gradient, Hessian and Lipschitz constants.
- Implements gradient descent, block coordinate gradient descent and coordinate minimization algorithms with various step-size and priority strategies.
- Compares different learners on synthetic data and applies them after preprocessing a real dataset.

## Project

`Project.ipynb` studies the Frank-Wolfe optimization method and applications:

- Implements three variants of the Frank-Wolfe algorithm:
    - Standard Frank-Wolfe
    - Away-step Frank-Wolfe
    - Pairwise Frank-Wolfe
- Explores multiple step-size strategies:
    - Armijo line search with parameters $\gamma$ (sufficient decrease) and $\delta$ (step reduction)
    - Diminishing step size $\gamma_k = \frac{2}{k+2}$
    - Exact line search, customized for each algorithm variant and objective function
- Visualizes algorithm performance through:
    - Loss function value vs. iterations
    - Duality gap vs. iterations
    - CPU execution time vs. iterations
- Tests on a convex quadratic objective over the simplex:
    - Minimizes $f(x) = \frac{1}{2}x^T Q x + b^T x$ where $Q$ is positive definite
    - Uses gradient $\nabla f(x) = Qx + b$
    - Implements exact step size $\gamma_k = \frac{-\nabla f(x_k)^T d_k}{d_k^T Q d_k}$
- Applies the methods to the Max-Clique problem via the Motzkin-Strauss formulation:
    - Transforms the discrete problem into continuous optimization: $\max_{x \in \Delta} x^T A x$
    - Implements two regularization approaches to address spurious maximizers:
        - $\Phi_B(x) = \frac{1}{2} |x|_2^2$ (L2 regularization)
        - $\Phi_2(x) = \alpha \sum_i (e^{-\beta x_i} - 1)$ (smooth non-convex regularizer promoting sparsity)
    - Solves the minimization form $-x^T A x - \Phi(x)$ using Frank-Wolfe variants
- Conducts hyperparameter searches for:
    - Armijo parameters $\gamma$ and $\delta$
    - L0-like regularizer parameters $\alpha$ and $\beta$
    - Tests performance on DIMACS graph benchmark instances

