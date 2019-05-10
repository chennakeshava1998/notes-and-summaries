### [Achieving Network Awareness in WSN](https://ieeexplore.ieee.org/document/6181081)

This work gives a work-around to the initial setup in traditional routing protocols in VCS based WSN. Traditionally, in the setup phase, *all the anchors flood the network* with packets in order to determine the shortest hop distances to all the nodes. This costs O(M*N) messages.
The proposed method piggybacks on random routing(RR), with a O(M) worst case increase in the packet header length, this method learns the VCS in a distributed manner without the setup phase or flooding.

After learning the VCS, every node attempts to constructs a TPM of the network and proceeds to use GLR. But if a specific node is not in Topological mode yet, it uses VC of it's neighbours and the final destination to decide the next hop.


1. In RR, a packet is forwarded to a randomly selected neighbour.
2. Every packet has a TTL field, to prevent it from lingering on the network indefinitely.


#### Algorithm:
1. When a anchor Ai intercepts a message, it appends a tuple (<Anchor_id>, hop_count_to_current_anchor). This tuple list is appended to by the subsequent anchors encountered by this packet. 
2. When a node-i recieves a packet, it checks if it's records have a smaller hopcount to a specific anchor in the tuple-header of the incoming packet. If so, the node-i updates it's nearest hop distance to the appropriate anchor. Otherwise, nothing is changed. (TODO: Overwrite the packet header with the shortest distance? What if anchors boradcast all incoming packets so that the most accurate information can be spread far and wide with the same TTL ofc.) 
3. If node-i does not have to change it's nearest hopcounts to any anchors for Lp packets consecutively, it enters VC mode. Instead of RR algorithm, it uses any of the VCS based routing techniques. It also begins to construct a TPM of the network.
4. If node-i intercepts a packet from node-j, node-i can construct an approximate VCs of node-j. Every node can store the VCS of upto Ln nodes in the network. Using this, it constructs a TPM for the subset of Ln nodes. But this set of nodes can be changed with time so as to encompass the entire WSN.
5. If a TPM covering all the nodes is constructed, then it's ~100% guarenteed about the routability of packets.
6. Construction of TPM from VCS involves the usage of optimised SVD and eigen decomposition, since only the values from the second and third columns are used. But in the worst case, it could be O(M^2 + Ln^3) at every node, M = Number of nodes, Ln = Subset of nodes being considred by node-i(say).

> As the network size increases, the TTL required to achieve correct VCS increases.
> Higher value of Lp will increase the number of packets required to bring all the nodes onboard the VC stage.
> Topology awareness can be used to select appropriate algorithms for any task. Ex: It can be used to forward packets to denser regions of the network, or according to straight line/any geometric pattern to increase the rendezvous probability.


#### Clarifications:
1. How to handle misbehaving node in the network? Something similar to misbehaving sender/reciever in ECN.

