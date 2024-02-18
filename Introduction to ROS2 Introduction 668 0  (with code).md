The paper reading module will share articles related to point cloud processing, SLAM, 3D vision, and high-precision maps. Official account is dedicated to the sharing of dry goods related to understanding the field of 3D vision. Welcome to join me. We will read an article every day and start the sharing journey. If you are interested, please contact WeChat dianyunpcl@163.com. 

 foreword 

 In 2017, the first official version of ROS 2, the open-source operating system software for robots, was finally launched. The new version was named "Ardent Apalone" and codenamed "ardent". 

 ROS2 is the new ROS version. Compared with ROS1, it is closer to the industrial scene, more stable and richer in functions. Let's take a look at the infrastructure of ROS2 before installing and learning. 

 The differences between ROS and ROS2 architectures 

 ![avatar]( 238fbb398869a1dec045212888aa9cba.png) 

 Architecture diagram (there is no master center node in ROS2) 

 ![avatar]( ba1c3a5678a04df0b6ec95e7fdff8435.gif) 

 ROS data publishing and subscription 

 ![avatar]( b8a615e918fd577b5ce381b9c4b5c758.png) 

 ROS2 data publishing and subscription 

 The relationship between ROS2 and DDS 

 ROS2 is based on DDS/RTPS as middleware, which provides discovery, serialization, and data transportation capabilities. 

 What is DDS (Data Distribution Service)? 

 DDS (Data Distribution Service) is an industry standard implemented by various vendors. DDS is an end-to-end middleware that provides some of the relevant features of ROS systems, such as distributed discovery, centralized discovery methods in non-ROS1, and control of data transfer in different "Quality of Service" options. 

 In order to use a DDS/RTPS implementation in ROS2, the ROS Middleware interface (or RMW for short) software package is designed in ROS2, which can realize the abstraction of the ROS middleware interface when using the DDS/RTPS API or tools. The process of using RMW to support DDS requires a lot of implementation and maintenance work. The first implementation of DDS support can ensure that the framework code of ROS2 does not need to try other special implementations. At the same time, users also want to separate DDS from their application projects. 

 DDS is divided into several logical networks in a physical network based on the Domain ID. ROS2 nodes in the same domain can be freely discovered and communicated, but they cannot communicate with each other in different domains. All ROS2 nodes use domain ID 0 by default. In order to avoid message confusion, different groups of devices running ROS2 in the same network should use different domain IDs. ROS_DOMAIN_ID there are two types (short version/long version). The recommended short version is used normally. Select between [0,101], and the long version can be selected between [0,232]. 

 Advantages of DDS: 

 (1) DDS (Data Distribution Service) is based on the design concept of data as the core, and defines a standard technology for describing data content/interaction behavior and service quality requirements in a network environment. 

 (2) DDS (Data Distribution Service) industrial-grade middleware, dynamic discovery of communication nodes, and high communication efficiency through shared memory. 

 (3) DDS makes the communication topology of all nodes rely on the P2P self-discovery model, without a master central node. 

 (4) Under this model, distributed nodes transmit data on the network in the form of publications or subscriptions. Nodes can be publishers or subscribers, or both publishers and subscribers. 

 (5) Data objects in the network are identified by topics, and distributed nodes publish or subscribe to information on topics of interest in the global data space. 

 (6) Each node has no master-slave relationship logically, and the relationship between points is equal. The communication method can be point-to-point, point-to-many, many-to-many, etc., establishing a connection under the control of QoS, and automatically discovering and configuring network parameters. 

 Disadvantages of DDS: 

 The resource consumption of the DDS itself. 

 The DDS interface is complex. 

 DDS Composition Model 

 (1) All members in the DDS are Entities, and any two Entities (entity roles) in the DDS must communicate within the same Domain, that is, the DomainID is the same when they are initialized, and the DomainID of different Domains must be unique. The DomainParticipant in the Domain is the entry point of the service. Any DDS application must first obtain the DomainParticipant, and then obtain other services through the Domain Participant, such as Publisher, Subscriber, Topic, etc. 

 ![avatar]( 1c01ac49078c02cb0e30013c5fe18613.png) 

 (2) Quality of Service Policy (QoS), the DDS specification defines a rich quality of service policy (Quality of Services Policies), QoS is a network transmission policy, the application specifies the required network transmission quality behavior, QoS services to achieve this behavior requirements, as far as possible to meet customer demand for communication quality, DDS defines a QoS policy to make it highly adaptable and robust to complex network environments, optimizing network transmission quality. 

 Comparison of ROS2 and ROS1 

 The differences between modules and ROS in ROS2 

 Participant (Domain Participant): A Participant Participant is a container, corresponding to a user who uses DDS. Any user of DDS must access the global data space through Participant. 

 Publisher: An executor of data publishing that supports publishing of multiple data types and can be associated with multiple data writers to publish messages on one or more topics. 

 Subscriber: An executor of data subscriptions that supports subscriptions of multiple data types and can be associated with multiple data readers to subscribe to messages on one or more topics. 

 Data Writers: Objects that apply updates to publishers, each corresponding to a specific Topic, similar to a message publisher in ROS1. 

 Data Reader (DataReader): An object that applies to read data from subscribers, each corresponding to a specific Topic, similar to a subscriber in ROS1. 

 Topic: This is consistent with the concept of Topic in ROS1, where a Topic contains a name and a data structure. 

 QoS Policy: Quality of Service, the principle of quality service, is responsible for data quality. QoS is a very important part of DDS, which controls the communication mechanism between all aspects and the underlying layer, mainly from the aspects of time limit, reliability, continuity, and historical records to meet the data application needs of users for different scenarios. 

 The problem with ROS 

 So what are the advantages of ROS2 over ROS1? 

 ![avatar]( 7e19ec57e72c7cc58708024de8ff6c11.png) 

 ROS2 extension to the system platform 

 ROS 1 is mainly built on Linux systems and mainly supports Ubuntu. ROS 2 adopts a new architecture, the underlying layer is based on DDS (Data Distribution Service) communication mechanism, and supports real-time, embedded, distributed, and multi-operating systems. ROS 2 supports systems including Linux, windows, Mac, RTOS, and even bare metal without operating systems such as microcontrollers. 

 compilation system 

 The ROS compilation system is from rosbuild in the early days, to catkin after groovy version, and then to ament in ROS2. The new compilation system of ROS2, ament, is a meta-compilation system used to build multiple independent functional packages that make up an application. It is not a completely new thing. It is a further evolved version of the catkin compilation system. In ROS 2, only isolated builds are supported, that is, each package is built independently, and the installation space can be isolated or merged. 

 Other comparisons 

 summarize 

 Real-time enhancements: Published data is updated before the end. 

 Continuous enhancement: Although ROS1 has the concept of data queues, it still has great limitations, and subscribers cannot receive data before joining the network; DDS can provide data history services for ROS, even if a new node joins, it can also obtain all the historical data published. 

 Reliability enhancement: By configuring reliability principles through DDS, users can choose performance mode (BEST_EFFORT) or stable mode (RELIABLE) according to their needs. 

 References 

 https://cloud.tencent.com/developer/article/1386970 

 https://www.guyuehome.com/35448 

 resource 

 3D point cloud paper and related application sharing 

 [Point cloud paper speed reading] Odometer based on lidar and positioning method in 3D point cloud map 

 3D object detection: MV3D-Net 

 Overview of 3D Point Cloud Segmentation (Part 1) 

 3D-MiniNet: Learning 2D Representations from Point Clouds for Fast and Efficient 3D LIDAR Semantic Segmentation (2020) 

 Use QT to add VTK plug-in under win to realize point cloud visualization GUI 

 JSNet: Joint Instances and Semantic Segmentation for 3D Point Clouds 

 A Survey of Semantic Segmentation of 3D Point Cloud in Large Scene 

 The outofcore module in PCL---Display of large-scale point clouds based on out-of-core octree 

 Target Segmentation Based on Local Convex 

 Point cloud labeling based on 3D convolutional neural networks 

 SuperVoxel of Point Cloud 

 Large-scale point cloud segmentation based on hyperdot graph 

 More articles can be viewed: A summary of historical articles on point cloud learning 

 SLAM and AR related sharing 

 [Open source solution sharing] ORB-SLAM3 is open source! 

 AVP-SLAM: Semantic SLAM in Automatic Parking Systems 

 [Point Cloud Paper Speed Reading] StructSLAM: Structured Line Feature SLAM 

 SLAM and AR Overview 

 Commonly used 3D depth cameras 

 Overview and Evaluation of Monocular Vision Inertial Navigation SLAM Algorithm for AR Devices 

 SLAM Review (4) Laser and Vision Fusion SLAM 

 Kimera's Semantic SLAM System for Real-Time Reconstruction 

 Overview of SLAM (3) - Vision and inertial navigation, vision and deep learning SLAM 

 Extensible SLAM Framework - OpenVSLAM 

 Gao Xiang: Challenges in unstructured road laser SLAM 

 SLAM Overview of Lidar SLAM 

 SLAM Method Based on Fisheye Camera 

 If you are interested in this article, please send "Knowledge Planet" in the background to get the QR code. Be sure to join the free Knowledge Planet according to the remarks of "Name + School/Company + Research Direction", download the pdf document for free, and communicate with more friends who love to share! 

