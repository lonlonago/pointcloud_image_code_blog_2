   Using statistical analysis techniques, we can centrally remove measurement noise points (i.e. outliers) from a point cloud data. For example, laser scanning usually produces point cloud datasets with uneven density. In addition, errors in measurement can also generate sparse outliers, which makes the effect poor. The calculation of estimating local point cloud features (e.g. normal vector or curvature change rate at sampling points) is complicated, which can lead to incorrect values, which in turn can lead to later processing failures such as point cloud registration. 

 Solution: Perform a statistical analysis of the neighborhood of each point and prune out some points that do not meet certain criteria. The sparse outlier removal method is based on the calculation of the distance distribution from points to neighboring points in the input data. For each point, calculate the average distance from it to all its neighboring points. Suppose the result is a Gaussian distribution whose shape is determined by the mean and standard deviation. Points with average distances outside the standard range can be defined as outliers and can be removed from the data. 

  Create file statistical_removal cpp 

 The running result is: 

 ![avatar]( 976394-20170227002757273-428890249.png) 

 (2) Projection point clouds using parametric models 

    How to project a point onto a parametric model (plane or sphere, etc.), which is set by a set of parameters, using its equation form for planes. There are data structures in PCL that deliberately store common model coefficients 

 The result of compiling and running is as follows 

 ![avatar]( 976394-20170227110155282-2085776941.png) 

 It can be seen from the experimental results that the Z-axis before projection is not 0, it is a randomly generated value. After projection, the printed results show that the value of xy has not changed, and z has become 0. 

 Therefore, the projection filter class is the input point cloud and the projection model, and the output is the point cloud projected onto the model. 

 To be continued **************************88888 

