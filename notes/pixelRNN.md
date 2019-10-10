## [Pixel Recurrent Neural Networks](https://arxiv.org/pdf/1601.06759.pdf)

tldr; The chief contributions of the paper:
1. Model images as discrete probability distributions instead of continous
2. Use 2D LSTMs
3. Use of residual and skip connections in LSTM layers.
4. Usage of masked convolutions to provide appropriate context.




### Notes
- The inference step in VAE's is intractable, so usually the lower bounds of these objective functions are maximised.

- LSTM is used to model the conditional probability distribution of the sequence of pixels.

> The advantage of parallelization of the PixelCNN over the PixelRNN is only available during training  or  during  evaluation  of  test  images.

While PixelRNN has an unbounded range, PixelCNN has a bounded but a large range. This could be justified in the works of Yann Dauphin, et al where Gated Convolutions are introduced in stead of RNNs.

**Training Objective:** Negative loss likelihood is used to train the generation of images. The Cross-Entropy between model's distribution and true underlying distribution is minimised. Refer to Section-3.1 in [1] for a introduction to the different evaluation metrics in the context of image generation.

### Try out:
1. Ablation studies on effect of using hierarchical softmax on accuracy versus training time. 
2. According to Eq.(2), to determine the Green color of i'th-pixel, it is conditioned on Red color of the i'th-pixel. Similarly, Blue color of i'th-pixel is conditioned on the Red and Green components of i'th-pixel apart from all the previously generated pixels. Why is this order important? Are the different colors necessarily correlated? What if we model them seperately and finally combine the three?


### References
1. Theis, Lucas, Aäron van den Oord, and Matthias Bethge. "A note on the evaluation of generative models." arXiv preprint arXiv:1511.01844 (2015).
