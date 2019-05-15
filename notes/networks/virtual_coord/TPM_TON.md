### [Topology preserving maps: extracting layout maps of wireless sensor networks from virtual coordinates](https://dl.acm.org/citation.cfm?id=2674860)


This work describes the procedure to obtain TPM from VCS. It also proposes an efficient version of SVD through eigen value decoposition (EVD) to get close approximations. It achieves <2% Etp.

#### Notes:
* Under-deployment of anchors causes multiple nodes to have identical VCs, while over-deployment/improper placement might aggravate logical minimas and logical voids.
* Geographic Routing: These routing algorithms(GPSR) forward the packet in the direction of the destination. Hence, presence of voids, especially concave ones will be expensive.
* The objective of TPM is not to preserve the relative distances. It is to preduce topologically isomorphic maps to the original physical map.
* The principal components (PCs) obtained from SVD are orthogonal to one another and are arranged in decreasing order of magnitude.
* The authors remark that they do not have a rigorous mathematical proof justifying their decision to forego the most important PC(The first one) in the attempt to generate TCs. They present proofs to show that the first PC is a convex surface and that since VCS propagates radially around the anchors. Since we are trying to construct an isomorphic map to the cartesian system which is orthogonal in nature, not radial, the authors choose to not use the first component of PCs as it contains most of the radial information of VCS.

> If the first PC is used in generating TCs, it produces maps with significant amount of folding (Appendix-A)

* The objective is to make use of PCs which vary linearly with the axes. Non-linear variation does not help us in recreating the geographical topology.

* Actual SVD computation is very expensive O(m^2 + n^3). Hence, the authors propose using i) a set of random nodes ii) set of anchor nodes to generate the V matrix of SVD.
> Matrix U is a by-product of SVD and is not useful for generating TPM. The above proposed method by-passes the need to produce U.  

* Communication range of every node is assumed to be unity.

* Etp: This method is based on *Counting Inversions*. But it has been extended for 2D networks also.
> A good anchor placement scheme significantly reduces the number of anchors required for generating a good TPM.

* Generating TPM at a central station (instead of a distributed algorithm) avoids multiple flooding of the network. -> More explanation in Refs. [5] and [6]. (A. Caruso, S. Chessa, S. De, and A. Urpi, “GPS free coordinate assignment and routing in wireless sensor networks,” in Proc. IEEE INFOCOM, Mar. 2005, vol. 1, pp. 150–160) and (Q. Cao and T. Abdelzaher, “Scalable logical coordinates framework for routing in wireless sensor networks,” Trans. Sensor Netw., vol. 2, pp. 557–593, Nov. 2006.)

* Beautiful explanation of SVD with respect to dimensionality reduction in ref [15] (M. Kirby, Geometric Data Analysis—An Empirical Approach to Dimensionality Reduction and the Study of Patterns. New York, NY, USA: Wiley, 2001)

* The authors claim that above generated TPM remains valid for dynamically changing networks also. But I've not come across experiments/proofs to justify the same.

* Dynamically changing networks consist of node failures, incorporating new nodes and mobility of nodes.
