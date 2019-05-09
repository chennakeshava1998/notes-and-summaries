### [Gated CNNs(Yann Dauphin et al, 2017)](https://arxiv.org/abs/1612.08083)

The paper aims to perform language modelling using Gated CNNs. This is the first non recurrent approach to language modelling, and the paper achieves substantial accuracy results on large-context datasets also. The main USP is that the CNN units can be parallised and hence this model is more faster than LSTM based models, **only during inference, not necesarily during training. 


#### Key Points:
1. Using stacked convolutions will increase the number of operations per context to O(nk) (per kernel), where n is the context size and k is the kernel width. 

2. *Causal convolutions* are used ie the kernel can only see the previous words and not the future words. This ensures that the model  does not cheat.

3. The initial part of the sentence is padded with (k - 1) tokens, where k is the width of the kernel.

4. Comparison between Gated Linear Unit and Gated Tanh Unit has been performed. GLU is better than the latter, because it better handles the vanishing gradient problem.

5. RNNs are parallelised over different sequences while training, and CNNs can be parallelised over different contexts or tokens.

6. Residual activation blocks are used (He et al, 2015)

7. Gradients have been clipped to [-5, 5]. Kaiming intiialization, Momentum, weight normalization -> These help in faster convergence even with large learning rates = 1.

8. **Adaptive softmax** is used, instead of the conventional softmax. This is less expensive but approximately gives the same results.

9. The authors empirically find that a context size of 40 tokens is sufficient to obtain high accuracies. Similarly, it is sufficient to limit the backpropagation to 40 time steps (instead of the theoritical infinite limits).

#### Notes:

This is a promising alternative to LSTM models. But it has been hard to reproduce the results of this paper. This is probably because certain components like adaptive softmax has been recent and do not have open source implementations.
