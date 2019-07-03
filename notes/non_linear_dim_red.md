- They do not calculate a function from higher-dimension to a lower dimensional manifold that can be used for a datapoint whose relationship with the training data is unknown.
- They assume the existence and computability of a meaningful distance metric in the input(higher dimensional) space.

- PCA and MDS produce linear embeddings only.
- All the spectral based methods like Laplacian Eigenmaps, LLE, Hessian LLE : They cannot create an embedding for a previously unknown datapoint, without recalculating embedding for the entire dataset. 
- The three spectral methods have 3 steps. Identify the neighbours, compute the gram matrix, then solve the eigen value problem for this matrix. All the htree methods differ in the second step.

Advantages of the proposed method:
1. Learned function is invariant to complex non-linear transformations like lighting changes in images or geometric distortions.

2. The learned function is smooth in the output space.

3. The function only used the neighbourhood of every data point to compute it's image in the lower dimensional manifold.