- output of the model is a number
- $g(x_i) = w_0 + \sum_{j=1}^n w_{j}x_{i_{j}}$
	- where each $x_i$ is an example
	- each $x_{i_{j}}$ a feature
	- $w$ are weights for each feature, with $w_0$ representing the initial bias
- *vector form* : $g(x_i) = \mathbf{W}^T\mathbf{X_i}$
	- recall that our features matrix needs to be augmented with a $1$ to account for the bias weight

### Normal Equation
- our goal is to have $Xw \approx y$ , so we need to find the right weights. Unfortunately $X$ is more often than not not invertible, since the number of examples is fair greater than the number of features, i.e. the matrix is not square
- [ ] $X^TX$ however will give us a square matrix , [[Gram Matrix]] and will almost always be invertible. Hence,
	- $(X^TX)^{-1} X^TXw = (X^TX)^{-1}X^Ty \equiv w = (X^TX)^{-1}X^Ty$