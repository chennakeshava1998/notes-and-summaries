### ![MAPO Liang et al](https://arxiv.org/pdf/1807.02322.pdf)

#### Key Points:
1. Pitfalls of policy gradient methods:
    - Sample Efficiency is poor.
    - High variance and unstability in learning.
    - Difficult to systematically explore search space. (This is true for model-based methods that seek to learn the environment in itself like MBMV, I2A)

> We consider an RL environment with a finite number of discrete actions, deterministic transitions, and deterministic terminal returns. In other words, the set of all possible action trajectories A is countable, even though possibly infinite, and re-evaluating the return of a trajectory Rpaq twice results in the same value.

2. Memory clipping alleviates *cold start* of policy gradients.
- Initially, if a bad policy assigns low probabiltity to a high-reward trajectory, it's hard to recover later. 
- Similarly, bad update will break the policy (brittle)
- Putting a lower bound onto memory weight ensures that high performing trajectories are never ignored. (but this also introduces bias :(( )

3. Bloom filter used to store billions of partial sequences for systematic exploration. 
- This helps reduce duplicate trajectories and helps find higher number of high-reward trajectories. 
- It's easy to parallelise bloom filters. 
- Is this performed for every example and inference also?

4. Distributed Sampling:
- If memory buffer is small, enumerate and calculate the exact expectation.
- else: cost of calculating expectation grows linearly with size of the memory buffer. So, go for sampling.
- now, the cost of calculating expectation grows linearly with size of the number of samples. but, *sampling itself is linear in the size of the memory buffer, because we need to find the probabilities of each of the trajectories.*
- They tackle this with having multiple actors (arXiv:1802.01561, 2018), but I think this isn't feasible. It's like running an exponential algorithm with linearly increasing number of cores.
- Each actor uses stale policy for sampling, because this is more efficient. The latest policy is synchronised every few time steps. TODO: Does **accuracy/sample efficiency** improve if this is made synchronous?? 

*Rejection Sampling:*



#### Doubts: 
*this section is under construction. please excuse me for lame doubts*
1. How is this method different from prioritised experiance replay in DQNs?
2. Have DQNs been used for program synthesis?
3. How is this weakly supervised training?
4. Do we use stochastic categorical policies here? Can we use diagonal gaussian policies? Will it make a difference?
5. The experiances stored in the buffer donot correspond to the current policy. Is it correct to compare the curent policy against a stale set of high-performing observations?
6. Why is MAPO applicable only to deterministic environments with discrete actions?
7. Why is memory weight clipping required? 
8. Difference between MAPO and Experiance Replay buffer? By storing only the high-reward samples, are we not introducing a bias into the model? How does naive policy gradient work against this problem? TODO!! The authors do use random policy in the initial phase to generate 1k programs per example to warm start the memory buffer.
9. Section-3: Is the program space countable? Can we sequenrtially order the set of all possible programs?
10. How is the Reward function conditioned on the context x?
11. In eq(2), a baseline b is subtracted from the rewards. But how does this reduce the variance of the model?
12. How are actions, env and transitions defined?
13. Find a way to tackle spurious programs: Check: Panupong Pasupat and Percy Liang. Inferring logical forms from denotations. In Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), volume 1, pages 23–32, 2016.
14. It is clear that variance can be reduced due the smaller size of the buffer / stratified sampling. But how do we prove that the model is unbiased? What is "principled" wrt memory weight? Is it constant or does it consitional?

15. Where the weights associated with the trajectories being used? Every actor calculates a weight for a trajectory and pushes them both into the learner queue. 