### [Dimension Reduction of VCS in WSN](https://ieeexplore.ieee.org/document/5683099)

This work aims to weed out useless anchors and reduce dimensions of the virtual coordinates.

#### Notes:
1. Current anchor placement schemes seek to place farthest nodes as anchors. Some schemes attempt to make the boudary nodes as anchors. But it is computationally expensive to identify if a specific node is a boundary node.
2. The authors use Novelty Filter Decomposition Method(M Kirby, Geometric Data Analysis, John Wiley & Sons) to filter out useless anchors. This method is expensive because the size of the VCS matrix is O(M*N). The method involves multiplcation of multiple matrices.
3. SVD is used(in the form of PCA) to retain the maximum variance components.
4. Greedy Ratio (Percentage of packets that reach the destination using Packet Forwarding) is used to evaluate the new VCS after performing dimensionality reduction. **Try t-SNE technique and evaluate the results**
5. The GR was obtained by Monte-Carlo simulation rather than using the All source-destination pairs.
> Higher number of anchors may reduce the number of non-unique IDs, but it does not necesarily increase the routability.