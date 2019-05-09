#### On Boundary Detection of 2D and 3D WSN

This constructs a Topology Preserving Map(TPM) using the virtual coordinates(VCs) and uses geometric properties on those coordinates to detect a boundary node.


**Computation complexity:**
If a node has K neighbors, it will have to perform (K Choose 3) calculations in the worst case scenario. So, the total computation complexity is O(N * max(K ^ 3)). But the paper mentions the same as O(max(|K|) ^ 2)

**Memory complexity:**
Similarly, we would need to store the topological coordinates for all neighbors of a node (O(K)) and there are N nodes. So that gives us O(N*K). But the paper mentions the memory complexity as O(max |K|) * max(|K|). 
The algorithm achieves 100% in detecting the inner and outer boundaries. It gets > 90% in detecting dynamically changing event-boundaries.

##### Notes:
1. A connectivity domain description can have multiple valid physical embeddings, even though only one of them might correspond to the actual physical network. 
2. Boundary detection is performed in two stages. First the TPM is constructed, then the boundary nodes are detected.
3. SVD is performd on the matrix of hop-distances. This is an expensive operation. (Cost of SVD = O(m^2 + n^3) where the matrix has m rows and n columns)
4. The dynamically changing event boundaries are detected by applying the algorithm only on the nodes which have detected the event.  
5. The mapping from physical to virtual coordinates is not linear, hence geometric properties do not hold true in the VCS.

##### Algorithm:
1. If a node has < 3 neighbours, it's a boundary node.
2. Consider the area of the traingle formed by every three of the neighbours of a node. If the sum of the areas match for any combination of the neighbours, then the node is an internal node, else it's classified as an boundary node.
3. If the size of the traingle formed by a specific node with any two of it's neighbours is 0, then the node is a boudary node.