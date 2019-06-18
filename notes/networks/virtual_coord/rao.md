[Geographic Routing without Location Information - Ananth Rao](http://delivery.acm.org/10.1145/940000/938996/p96-rao.pdf?ip=129.128.184.5&id=938996&acc=ACTIVE%20SERVICE&key=FD0067F557510FFB%2EE7ED0E691902343F%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1560885797_45816a6e7e4388b8a8b07d3f04c2f04f)

*Work in Progress*

This paper introduces the concept of virtual-coordinates. It uses the information about perimeter nodes for assigning the VCs to other nodes in the network. The routing algorithm used is very similar to Logical Coordinate Routing. This performs better than geographic routing in the presence of obstacles. But the work by D. C. Dhanapala et al on Convex Subspace Routing achives better performane than this paper on similar network topologies. 

- **On-Demand Routing:** No periodic exchange of messages. A route request is flooded through the entire network when there is a need to send a message. Does not work well with large networks.
- Geographic routing is scalable, as nodes only keep state for their neighbors, and supports a fully general any-to-any communication pattern without explicit route establishment.

- GOAFR+[1] is both worst case optimal and average case efficient for overcoming cases where no neighbour is nearer to the destination.
- Virtual Coordinates perform better than geographic coordinates. Intuitively, this is because virtual coordinates reflect the network connectivity instead of the nodes’ true positions which are less relevant in the presence of obstacles.

- Ad-hoc networks need routing between generic pair of source and destination. On the other hand, in sensornets, there is no reason for sensors to communicate with one other. Instead, they usually send their data back to the central station.


### References
1. Fabian Kuhn, Roger Wattenhofer, Yan Zhang and Aaron Zollinger, ”Geometric Ad-Hoc Routing: Of Theory and Practice,” in Principles of Distibuted Computing, 2003. ===> Obtain localization solely through the connectivity information 
