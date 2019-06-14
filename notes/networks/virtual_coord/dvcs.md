### [Directional VCS for WSN](https://ieeexplore.ieee.org/document/5963079)

This work aims to glean directionality information coupled with VCS to increase the available information for routing. Routing based on the new coordinates provies better functionality than the existing routing mechanisms like CSR and LCR. 

1. Greedy Forwarding: A packet is forwarded to the neighbour whose distance to destination < distance to destination from the current node.
If no such neighbour is found, then a local minima has been reached.

2. Physical domain to VCS transformation is many-to-one because VCS is indifferent to directions.

3. *After the transformation to DVCS, the address size of every node is (M choose 2), where M = Number of anchors.*
4. This transformation maps the VCS into positive and negative parts of the real line with respect to every pair of anchors. 
5. The authors prove that 100% routability can be achieved in a constrained tree (CT, deg of every node<= 3)
6. In the routing algorithm, to forward a packet, a node must perform *atleast* O(K + 1) calculations to determine the next nearest neigbour to transfer the packet, where K = maximum number of neighbours of the node / maximum degree of a node.

