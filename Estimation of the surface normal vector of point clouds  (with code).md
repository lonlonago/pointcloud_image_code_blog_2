The point cloud surface normal vector is an important geometric surface property that has a wide range of applications in computer imaging, such as determining a reasonable light source position when performing lighting rendering and other visualizations. It is usually not difficult to estimate the surface normal vector from the known determined geometric surface. But there are usually two schemes for estimating the corresponding normal vector from a set of actual surface point cloud data obtained: 

 theoretical basis 

 Although there are many methods for estimating the normal vector of point clouds, we will focus on the simplest one, which works as follows. The problem of estimating a normal vector at a point on a surface is similar to the problem of estimating the normal vector of a plane tangent to the surface, so the problem is transformed into a least squares fitting estimation problem. 

 Note: More details are found in Mr. Rusu's "Semantic 3D Object Maps for Everyday Manipulation in Human Living Environments", a third of which deals with some of the early processing of 3D data, and the remaining two thirds are applications of actual robots in scene semantic recognition. 

 Solving the normal vector problem at a point by the least squares method is actually transformed into a process of solving the eigenvalues and eigenvectors of a covariance matrix (also known as PCA principal component analysis). 

 Where a, b, c are the normal vector of the pre-solved plane, normal vector n = (a, b, c). From the knowledge of spatial analytic geometry, the normal vector corresponds to the value corresponding to the smallest eigenvalue. 

 The above are just some purely mathematical theoretical derivations, implemented in PCL by calling relevant functions. 

 Function Implementation in PCL 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573714700
  ```  
 However, there is a general direction problem in the solution of the vector, and the normal vector obtained by the above method also has inconsistent directions. For this problem, there are usually two solutions. 

 Selecting an appropriate scale: The above normal vector estimation is actually an estimation of the k-nearest neighbor or r-neighborhood determined by a certain point in the point set as a query point. The selection of k or r is very important for the estimation of normal vector and curvature. In general, if the details of a feature are very high, k or r should be taken on a small scale, and vice versa. 

 Normal vector estimation code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573714700
  ```  
 The algorithm flow is as follows: For each point p in the point cloud P: (1) get the nearest neighbor of the point p or determine a neighborhood by the radius r; (2) calculate the normal vector of the point p; (3) check the consistency of the normal vector, inconsistent flip. 

 Using OpenMP acceleration 

 In practical applications, if the computing speed is required, you can use the additional implementation program provided by PCL to develop multi-threaded. The class is named pcl:: NormaleEstimationOMP to achieve. 

 At present, the WeChat exchange group is growing, due to the large number of people, there are currently two groups, in order to encourage everyone to share, we hope that everyone can actively share while learning, and send your questions or small summary submissions to the group owner mailbox main mailbox dianyunpcl@163.com. 

 If the above content is wrong or needs to be added, please leave a message! At the same time, everyone is welcome to pay attention to the WeChat official account, actively share submissions, or join the 3D visual WeChat group or QQ exchange group. 

 ![avatar]( 20200121193829858.jpeg) 

 Original is not easy, please contact the blogger for reprinting and indicate the source.  

