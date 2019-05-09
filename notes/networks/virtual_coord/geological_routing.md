#### [Geological Routing in WSN]()

Constructs a Topology Preserving Map(TPM) from virtual coordinates(VCS). It swithces between using Topological coordinates, Virtual coordinates and routing to the nearest anchor to the destination. This switching is helpful in bypassing the local minima in each of the local minima of the individual domains.

#### Notes:
1. Physical voids become transparent in the virtual domain, but they are inefficient in handling the local minima(for instance, the right hand rule could become very expensive around a void)

> Topological Coordinates more accurately select the neighbours to forward a packet than geographic coordinates.
This is probably because topological coordinates contain the connectivity information also. It's not entirely clear how topological coordinates have neighbourhood information, because they do not use physical/GPS coordinates in their generation process. 

2. L1 and L2 norms are used in VCS too, although VCS is a radial coordinate system.
3. If TPM has a local minima, we switch to VCS. If VCS also has a local minima, we send the packet to the nearest anchor to the destination. 
4. Packet header contains information about the mode of routing(TC, VC or AM)
5. Every packet saves the successor and predecessor information to prevent looping information.
6. Avg path length calculation includes those of packets which did not reach the destination. This might show a optimistic picture of Avg Path Length metric.

7. The paper presents a literature survey on previous methods to handle problem of packets getting stuck at the local minima. 
8. It requires O(M*N) packets to generate the VC information, M = Number of anchors, N = Number of nodes.
9. Cost of generating topological coordinates << Cost of generating physical coordinates


> Identification of optimal number of anchors and their placement is an open problem in the Virtual Coordinate System.
