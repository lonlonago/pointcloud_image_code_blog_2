 application example 

 (1) Use a pass filter in PCL to filter the point cloud 

 The code is parsed as follows 

 Due to the randomly generated point cloud, the result of each run is different, but the points in the point cloud with the Z coordinate outside the range of (0, 1) will be filtered out 

 ![avatar]( 976394-20170226220147851-48329442.png) 

 (2) Downsampling the point cloud using a VoxelGrid filter 

  The use of the voxelization grid method to achieve downsampling, that is, to reduce the number of points, reduce the point cloud data, and simultaneously save the shape characteristics of the point cloud, which is very practical in improving the speed of algorithms such as registration, surface reconstruction, and shape recognition. PCL is the implementation of the VoxelGrid class to create a three-dimensional voxel grid through the input point cloud data. After accommodating each voxel, the center of gravity of the voxel is used to approximately display other points in the voxel, so that all points in the voxel are finally represented by a center of gravity. For the filtered point cloud obtained after processing all voxels, this method is slower than the method of approximating the center of the voxel, but it is more accurate for the representation of the surface corresponding to the sampled points. 

 code explanation 

 voxel_grid.cpp 

 As can be seen from the output results, the amount of filtered data is greatly reduced. The print result is as follows 

 ![avatar]( 976394-20170226225140929-1170511150.png) 

  The resulting graph shows a comparison. 

 ![avatar]( 976394-20170226225207851-84573187.png) 

 The visualization results of the original point cloud and the filtered point cloud show that the density and neatness of the points are different. Although the amount of processed data is greatly reduced, it is obvious that the shape features and spatial structure information contained are similar to the original point cloud. 

  WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303134842923-2129395911.jpg) 

 To be continued ***************************88 

