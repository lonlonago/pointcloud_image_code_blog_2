Point cloud PCL free knowledge planet, point cloud paper speed reading. 

 标题：HoPE: Horizontal Plane Extractor for Cluttered 3D Scenes 

 作者：Dong, Zhipeng and Gao, Yi and Zhang, Jinfeng and Yan 

 Planet ID: particle 

 Welcome to join the free knowledge planet, get PDF papers, and welcome to forward Moments to share your happiness. 

 Abstracts of papers 

 Extracting horizontal planes in a messy 3D scene is a fundamental step in many robotic applications. Aiming at the limitations of general plane segmentation methods on this issue, we propose a new algorithm for plane extraction, which can efficiently extract planes in messy ordered point clouds or disordered point cloud data. The sensor orientation obtained by pre-calibration or inertial measurement units converts the source point cloud into a reference coordinate system, and proposes an improved region growth algorithm combined with the Z-axis clustering algorithm, a method for point cloud clustering and segmentation based on principal component analysis (PCA). In addition, we also propose a nearest neighbor plane matching (NNPM) strategy to maintain the stability of extracted planes in continuous sequences. Qualitative and quantitative evaluation of real and synthetic scenarios shows that our method outperforms several state-of-the-art methods in terms of robustness, accuracy and efficiency in processing noisy point cloud data. And the algorithm has been open-sourced on github: https://github.com/DrawZeroPoint/hope 

 Main contributions 

 (1) Transform the point cloud data according to the orientation angle of the 3D point cloud acquisition device to simplify the process of horizontal extraction, and provide a fast and robust method for point cloud clustering, segmentation and recognition. 

 (2) Reduce the number of thresholds used in a reasonable way to reduce the instability of the algorithm, and achieve better segmentation results with expected accuracy and efficient computing time. 

 (3) Compatible with Point Cloud Library PCL and Robot Operating System (ROS) and open source. 

 Paper Atlas 

 ![avatar]( 20200524221057647.JPG) 

  Algorithm flow of multiplane extraction 

 ![avatar]( 20200524221113632.JPG) 

 This paper proposes a framework for extracting organized and unorganized 3D point clouds from multiple levels in chaotic scenarios. Taking full advantage of the directional information of the collected point cloud data and simplifying the process including downsampling, point cloud clustering, refinement, and result recognition, the algorithm uses prior knowledge of the sensor orientation in the first stage to transform the source point cloud into a reference point cloud with its z-axis pointing upward. The framework provides some specialized and novel features that can provide robust and efficient results. And the potential advantage of the framework lies in the variability of scene size and its ability to continuously identify the extracted content. Experiments on real-world datasets show that our method can maintain the consistency of the results even in dynamic scenarios. 

 ● English abstract 

 ![avatar]( 20200524221142704.JPG) 

 Extracting horizontal planes in heavily cluttered three-dimensional (3D) scenes is an essential procedure for many robotic applications. Aiming at the limitations of general plane segmentation methods on this subject, we present HoPE, a Horizontal Plane Extractor that is able to extract multiple horizontal planes in cluttered scenes with both organized and unorganized 3D point clouds. It transforms the source point cloud in the ﬁrst stage to the reference coordinate frame using the sensor orientation acquired either by pre-calibration or an inertial measurement unit, thereby leveraging the inner structure of the transformed point cloud to ease the subsequent processes that use two concise thresholds for producing the results. A revised region growing algorithm named Z clustering and a principal component analysis (PCA)-based approach are presented for point clustering and reﬁnement, respectively. Furthermore, we provide a nearest neighbor plane matching (NNPM) strategy to preserve the identities of extracted planes across successive sequences. Qualitative and quantitative evaluations of both real and synthetic scenes demonstrate that our approach outperforms several state-of-the-art methods under challenging circumstances, in terms of robustness to clutter, accuracy, and efﬁciency. We make our algorithm an off-the-shelf toolbox which is publicly available.  

