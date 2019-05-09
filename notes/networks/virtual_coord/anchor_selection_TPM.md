### [Anchor Selection and TPM](https://ieeexplore.ieee.org/document/5984912)

#### Notes:
1. ENS(Extreme Node Search) automatically finds the optimal number of anchors and their placement too.
2. DVCS uses O(M choose 2) axes for calculation of distances, because you can define an axis with every pair of anchors. This problem was resolved by introducing angles in the TPM and choosing the anchors which are almost orthogonal to one another.

> Adding the (n+1)th anchor to an optimal placement of n anchors, does not result in the optimal placement of (n+1) anchors. The placement of anchors does not have the *optimal substructure* property.

Contrary to common perception, not all boundary nodes make good anchors.
3. The paper presents a literature survey on the evolution of virtual coordinate system.
4. The ENS algorithm is distributed in nature.

##### ENS Algorithm:
1. Select two arbitrary nodes as anchors. Flood the network using these nodes to generate VCS across the network. 
2. Every node verifies if it is a local minima in it's h-hop neighbourhood. If it's a minima/maxima, it declares itself as an anchor
3. The selected anchors again flood the network and generate VCS. The initial two random nodes may also be used along with the newly generated nodes as the anchors.
4. The metrics of Avg Routability and Avg Path Length is calculated using the All Source-Destination Paths.
5. DVCR has higher path length ratio when compared with CSR and LCR. This implies that DVCR can improve on the quality of paths it produces.
6. I still need to learn why the only second and third column is used to glean the topological coordinates after performing the SVD on the VCS matrix.

> If a few nodes fail, VCS will have to be recalculated. But TPM preserves it's validity even if a moderate number of nodes fail.