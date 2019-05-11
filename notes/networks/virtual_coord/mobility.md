[Tracking and Prediction of Mobility using TPM](https://ieeexplore.ieee.org/document/6654789)

This work aims to track and predict the position of a mobile node using Topological preserving map(TPM). The traditional method uses GPS/Localization algorithms which are expensive/inaccurate respectively.
The originally proposed TPM uses the second and third principal components in the SVD. Hence, this causes compression of the TPM near the edges, which consequently leads to poor mobility tracking and prediction results along the edges/boundaries of the network.
This work proposes to use the first principal component also, along with the second and third components to alleviate the above mentioned problem.
Competitive results are obtained when compared to that of geographic coordinates.

#### Notes:
1. VC generation is a many-to-one transformation from the physical domain to the virtual domain. Hence the VCS do not contain the directional information.
2. Transformation between geographic coordinates to topological cordinates is non-linear. Hence *even if an object moves with constant velocity in geographic coordinates, it does not do so in topological coordinates.*
3. Directional and geographic information is not available in VCS, VCS is a radial system.
4. Topological coordinates of the mobile node is first estimated by taking the average of the sensor nodes which detect it's presence. Later, modified SVD transformed is performed on the averaged VCS.
5. Assumption: It's assumed that the time for inter-communication of the sensors is negligible when compared to the time taken for the mobile node to change neighbourhood.
6. A linear mobility model is used to predict the future position of the mobile node.
7. An ellipse is used to depict the future presence of the mobile node at some point of time in the future. The ellipse serves as error-tolerance area for the prediction of the mobile target. The major axis of the ellipse is perpendicular to the predicted direction of motion of the mobile target.
8. If the target is predicted to go out of range of the WSN, all the appropriate border nodes are alerted.
9. The suggested method is centralised in nature. The base station aggregates all the data, performs all the computation and alerts the sensor nodes which are predicted to be in the ellipse.
10. Geographic coordinates reflect a continous change in the position of the target. In addition, the object moves with a constant velocity in the geographic coordinates domain.
11. The authors note that:
> Tracking in TC domain is not very effective when performed at very fine granularity.
This is quite counter intuitive. Even if the transformation between geographic and topological domains is not linear, there is no reason for TC domain changes to not be continuos. (i like using double negatives :P) It's not very clear why smaller sampling rate does not guarentee better tracking/prediction results.
12. The model has been tested on two topologies. (Why not test it againt all of the test cases - building, spiral, odd shape?) 

