In the past few years, there has been a lot of in-depth research on 2D images, and it has made great progress. It has achieved excellent results on classification tasks mainly due to two key factors: 1. Convolutional neural networks. 2. Data - A large amount of image data is available. 

 But for 3D point clouds, data is growing rapidly. There is a great trend of developing from 2D to 3D. For example, relevant modules for 3D point cloud processing have been gradually included in opencv. In terms of data, there are also multiple channels for point cloud acquisition, whether it is from CAD models or scanning point clouds from LiDAR sensors or RGBD cameras, which are everywhere. In addition, most systems directly acquire 3D point clouds instead of taking images and processing them. Therefore, in the era of deep learning fire, how can we apply these amazing deep learning tools to process 3D point clouds as well as 2D images? 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNDUwOTUyMz93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 Challenges faced by 3D point clouds applying deep learning. Challenges faced first on neural networks: (1) Unstructured data (no mesh): A point cloud is an XYZ point distributed in space. There is no structured mesh to help CNN filters. (2) Immutable permutation: A point cloud is essentially a long string of points (nx3 matrix where n is the number of points). Geometrically, the order of the points does not affect how it is represented in the underlying matrix structure, for example, the same point cloud can be represented by two completely different matrices. As shown in the following figure: (3) Variation in the number of point clouds: In an image, the number of pixels is a given constant, depending on the camera. However, the number of point clouds can vary widely, depending on various sensors. Challenges in point cloud data: (1) Lack of data: The scanned model is often occluded and part of the data is lost. (2) Noise: All sensors are noisy. There are several types of noise, including point cloud perturbations and outliers. This means that a point has a certain probability of being within a certain radius near the place where it was sampled (perturbation), or it can appear anywhere in space (outliers). (3) Rotation: If a car turns left and the same car turns right, there will be different point clouds representing the same car 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNDYyMTE3MD93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 Princeton's Modelnet40 dataset. It contains about 40 object categories (such as airplanes, tables, plants, etc.), 12,311 CAD models represented by a triangular mesh. The data is divided into 9843 training modes and 2468 test modes. As shown in the figure below, the direct way to apply deep learning on a point cloud is to transform the data into a volumetric representation. For example, a voxel mesh. This way we can train a CNN with a 3D filter without neural networks problems (the mesh provides the structure, the transformation of the mesh solves the arrangement problem, and the number of voxels is also constant). However, there are some disadvantages to this. Volume data can become very large, very fast. Let's consider a typical image size of 256 × 256 = 65536 pixels, now let's add a dimension 256x256x256 = 16777216 voxels. This is a large amount of data (although GPUs have been evolving). This also means very slow processing time. Therefore, usually we need to compromise and take a lower resolution (some methods use 64x64x64), but it comes with the cost of quantization error. So, the solution required is a direct deep learning approach that will be the focus of deep learning for 3D point cloud applications. 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNDY0MTcxMD93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 The authors investigated three recently published papers, mainly for deep learning of point clouds. As shown in the figure below, shows the 3D point cloud classification accuracy publication (accuracy, year and data type), which summarizes the latest accuracy results on the dataset. And the type of data each method is processing. As can be seen, in 2015, most methods were used for multi-view data (that's a short way of saying it - let's take a few photos of the 3D model and process them using 2D methods), 2016 saw a significant increase in point cloud learning using voxel representation and 2017 saw a significant increase in point-based methods. PointNet (CVPR2017) Trailblazer! Coming from Stanford University, their work got a lot of attention. They did something surprisingly simple and proved why it works well, they trained an MLP on each point separately (sharing weights between points). Each point was "projected" into a 1024 dimensional space. They then solved the point cloud ordering problem with a point symmetry function (max-pool). This provided each point cloud with a 1 x 1024 global feature that was fed into a nonlinear classifier. The rotation problem was solved using a "mini-network" they called T-net. It learned the transformation matrix on points (3 x 3) and intermediate features (64 x 64). Calling it "mini" is a bit misleading, as it is actually related to the size of the main network. Also, due to the large increase in the number of parameters, a loss term is introduced to constrain the 64 × 64 matrix to be close to orthogonal. Parts segmentation is also done using a similar network. Scene semantic segmentation is also done. Well done! I highly recommend reading (or you can also watch the demo video). The accuracy of this article on the ModelNet40 dataset is as high as 89.2%. The figure below is a framework for pointNet point cloud classification. Cited by: Charles R. Qi, Hao Su, Kaichun Mo, and Leonidas J. Guibas. Pointnet: Deep learning on point sets for 3d classi cation and segmentation. In The IEEE Conference on Computer Vision and Pattern Recognition (CVPR), July 2017. 

 The code is available on GitHub: PointNet code 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNTExNzEwMj93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 Pointnet ++ (NIPS 2017) Shortly after PointNet, Pointnet ++ was introduced. It is essentially a hierarchical version of PointNet. Each layer has three sub-stages: Sampling, Grouping, and PointNeting. In the first stage, centroids are selected, and in the second stage, adjacent points around them (within a given radius) are created to create multiple sub-point clouds. They then feed them to a PointNet network and obtain a higher-dimensional representation of these sub-point clouds. Then, they repeat the process (sample centroids, finding their neighbors and a higher-order representation of Pointnet to obtain a higher-dimensional representation). Use 3 of these network layers. Some different aggregation methods at different levels were also tested to overcome differences in sampling density (a big problem for most sensors, dense samples when objects are close and sparse when far away). They improved on the prototype PointNet and achieved 90.7% accuracy on the ModelNet40. Below is the Pointnet ++ architecture. Citation: Charles R Qi, Li Yi, Hao Su, and Leonidas J Guibas. Pointnet ++: Deep hierarchical feature learning on point sets in a metric space.arXiv preprint arXiv: 1706.02413, 2017. 

 Kd-Network (ICCV 2017) This paper uses the famous Kd tree to create a point cloud in a point cloud with a certain order structure. Once the point cloud is structured, they learn the weights of each node in the tree (representing the subdivision along a specific axis). Each coordinate axis shares weights at a single tree level All the greens in the figure below have shared weights because they subdivide the data along the x dimension. The spatial subdivision of random and deterministic was tested and it was shown that the random version works best. But at the same time some disadvantages are also stated. Sensitive to rotation (because it changes the tree structure) and noise (if it changes the tree structure). For each input point cloud data, upsampling, downsampling, or training a new model is required. 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNTI0ODk5NT93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 90.6% accuracy dataset of 1024 points (depth 10 trees) and 91.8% accuracy of~ 32K points (depth 15 trees) are reported on Modelnet40. Partial point cloud segmentation, shape retrieval, and other tree structures can be tried in later work. Reference: Roman Klokov and Victor Lempitsky. Escape from cells: Deep kd-networks for the recognition of 3d point cloud models.arXiv preprint arXiv: 1704.01222, 2017. 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNTMzNTEwND93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 ![avatar]( aHR0cHM6Ly9pbWctYmxvZy5jc2RuLm5ldC8yMDE4MDMyMjExNTQwNTk2Mj93YXRlcm1hcmsvMi90ZXh0L0x5OWliRzluTG1OelpHNHVibVYwTDNVd01UTXdNVGt5T1RZPS9mb250LzVhNkw1TDJUL2ZvbnRzaXplLzQwMC9maWxsL0kwSkJRa0ZDTUE9PS9kaXNzb2x2ZS83MA) 

 Summary: Pointnet and Pointnet ++ use symmetric functions to solve sequential problems, while kd-Network uses Kd-tree. Kd trees also solve structural problems, while each point in PointNets MLP is trained separately. The article is translated http://www.itzikbs.com/3d-point-cloud-classification-using-deep-learning, if you have any questions, please point out that the record of taking notes in this way makes my understanding of the article more profound. At the same time ** Welcome to follow the WeChat official account or join the 3D visual WeChat group to communicate and share ** *  
