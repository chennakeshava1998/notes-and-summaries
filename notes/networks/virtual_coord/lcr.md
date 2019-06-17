# (LCR - Logical Coordinate Routing)[https://ieeexplore.ieee.org/document/1381321]
I have not touched upon the perforance analyses here because this paper became the basis for subsequent work on routing without geographical information, and hence was the state-of-the-art at that time.
#### Definitions
- Address-based Routing: Routing based on explicit destination address. These are not usually scalable because the per-node state grows as a function of the network size or the number of active destinations.
- Content-based Routing: Use a predicate to filter a set of nodes as destination, useful for multi-cast routing. Then use address-based routing for unicast message delivery.

### Assumptions
1. Nodes are placed in a 2D plane. (Where is this assumption used? The properties could still be proved without using this asumption)
2. Nodes are static (LCs can be recomputed periodically)
3. It is inexpensive to choose anchors/landmarks of our choice.
4. Communication links are bidiretional.

#### Logical Coordinate Space
This is similar to the concept of distance vector. But minimum hopcounts is measured from every node to a set of anchors/landmarks only, unlike distance vectors where hopcounts is known for every pair of nodes.

#### Properties
1. Neighbours differ by atmost unity with respect to the same anchor.
2. Between any two nodes, bounds on the hopcounts is derived. Suppose X and Y be two arbitrary nodes, then<br> *Minimum:* max(Xi - Yi), where Xi refers to the hopcount between X and anchor-i.<br>
*Maximum:* Summation over all i (Xi - Yi)

- Distance between two points X and Y : sqrt(sum over all i (Xi - Yi)^2)  [Similar to rms without the mean]

> Every node is aware of the logical coordinates of it's neighbours. Is it possible to find out the neighbours of a node using only the LCs information? Can we perform routing without the additional information of neighbourhood of a node specified explicitly.

#### Loop Avoidance
- This proble arises when multiple neighbours have the same distance to the destination. Worst case is when all the neighbours have the same distance to the destination. Less likely in the case of geographical cordinates.
- Solution: Store a window of recently visited nodes in the packet's header. Tradeoff between message header size and message delivery. Kill the message after  maximum number of hops.

#### Void Avoidance
- There might not any neighbour which is closer to the destination than the present node itself. Th
- Solution: Send the packet to the closest node to the neighbour (best *upstream* node). The hope is that there is a viable path from the upstream node to the destination. *MaxTolerance* is the bound after which packet will be dropped. Every packet has a tolerance counter in the header which is incremented after transmission to an upstream node.
> Often, Logical Cordinates mask the presence of physical/geographical voids.

> This is a heuristic way to solve this issue.

#### Dynamic Issues:
- Addition of new nodes is not an issue. The new node can infer logical cordinates from it's neighbours. But if a node is removed, it's not clear how the system can converge to the correct logical cordinates.
> Suppose a cut-vertex is removed from the graph, then according to the system, remaining nodes continue to use the old Logical Coordinates. But practically, the graph would have been disconnected.

### Results
- LCR has higher routability/delivey ratio than the protocols reported in [1] and [2].
- LCR uses only one-hop neighbourhood table for routing. Both [1] and [2] require 2-hop neighbourhood information is collected.
- LCR uses a constant state per node. Irrespective of the size of the network, every node only maintains the logical cordinates of it's neighbours.
- LCR can be made robust by arbitrarily increasing the number of anchors. This increases the redundancy of the network in case of node failures. 


#### References
1. J. Newsome and D. Song. Gem: Graph embedding for routing and datacentric storage in sensor networks without geographic information. In Proceedings of the SenSys 2003, 2003.
2. A. Rao, C. Papadimitriou, S. Shenker, and I. Stoica. Geographic routing without location information. In Proceedings of Mobicom, 2003.

### Doubts
1. Check out the works of Leighton and Moitra(2010) which proves Papadimitrou's conjecture on planar tri-vertex connected graphs.
2. Works on Kissing Number, Greedy Embedding in hyperbolic planes to determine the optimal number of anchors. 




