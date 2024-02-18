![avatar]( 20200508212909935.JPG) 

 This paper introduces a visual SLAM framework with high usability and extensibility - OpenVSLAM. Visual SLAM systems are essential for autonomous control of AR devices, robots and drones, etc. However, traditional open source visual SLAM frameworks are not properly designed like libraries called from third-party programs. To overcome this situation, we have developed a new visual SLAM framework. The software is simple in design, easy to use and extend. It contains some useful features and functions for research and development. OpenVSLAM was published on https://github.com/xdspacelab/OpenVSLAM 

 Detailed introduction and comparison 

 ![avatar]( 20200508212845234.gif) 

  In the introduction, the article highly affirms that ORB - SLAM [10, 11], LSD - SLAM [4], and DSO [3] are pioneering visual SLAM solutions. However, in terms of usability and scalability, they have not properly designed SLAM libraries in terms of ease of use and scalability. Therefore, researchers and engineers must strive to apply these SLAM systems to their applications. In other words, it is inconvenient to use existing open-source software for visual SLAM as a way to model and build maps from 3D, such as autonomous control of robots and unmanned aerial vehicles (UAVs), and augmented reality (AR) on mobile devices. Therefore, it is very valuable to provide an open-source visual SLAM framework that is easy to use and easy to extend by users.  

 OpenVSLAM Advantages 

 OpenVSLAM is a monocular, stereoscopic and RGBD visual SLAM system, which belongs to the direct method based on sparse features. Its main differences in contributions are: (1) Compatible with various types of camera models, which can be well adapted to the camera model selected by the user. The system can handle various types of camera models, such as perspective, fisheye, and isorectangle maps. If necessary, users can easily implement additional camera models (such as Pisces Eye, catadiopractive, etc.). (2) Operations such as loading and storing the created map can be performed, and the project can perform positioning operations based on pre-built maps. (3) The system is fully modular, and it is packaged by api that will carry out some easy-to-understand function functions. (4) Code engineering provides some code snippets to assist in understanding the core functions of the entire system. Please refer to the * .cc file in the./example directory, or view simple tutorials and examples. 

 The installation tutorial and the use tutorial are very detailed. If you are interested, you can follow the tutorial step by step. 

 Sparse vision SLAM 

 • MonoSLAM: (Monocular Camera) is the first real-time single SLAM system based on EKF [14]. • PTAM: (Monocular Camera) is the first SLAM system to track and build maps in parallel. It first employs bundle adjustment to optimize the concept of keyframes [15]. Higher versions support simple and efficient repositioning [16]. • ORB-SLAM: It (Monocular) uses three threads: tracking, building maps, and closed-loop detection [17]. ORBSLAM v2 [18] supports monocular, stereo, and RGB-D cameras. CubemapSLAM [19] is a monocular fisheye lens SLAM system based on ORB-SLAM. • Visual inertia ORB-SLAM [20] explains the initialization process of the IMU as well as joint optimization using visual information. • proSLAM: (Stereo Camera) is a lightweight visual SLAM system and is easy to understand [21]. • ENFT-sfm: (Monocular Camera) is a feature tracking method that efficiently matches feature point correspondence between one or more video sequences [22]. The newer version ENFT-SLAM can be run at scale. • OpenVSLAm: (supports all types of cameras) [23] is based on an indirect SLAM algorithm with sparse features. The advantage of OpenVSLAM is that the system supports perspective views, fisheye diagrams and isometric rectangles, and even supports any user-designed camera model. • TagSLAM: It implements SLAM via the AprilTag benchmark [24]. Moreover, it provides a front-end to the GTSAM factor graph optimizer that can design a large number of experiments. Other similar efforts can be listed below, but are not limited to UcoSLAM [25]. 

 The purpose of open source 

 Visual SLAM is considered the next generation of technology to support industries such as automotive, robotics, and xR. We are releasing OpenVSLAM as an open source project with the goal of working with people around the world to accelerate the development of this field. In return, we hope this project will bring safe and reliable technology to a better society. 

 ![avatar]( 20200508212935104.JPG) 

 ![avatar]( 20200508213002561.JPG) 

 Main modules of OpenVSLAM: tracking, map building, and global optimization modules. Comparison of ORB-SLAM path error statistics, references 

 [1] Raúl Mur-Artal, J. M. M. Montiel, and Juan D. Tardós. 2015. ORB–SLAM: a Versatile and Accurate Monocular SLAM System. IEEE Transactions on Robotics 31, 5 (2015), 1147–1163. https://doi.org/10.1109/TRO.2015.2463671 

 [２] Raúl Mur-Artal and Juan D. Tardós. 2017. ORB–SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras. IEEE Transactions on Robotics 33, 5 (2017), 1255–1262. https://doi.org/10.1109/TRO.2017.2705103 

 [3] Jakob Engel, Vladlen Koltun, and Daniel Cremers. 2018. Direct Sparse Odometry. IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI) 40, 3 (2018), 611–625. https://doi.org/10.1109/TPAMI.2017.2658577 

 [4] Jakob Engel, Thomas Schöps, and Daniel Cremers. 2014. LSD–SLAM: Large-Scale Direct Monocular SLAM. In Proceedings of European Conference on Computer Vision (ECCV). 834–849. https://doi.org/10.1007/978-3-319-10605-2_54 

 resource 

 CVPR2020 Papers CenterMask Interpretation 3D object detection: MV3D-Net 3D-MiniNet: Learning 2D representations from point clouds for fast and efficient 3D LIDAR semantic segmentation (2020) Point cloud visualization using QT add VTK plugin under win GUI JSNet: Joint instance and semantic segmentation of 3D point clouds, a review of semantic segmentation of 3D point clouds in large scenes outofcore module in PCL - Display of large-scale point clouds based on extranuclear octree, Target segmentation based on local irregularities, Point cloud labeling based on 3D convolutional neural networks, SuperVoxel of point clouds Large-scale point cloud segmentation based on hyperdot graphs, Introduction to SLAM method based on fisheye camera, Point cloud learning history article Dahui total 

 If you are interested in this article, please click "Original Reading" to get the QR code of Knowledge Planet. Be sure to join the free Knowledge Planet according to the remarks of "Name + School/Company + Research Direction", download the original pdf document for free, and communicate with more friends who love to share! 

 ![avatar]( 20200508213041631.png) 

