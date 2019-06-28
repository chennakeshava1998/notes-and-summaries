## [Sparse Representation, AAAI 2019, Vincent, White](https://arxiv.org/pdf/1811.06626.pdf)
WIP
- [D] In *Background* section, you force the prediction to be a linear combination of the representations. This reduces the expressivity of the neural network. It also limits the posibilities of transfer-learning or fine-tuning later layers[Check!]. Is this assumption necessary? 

- [D] Sparse representation ensures stable value functions. But what about the rate of convergence to the true value?
- [D] How does Fig. 4a represent locality of neurons in the input space? **IMP**
- To compute Table-1, how many pairs of inputs were used?

### Definitions:
- Instance sparsity corresponds to the percentage of active units for each input. 
- Interestingly, 1-NN and 2-NN actually produced less instance sparsity than vanilla neural networks.
- If the overlap between two representations corresponding to two different inputs is zero, the interference would be zero. Updating the value function with respect to one state, therefore, would not affect the other state’s value.


### Doubts
1. What do you mean by catastrophic interference?
2. What do you mean by local representations?
3. How does sparsity ensure local representations?
4. WTH is tile coding? Check Sutton 1998
5. Fig.2 : Why is cumulative reward decreasing in Mountain Car for Vanilla Neural Network ??
6. Try the expt. of Fig. 4b with random positions, instead of the center and middle.
7. Try the exact opposite of the sparse representation, to obtain dense representation to check if it performs better than TC.
8. Empiricaly, to reduce interference, you need lesser activation overlap[French, 1991]. It's not necessary to have sparse representation per se.

