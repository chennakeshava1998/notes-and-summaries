# [CSR - Convex Subspace Routing](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5355185)

tl;dr - In contrast to existing VCR schemes that use backtracking or hill climbing techniques to overcome local minima, CSR avoids using anchors that cause local minima. CSR selects subsets of anchors dynamically to provide a **convex distance function** from source to destination. Consequently, it is less sensitive to anchor placement and over anchoring.

- CSR uses the neighbourhood table information, similar to LCR. It only differs in choosing the subset of anchors for distance calculation.

- When the source and destination are dynamic, content-based routing is used to obtain the list of destination nodes. In case of static networks where the addresses of all nodes are known, address-based routing is used. 
- Address-based routing is further classified into hierarchical and location-based routing. GPS and Virtual-Coordinates come under location-based routing.

### Advantage of VCS over Geographical Routing (Introduction)
- Geographical routing is futile in the presence of physical voids. Virtual-coordinates(VC) masks the voids.
- Distance calculated using Geographic Coordinates(GC) provides the line-of-sight distance, unlike VC which provides the actual hop-counts required for routing.
- GC suffer from errors in localization.
- GC does not help in obtaining the routing path(networks with low node densities). But the VC help in etching out the actual path of a packet.

- Identical VC cannot be guarenteed. It is a function of number and placement of anchors.
> Increasing the number of anchors decreases the number of idential VCs, but it also  increases the logical voids.
**Logical Void:** Minima in the distance function. There is no neighbour that is closer to the destination than the given node itself.

- [1] attributes local minima of the distane function to VC quantization ie. VC is coarse since the hop-counts are always integers. This paper also attributes the loss of directionality as one of the causes.

### Properties
1. In a virtual coordinate system, two anchors cannot have identical coordinates. Also a non-anchor node and an anchor cannot have identical coordinates.  it is possible for more than one non-anchor node to have the same coordinates. 

2. Anchors cause a local maximum in the distance function between any source-destination pair. Hence, it is preferred to keep the anchors at the boundaries to prevent the occurence of a local maximum in the distance function, because this also causes a local minimum.
> Identification of boundary nodes is complicated in presence of physical voids.

**Optimal Nnumber of anchors** : Under deployment of anchors results in multiple identical VCs, hence degrades greedy ratio. The authors give a toy example of how over-deployment also degrades Greedy Ration and sabtages the direction of routing.

### TODO: Improper anchor placement


### Notes
1. Hopcounts create a non-convex distance function. Consequently, the presence of local minima/saddle points cause the logical void problem.

### References
1. K. Liu and N. Abu-Ghazaleh, “Aligned virtual coordinates for greedy routing in WSNs,” Proc. IEEE Int. Conf. on Mobile Adhoc and Sensor Systems, pp. 377–386, Oct. 2006.


### Doubts:
1. Why should we choose L2 norm as the distance metric? This deserves an ablation study to study if the performance is monotonic with respect to p in Lp norm. Also, try other metrics appropriate to measure distances between vectorss- Hammond?
2. Why is the distance function chosen in such a manner? Rationale????? -> Check mertrics, topology, etc. What are the properties of such a distance function.
3. Does CSR change the anchors for every pair of source-destination? Or does it choose a set of anchors such that the distance function is convex for all pairs of source-destination? Is that even possible?