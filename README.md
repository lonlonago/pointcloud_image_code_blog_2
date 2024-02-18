Requirements: Obtain speed information (angular velocity + linear velocity) in geometry_msgs :: TwistStamped format Method 1: Obtain the linear velocity from the chassis, imu obtain the yaw angular velocity data, and then combine the data to publish information. Method 2: By fusing the pose (x, y, yaw) of the positioning output, calculate the linear velocity and yaw angular velocity through the front and rear frames, and then publish the information. Method 1 implements: Header file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 Implementation file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 main： 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 To launch: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 Method 2 implementation: header file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 Implementation file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 Mian file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  
 To launch: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573727016
  ```  


--------------------------------------------------------------------------------

Recently, in the WeChat group, many group friends have purchased Astra Pro's depth camera under the recommendation of group friends. The price is authentic and the value for money is excellent! The feedback from group friends is positive, so there is a wave of simple tutorials here. 

 The following content knowledge is helpful, mainly to explain the test cases under Windows and Ubuntu. 

 (1) Astra Pro parameters 

 ![avatar]( 20191220184807421.png) 

 The depth camera is a somatosensory camera cooperated by LeTV and Obi Zhongguang, benchmarking Microsoft Kinect, which can be used for 3D reconstruction, SLAM learning, and can also be used as a drive-free UVC camera somatosensory camera. Camera parameters  

 ![avatar]( 20191220184833271.png) 

 Then the camera driver is also very complete, support Windows, Android, linux, and Unity, the specific driver can visit the official website: https://orbbec3d.com/download-sdk/  

 ![avatar]( 2019122018484596.png) 

 (2) Windows 10 64-bit test tutorial, according to the plan provided by the website, we can have two ways: one is to directly download and install the camera driver to run the demo, and the other is to test the demo under VS. For simple testing, we use the first type. After installing the driver, run the OpenNI test demo directly to download the driver, and download the openNI development package after installation. You can directly open the test. After decompression, plug it into the USB port of the camera. 

 ![avatar]( 20191220184906720.png) 

  Open the OBNiViewer application in the Astra OpenNI2 Development Instruction (x64) _V1\ Tools\ OBNiViewer directory. 

 ![avatar]( 20191220184914687.png) 

  The second is to test under VS. We open the VS project in the following directory without modifying the properties, and run it directly after compilation.    

 The above is a simple test under windows, which is relatively simple, because the official website provides detailed test cases. It can run normally without too many modifications. 

 (2) The test in the Ubuntu 16.04 environment, the test under Ubuntu, first we need to install the necessary dependencies and open the command serial port. Run the command line, sudo apt-get install build-essential freeglut3-dev If it prompts that other installation packages are missing, you need to use sudo apt-get install + yourself (the suggested dependency name) 

 ![avatar]( 20191220185058115.png) 

 Download the two installation packages, unzip them respectively, and open the command window under~/astra/AstraSDK-Linux/install 

 ![avatar]( 20191220185113559.png) 

 sudo sh. / install.sh Home  

 Prompt us to add path information in environment variables, then the command line, or directly double-click to open the .brshrc environment configuration article to add 

 ![avatar]( 20191220185248190.png) 

 ![avatar]( 20191220185307988.png) 

 export ASTRA_SDK_INCLUDE=/home/yao123/astra/AstraSDK-Linux/install/include export ASTRA_SDK_LIB=/home/yao123/astra/AstraSDK-Linux/install/lib  保存后使用命令行source ~/.bashrc使之有效。 

 * Choose the archive with your own system has been OpenNI_2 3.0.55 unzip OpenNI-Linux-x64-2.3.zip cd~/astra/OpenNI_2 3.0.55/Linux/Op enNI - Linux - x 64 - 2.3.0.55 install sudo chmod a + x install.sh sudo./install.sh 

 Replug device 

 ![avatar]( 20191220185345831.png) 

 ![avatar]( 20191220185359653.png) 

 Add environment source OpenNIDevEnvironment compile example cd Samples/SimpleViewer make connect the device, mine is a virtual machine, so you need to manually check whether the device is connected in the option of the virtual machine, and then execute the example cd Bin/x64-Release./SimpleViewer to display the normal view 

 ![avatar]( 20191220185431471.png) 

 ![avatar]( 20191220185459857.png) 

 ROS under the test steps, familiar with ROS here is not one by one to explain the installation of ROS environment, here because I use the 16.04 version of Ubuntu so here to install the Kinetic version of ROS, if you do not have their own ROS workspace, then you can directly use the command line to install sudo apt-get install ros-kinetic-astra-camera ros-kinetic-astra-launch if no accident should be installed successfully, of course, if you want to read the source code, you can create a ROS workspace yourself, source code compilation, after the installation is successful, we can follow the steps of normal ros operation and visualization, the first is to start roscore If this step is not started, indicating that your ROS environment variables are not set, you can use the following command line can source it, then start roscore after opening, new end Point, execute astra_launch roslaunch astra_launch astra.launch Use rqt_image_view, select the corresponding topic to display an image, such as the original depth map I displayed. Is my shadow 

 ![avatar]( 20191220185524140.png) 

 ![avatar]( 20191220185537735.png) 

 When we selected the corresponding ROS topic, we found that rgb is not displayed correctly! Because UVC support is required, we need to install libuvc and libuvc_ros installation steps. Installing libuvc supports $cd~ $git clone https://github.com/ktossell/libuvc $cd libuvc $mkdir build $cd build $cmake... $make & & sudo make install  

 Next, install libuvc_ros If you don't have ROS workspace, you can do the following 

 Mkdir -p~/catkin_ws/src cd~/catkin_ws/src catkin_init_workspace (generate the corresponding CMakeLists.txt) cd~/catkin_ws/catkin_make (After executing this command, I found that there are three directories in the workspace catkin_ws: build devel src) source devel/setup.bash (set environment variables) echo $ROS_PACKAGE_PATH (view current environment variables) 

 At this point, our ROS workspace is created. At this time, we need to download libuvc_ros development package and enter our workspace cd~/catkin_ws/src git clone https://github.com/ros-drivers/libuvc_ros.git cd... catkin_make After the compilation is successful, test it. After starting roscore, use rosrun libuvc_camera camera_node run rqt_image_view to view rgb images 

 Test completed 

 ![avatar]( 20191220185547637.png) 

 The above is the whole content. There may be some wrong welcome instructions, and you can send emails to communicate. You can follow the WeChat official account. Join our translation team or join the WeChat official account group, and also join the technical exchange group to communicate with more friends.  



--------------------------------------------------------------------------------

>  GitHub地址：point-cloud-viewer GitCode地址：point-cloud-viewer 

 The author started to design and implement this point cloud processing and 3D reconstruction software Point Cloud Viewer, PCV at the end of 2021. It took three months to complete most of the functions of the software. Since the author switched to embedded bottom-level related work and stopped researching point cloud processing related technologies, the subsequent function implementation of PCV has been stranded. When writing this software, there was a lack of relevant information for technical selection. In order to avoid detours for students who are interested in point cloud processing software development, this software is now open-sourced. Students can refer to the framework of this software to design and implement their own point cloud processing software. PCV is a software based on integrated point cloud display and point cloud processing. The point cloud processing function mainly includes the following functions: 

 The software is implemented by Qt design, its interface design refers to Cloud Compare, and the kernel algorithm is implemented based on the point cloud processing tool library PCL. See below for specific design and implementation details. 

 ![avatar]( 8dee241aeb674563adc018e42fda9c41.png) 

 Here are some demos:  

 ![avatar]( a33d787ca71c462894cc3824d4e37985.gif) 

 ![avatar]( 5fd5e4aa361346f5922796d2b11520df.gif) 

#  Use tutorials and related tool libraries 

 The following table is the technical solution adopted by this software. If you want to run through this project, it is recommended to refer to the following table: 

##  Step 1 Build the environment 

##  Step 2 Build the project with Cmake 

 This project uses Cmake to build the project: 

 ![avatar]( bb7658982d094ee3a0c0ebb303371ec5.png) 

 The most important of these is the writing of CMakeLists.txt: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573782929
  ```  
 Specific usage methods: 

 ![avatar]( eef256f5c15847adb6c8ce7a55305b21.png) 

##  Step3 Use VS to write code and compile execution 

 ![avatar]( d99787a7b822495a994f4362dcf7ec77.png) 

 After the build is completed, there is a PointCloudViewer.sln file in the output folder, which can be opened using VS   

 If there is a problem that the program cannot be started, please refer to the blog post: 

 The solution to the problem that the project compiled and generated by using CMake + Visual Studio cannot start the program 

 Set PointCloudViewer as the startup project: 

 ![avatar]( dc4025a7225f4061aed22080bbe67b6a.png) 

#  Design and Implementation of Point Cloud Processing and 3D Reconstruction Software 

 This chapter will focus on the overall design, function development and running test of Point Cloud Veiwer (PCV). 

#  First, the overall design of the software 

 Before designing the point cloud processing and 3D reconstruction software in this paper, two general software design guidelines need to be followed: 

##  1.1 Software design process 

 Figure 1 shows the design flow chart of the point cloud processing and 3D reconstruction software in this paper. The design and implementation of a mature and reliable software first requires complete and clear design ideas and compliance with standardized software system design principles. 

 ![avatar]( 9516cf881c15454da4e2aa621645f435.png) 

 Fig. 1 Design flow of point cloud processing and 3D reconstruction software 

 From Figure 1, it can be seen that the design process of this software mainly involves six major steps: 

###  demand analysis 

 Before the software is designed and implemented, it is necessary to analyze the user request, that is, to clarify what functions the current software needs to achieve and the final effect to be achieved, in order to solve the problems currently encountered by the user. As shown in Table 1, the requirements analysis table for the point cloud processing and 3D reconstruction software designed and implemented in this chapter. 

 Table 1 Function list of point cloud processing and 3D reconstruction software 

###  overall design 

 After the requirements analysis, design the overall architecture of the software and determine its various functional modules. The overall architecture of the software is shown in Figure 2. 

###  Technology selection 

 Developers choose the appropriate software and hardware environment for software development according to the current budget, development cycle and the developer's own knowledge reserve. This process is called technology selection. According to the actual situation, after studying and judging the current key technologies of point cloud 3D reconstruction, the technology selection list for point cloud processing and 3D reconstruction software development is shown in Table 2. 

 Table 2 Selection of point cloud processing and 3D reconstruction software technologies 

###  detailed design 

 After the overall design and technical selection of the software, the technical direction and functional modules of the software have been preliminarily determined. The next step is to carry out specific design of each functional module. For example, the design or selection of algorithms in the module, the design of the operation interface and so on. 

###  Function implementation 

 After the detailed design of the software, the specific functions of the software are developed and realized, mainly including the development of the software interface and the implementation of the algorithm code related to the key technology of 3D reconstruction. 

###  Run the test 

 After the software development is completed, it is necessary to test the software by using some point cloud data with large data volume and complex surface characteristics as input to test the extreme performance of the software. 

##  1.2 Software Composition Structure 

 Figure 2 shows the overall architecture diagram of the point cloud processing and 3D reconstruction software designed in this paper. It can be seen from the figure that the software in this paper can be mainly divided into three functional modules: point cloud IO module, point cloud processing module and 3D visualization module. 

 ![avatar]( a79ec1071b3b4993bfdb3502ca89bcf3.png) 

 Figure 2 Point cloud processing and 3D reconstruction software architecture diagram 

 The following is a brief description of these three main functional modules: 

###  Point Cloud IO Module 

 The point cloud IO (Input/Output) module is mainly responsible for reading, converting and saving point cloud data. It is worth mentioning that this software has two point cloud reading methods: one is to establish communication with the lidar, read the point cloud data scanned by the lidar in real time, and save it locally. The currently supported lidar brands are Velodyne and Radium God. The second is to directly read the existing point cloud data files. The file formats currently supported by this software are: PCD, PLY, STL, PCAP, TXT and OBJ and other 6 formats, and support the mutual conversion of these formats. 

###  Point cloud processing module 

 The point cloud processing module is the core functional module of this software. It has five main functions: point cloud preprocessing, point cloud registration, surface reconstruction, point cloud segmentation and point cloud attribute extraction. Among them, point cloud preprocessing, point cloud registration and surface reconstruction are the key technologies of 3D reconstruction based on lidar, which is the focus of this paper. It not only integrates various improved algorithms proposed in this paper, but also integrates a large number of classic point cloud processing algorithms at home and abroad. The selection of the algorithm has a high degree of freedom, which is convenient for users to choose the appropriate algorithm for 3D reconstruction according to the actual situation of the target point cloud to be reconstructed. In addition, point cloud segmentation and point cloud attribute extraction are developed to expand on the basis of 3D reconstruction technology, and the functions are used to assist users in solving various problems encountered in 3D reconstruction, such as segmentation and extraction of target point clouds, obtaining specific geometric properties of point clouds, etc. 

###  3D visualization module 

 The 3D visualization module mainly includes functions such as visual interface, visual display and visual operation. The visual interface consists of five parts: main window, point cloud attribute window, point cloud processing console window, toolbar, menu bar, etc. Its interface design is friendly and easy to use. The visual display and operation functions of the point cloud use the QVTKWidget plug-in to visualize the results produced in the 3D reconstruction process in real time, and can be rotated, scaled, panned and changed at will, so that users can observe the point cloud model in more detail. 

##  1.3 Software Workflow 

 The three main functional modules based on point cloud processing and 3D reconstruction software are depicted in Figure 3. 

 ![avatar]( d7cc76f0f4584cf087d344fe1ea42bf8.png) 

 Figure 3 Point cloud processing and 3D reconstruction software workflow chart 

 As can be seen from Figure 3, the main workflow of the software in this chapter consists of the following steps: 

#  Second, the software development platform and function introduction 

##  2.1 Software development platform 

###  Integrated development environment 

 The point cloud processing and 3D reconstruction software designed in this paper is mainly based on two integrated development environments, Microsoft Visual Studio 2017 and Qt Creator, to complete the code writing, analysis, compilation and debugging. In addition, this paper is mainly based on the Qt framework to complete the design of the software interface and the implementation of internal logic functions. Qt has a set of codes and runs on multiple platforms. Therefore, the software developed using this framework can not only run on operating systems such as Windows and Linux, but also on MacOS. It is precisely because of the cross-platform development characteristics of Qt that the software designed in this chapter can run normally in multiple operating systems. Not only that, Qt can also be developed in combination with PCL. By using the QVTKWidget plug-in, point cloud processing software with GUI can be developed. The integrated development environment used by Qt is Qt Creator. This chapter mainly uses this IDE to complete the design of the software UI. 

###  PCL Point Cloud Data Processing Library 

 Point Cloud Library (PCL) is referred to as PCL. It also has the characteristics of cross-platform development. It adopts the BSD open-source protocol, which not only allows developers to conduct secondary development on the basis of the PCL tool library, but also encourages domestic and foreign scholars to share their own point cloud data-related research results in the form of code. Therefore, PCL largely integrates general algorithms for point cloud data acquisition and processing at home and abroad, as well as efficient point cloud-related data structures. Commonly used algorithm modules are: surface reconstruction module, point cloud filtering module, and point cloud registration module. Commonly used point cloud-related data structures include OC-TREE and KD-TREE. Most of the algorithm implementations in this paper are based on the PCL tool library, and the algorithm source code provided by it is improved and optimized. In addition, the visualization class used in this paper is pcl < unk > PCLVisualizer, and by recompiling the source code of the Visualization Toolkit (VTK), a QVTKWidget plug-in corresponding to the PCL version is generated, which is loaded in the Qt-based visualization software to display the point cloud processing results. 

###  Compile configuration tool CMake 

 CMake is an advanced compilation (installation) configuration tool. It also supports cross-platform features, so it can output the corresponding Makefile file or Project file according to the currently selected platform (such as VS2017) and compiler (such as MSVC or MinGW, etc.). CMake is relatively simple to use. You only need to write configuration environment variables and library-dependent command statements in its configuration file (a CMake script dedicated to building projects). The CMake configuration file is named after CMakeLists.txt. The PCL, VTK, and Qt used in this article all use the CMake tool to configure the compilation environment. 

 ![avatar]( 9dc3b189701540bb868ceb3d8397463a.png) 

 Figure 4 PCL function module 

##  2.2 Software main interface design 

 Figure 5 shows the loading page when the software is started. The layout of the main interface of the software is shown in Figure 6, which refers to the foreign open-source point cloud processing software Cloud Compare. In addition, the internal logic functions of the software and the specific implementation of various algorithms are independently designed and developed by this paper. It can be seen from Figure 7 that the software has six functional areas, namely: menu bar, point cloud processing toolbar, point cloud view operation toolbar, point cloud attribute window, point cloud display main window and operation record window. 

 ![avatar]( 01243d57dfc443938089c67e1ad67193.png) 

 ![avatar]( b28db9b225784c498c0eba27dde70a74.png) 

 ![avatar]( 46dc572b3199413caf5720d99299d99a.png) 

  File menu shortcut menu 

 Figure 7 Detailed explanation of the main interface of the software 

###  Menu Bar 

 There are 13 menus in the menu bar of this software. As shown in Figure 8, in addition to the point cloud processing related function menu, there are file menu bar and shortcut menu bar in the menu bar to improve the efficiency of software use. Figure 9 is a schematic diagram of the menu related to point cloud file processing in the software. It not only supports the import and export of point clouds in various formats, but also supports the export of point cloud processing logs. Figure 9 is the shortcut menu in the software. Users can either click on the menu item or press shortcut between them to run some functions of the software, such as screen snapshots, data point size settings, and point cloud view scaling. 

 ![avatar]( b30787a8ad0b463489f586d7a49aa8dc.png) 

 ![avatar]( 46fc9fd67432496fa8f63755cc622d2a.png) 

 ![avatar]( a43a3b0b76564e04aefe386c63afa5ec.png) 

 Figure 9 File menu and shortcut menu 

###  Toolbar 

 Users can either click on the corresponding menu items in the menu bar to run specific functions, or they can quickly operate by clicking on the icon buttons in the toolbar. There are two software toolbars. Figure 10 shows the visual operation toolbar, and Table 3 shows the functional interpretation of the button icons in the toolbar. By clicking the buttons, you can quickly operate the point cloud view, such as six views to quickly view the target point cloud, point cloud rotation fixed angle, and point cloud scaling. Figure 11 shows the software algorithm toolbar, and Table 4 shows the functional interpretation of each button icon in the algorithm toolbar. The algorithm toolbar covers the operation functions related to point cloud processing, such as copy and paste of point clouds, point cloud export, and shortcuts related to point cloud 3D reconstruction. 

 ![avatar]( 3edff6f48b3a422e8957eb3476632657.png) 

 ![avatar]( e42d8e84057c427fafca5b1c5d6b72b3.png) 

 ![avatar]( 5627c8b556084a6a8e571596eb764dac.png) 

 ![avatar]( 8cc133f3ca9e44f285b794abde8be95e.png) 

 Table 3 Software visual operation toolbar icon function detailed explanation   

###  Point Cloud Properties Window and Main Window 

 The right side of Figure 12 is the main point cloud window, which is used to display the currently loaded point cloud file. Not only can you use the mouse to drag, zoom, and rotate the target point cloud, but you can also add tools such as axes and rulers to the window to facilitate the visualization of the target point cloud. The left side of Figure 12 is the main point cloud attribute window. Through this window, you can know the specific attributes of the currently loaded and selected point cloud file of the software, such as file format, file name, number of point clouds, data format, and included fields. 

 ![avatar]( d913e2b8c92f4b08a4e773363995174b.png) 

 Figure 12 Point cloud attribute window and main window 

###  Point cloud processing record window 

 Since there are many related steps in point cloud processing, in order to make the steps in the point cloud processing process clearer and clearer for users, this software specially sets up a point cloud processing record window for recording the specific details of the current point cloud operation. As shown in Figure 13, each record is mainly composed of three parts: operation time, operation result and activity details. Not only that, point cloud processing records also support one-click export, which is convenient for users to record and analyze each process in point cloud processing. 

 ![avatar]( 795072686c1149f095bf2740b3db7e37.png) 

 Figure 13 Software point cloud processing record window 

###  Software related data structures 

 The point cloud processing and 3D reconstruction software designed in this paper not only supports direct reading of point cloud data for processing, but also can read the point cloud data scanned by the lidar in real time and save it locally. Taking the Velodyne lidar as an example, after the host computer and the lidar establish network communication, the software in this paper will continuously read the UDP packets sent by the Velodyne lidar, parse the UDP packets, and save the original point cloud data locally in the form of a PCAP file. The file structure of PCAP is shown in Figure 14. The PCAP file saves the point cloud data stream. In other words, a PCAP file contains multiple frames of point cloud images, and each frame of point cloud image data has its own data header (Packet Header) and timestamp (Timestamp). In the actual point cloud processing process, there is no need for multiple frames of repeated point cloud images. Therefore, only one of the point cloud images needs to be extracted from the PCAP file and the redundant information is removed to obtain the key frame point cloud image describing the target object. There are many storage methods for single-frame point cloud images according to their uses and processing methods, such as PCD, PLY and STL formats. 

 ![avatar]( 43e40c967bbe4eb38c3e53b59b7d4d4a.png) 

 Figure 14 PCAP file structure 

 Since the software in this paper is designed and developed based on the PCL tool library, and PCL not only has the highest compatibility with the PCD format, but also has a faster reading and writing speed for PCD files than other formats, the software also chooses the PCD format as the primary format for reading and writing point cloud data. In the header of the PCD file (the first 10 lines), various attributes of the current point cloud data must be declared first. Attributes contain 10 fields, each field occupies one line. Table 5 shows the meaning of each field of the PCD. From the FIELDS field, you can know the information contained in each data point of the current point cloud. As can be seen from Table 5, for example, it means that each data point contains coordinate information. If so, it means that each data point contains each point cloud color attribute (RGB) in addition to coordinate information. In addition, the POINTS, WIDTH and HEIGTH fields have a relationship. If the current point cloud is an unordered point cloud, the value of HEIGTH is 1, and WIDTH can also represent the number of points in the current point cloud. The content after the DATA field is the data part of the point cloud. In the .7 version of PCD, formats and formats are supported. It is important to note that the various fields in the PCD file have strict order requirements and cannot be missing, and must be described in the order shown in Table 5. 

 Table 5 PCD file field meaning 

#  Third, software point cloud processing related functions 

 The point cloud processing module is mentioned in the software composition structure in Figure 2 above. The point cloud processing module includes five functions: point cloud preprocessing, point cloud registration, point cloud surface reconstruction, point cloud segmentation and point cloud attribute extraction. In addition to point cloud preprocessing, point cloud registration and surface reconstruction and other 3D reconstruction related functions, the software in this paper also expands the functions of point cloud segmentation and point cloud attribute extraction based on this. Point cloud processing related functions are the core functions of this software, including 78 excellent point cloud processing related algorithms at home and abroad, including the improved algorithms in this paper, and as many as 156 related function functions. And each point cloud processing algorithm can independently set the input parameters, and different algorithms can be freely used together. Each function is described in detail below. 

##  3.1 Point cloud preprocessing function 

 The point cloud preprocessing function mainly includes three parts: point cloud sampling, point cloud outlier removal, point cloud filtering, etc. The software in this paper integrates five algorithms including downsampling, uniform sampling and upsampling based on voxel grid in the point cloud sampling function. As shown in Figure 15 (a), there are also functions such as KD-TREE, OC-TREE and normal estimation. For outlier removal function, as shown in Figure 15 (b), the software in this paper integrates DBSCAN outlier removal algorithms based on statistics, density, and clustering. In addition, the point cloud filtering function of this software integrates 9 point cloud filtering methods including Gaussian filtering, average filtering and Laplacian filtering. Users can choose the appropriate filtering method according to the actual situation of the current point cloud. In addition, there are functions such as "one-click removal" and "one-click filtering" in the menu, which can quickly process the point cloud using pre-set algorithms and algorithm parameters. 

 ![avatar]( 4f5d49497fc94fb09a05b810c3cc87b8.png) 

 ![avatar]( 93db69dae5064dc7a43b679ced344d4f.png) 

 ![avatar]( d711403385964d4b84de10027331ba49.png) 

 Figure 15 Point cloud preprocessing related function menu 

##  3.2 Point cloud registration function 

 Point cloud registration related functions include key point extraction algorithm and point cloud registration algorithm. As shown in Figure 16 (a), it is the key point extraction related function menu. The software in this paper integrates 8 key point extraction algorithms including Agast key point, Harris key point, ISS key point and SIFT key point. And Figure 16 (b) is the function menu related to point cloud registration. It can be seen from the figure that the software in this paper integrates 9 registration algorithms including ICP, NDT, Super 4PCS and the improved Super 4PCS algorithm based on ISS key points in this paper. In addition, for key point extraction and registration, the software in this paper also sets shortcut functions such as "one-click extraction" and "one-click registration". 

 ![avatar]( da6b46dfb21e457aa5f60c847cb616b9.png) 

 ![avatar]( b2cce6cb035d44d2a9bcf7f18fbc2fe4.png) 

 Figure 16 Point cloud registration related function menu 

##  3.3 Point cloud surface reconstruction function 

 Figure 17 shows the function menu related to point cloud surface reconstruction of this software. This software supports 8 surface reconstruction algorithms including MLS, Poisson algorithm, greedy projection triangulation algorithm and improved greedy projection triangulation algorithm proposed in this paper, and also supports the shortcut function of "one-click reconstruction". In addition, this software can also export the reconstructed 3D model to files in OBJ, STL and PLY formats, which can be widely used in other application scenarios such as 3D printing. 

##  3.4 Point cloud segmentation function 

 The point cloud segmentation function of this software integrates 10 point cloud segmentation algorithms including plane segmentation, cylinder segmentation, European distance segmentation and color-based segmentation. The point cloud segmentation function menu of the software is shown in Figure 18. The purpose of point cloud segmentation is to extract the target point cloud required by the user from the point cloud data containing multiple targets. Users can use different segmentation algorithms for the target point cloud according to different properties of the point cloud. After the point cloud segmentation is completed, the different sub-point clouds obtained by the segmentation can be saved separately for the next processing. 

 ![avatar]( 5b046eb485cb45f78939c28411e989a2.png) 

 ![avatar]( 0e0c210442aa474989a94860f0707881.png) 

###  Point cloud attribute computing function 

 ![avatar]( e4fa5baf6df24967912e6a25c47f5f3b.png) 

 ![avatar]( 7c9b11c902824ae39c734663fe577ab4.png) 

 ![avatar]( 35e495b6ec7949019e063e28d6bd9d15.png) 

 ![avatar]( a8066332729b4e31a9f45417f0d144c1.png) 

 The geometric attribute extraction function menu of this software is shown in Figure 19. The software can calculate the geometric attributes such as surface area, volume, circumcircle, centroid, density and covariance matrix of the target point cloud. These attributes can be freely selected for extraction calculation, or you can click the "One-click Extract" menu item in the menu to calculate all the attributes of the target point cloud. It is worth mentioning that the calculation functions of the surface area and volume in this software need to be reconstructed after the surface of the target point cloud can be calculated. Schematic diagram of AABB bounding box and schematic diagram of OBB bounding box 

 Figure 19 Point cloud attribute computing function menu 

 This function can not only calculate the surface area of the target point cloud, but also obtain the maximum unit area and minimum unit area of the reconstructed surface. In fact, the surface reconstructed by the surface is composed of several unit surfaces, such as the surface generated by the greedy projection triangulation surface reconstruction algorithm, which is composed of several unit triangular surfaces. In addition, the software in this paper can calculate the actual volume of the target point cloud, but also calculate the target point cloud axis-aligned bounding box (AABB) volume and directed bounding box (OBB) volume, AABB bounding box and OBB bounding box schematic diagram as shown in Figure 19 © and Figure 19 (d), the two volumes are obtained for the packaging and transportation of real target objects. [78] 

#  IV. Software operation and testing 

 This section will use the point cloud processing and 3D reconstruction software developed in this paper to perform point cloud processing preprocessing experiments, point cloud registration experiments, point cloud surface reconstruction experiments, point cloud segmentation experiments and point cloud attribute computing experiments on point cloud data of different scenes, in order to verify the validity and practicality of the software in this paper. Figure 20 is the selected two main experimental point cloud images, and Figure 20 (a) is the point cloud image of the table. The point cloud image has a large amount of data, with 460,400 data points. It can be seen from the image that the point cloud contains more outlier noise points, and the point cloud space is not closed, so it is difficult to perform 3D reconstruction of such point clouds. Figure 20 (b) shows a point cloud image of a Chinese dragon, which also has a large amount of data, with a total of 437,645 data points. Unlike Figure 20 (a), the spatial characteristics of the point cloud are closed, but the surface curvature of the point cloud is complex and varies greatly. There are many raised areas, and it is also difficult to perform three-dimensional reconstruction. 

 ![avatar]( 3039dc791e7b4e46af19a48c6a4e9925.png) 

 ![avatar]( 699a5a1da40f4de5bcce7d808087138c.png) 

 Figure 20 Experimental point cloud object 

##  4.1 Point cloud preprocessing function test 

 As shown in Figure 21 (a) and Figure 21 (b), it is the main interface for loading and displaying the two point cloud images using the software in this paper. Then click the software function button to perform preprocessing operations such as outlier removal (KANN-DBSCAN outlier removal algorithm accelerated by KD-TREE), filtering smoothing (Gaussian filtering), and downsampling (voxel-based downsampling) on the current point cloud image. Figures 21 © and 21 (d) are schematic diagrams of the work when the software processes point clouds. Figures 21 (e) and 21 (f) are the results after point cloud preprocessing. As can be seen from the figure, the software in this paper not only removes the outliers in the two point cloud images, but also greatly simplifies the point cloud scale of the point cloud data while retaining its surface characteristics. As can be seen from Table 6, the point cloud preprocessing time for the table point cloud is 1955 ms, and the point cloud reduction rate is 0.07. The processing time of China Dragon Point Cloud is 1373 ms, and its reduction rate is 0.055. Although the point cloud scale of the two point cloud images has been reduced from 100,000 to 10,000, the contour characteristics of the point cloud have not been affected. 

 ![avatar]( 2ffe1801359b4d42920122fd2a8b4306.png) 

 ![avatar]( 5f000e92990e4713b35e9766866702bd.png) 

 ![avatar]( 6ab166c3b2284e088cb4bd0fec1bb070.png) 

 ![avatar]( de48e887156c42ed855bd398ce4d0b6d.png) 

 ![avatar]( fd07c48c76ed4b98ab894b14d41c0e74.png) 

 ![avatar]( 080f73eff24c4b37ad31e5019ca98f85.png) 

 Table point cloud image loading completed: Table point cloud image preprocessing, table point cloud image preprocessing completed, China dragon point cloud image loading completed: China dragon point cloud image preprocessing: China dragon point cloud image preprocessing completed:  

 Figure 21 Schematic diagram of software point cloud preprocessing 

 Table 6: Experimental results of point cloud pretreatment 

##  4.2 Point cloud registration function test 

 After the original point cloud data is preprocessed by the point cloud, it can be used for point cloud registration experiments. First, two frames of point cloud data at different positions are read into the software, as shown in Figure 22. Figure 22 (a) shows two frames of point cloud images of the table point cloud in different poses. Figure 22 (b) shows two frames of point clouds of the Chinese dragon in different poses. By clicking the function button on the software, select the registration algorithm to perform the registration experiment. As shown in Figure 22 © and Figure 22 (d), it is a schematic diagram of the registration work being carried out by the software. The registration results are shown in Figure 22 (e) and Figure 22 (f). It can be seen that the two red and blue point clouds almost completely overlap. The higher the degree of overlap between the point clouds, the better the point cloud registration effect. In the point cloud properties window in the software, you can see the conversion matrix from the current source point cloud (red) to the target point cloud (blue): 

 ![avatar]( 1b54dd4e4f6448b69ac0288f903ac3a8.png) 

 Table 7 shows the result analysis table for point cloud registration. As mentioned above, the smaller the FitnessScore, the closer the distance between the two frames of point clouds, and the higher the degree of coincidence. If the FitnessScore is 0, it means that the two frames of point clouds are completely coincident. It can be seen from the table that after 11 iterative registration times, the registration score of the table point cloud is 1, while the registration score of the Chinese dragon after 15 iterations of registration is 1. The registration score of the two-point cloud is approximately 0, indicating that the registration effect is more accurate. 

 ![avatar]( 3b2dec162a4b4fc89bf72ae8bca34c3f.png) 

 Figure 22 Schematic diagram of point cloud registration experiment 

 Table 7 Point cloud registration experiment results 

##  4.3 Point cloud surface reconstruction function test 

 After the point cloud registration is successful, by clicking the function button in the software, the greedy projection triangulation surface reconstruction algorithm is selected to perform surface reconstruction on the two target point clouds respectively. Figures 23 (a) and 23 (b) are schematic diagrams of the surface reconstruction being carried out by the software in this paper. Figures 23 © and 23 (d) are the three-dimensional models after the software surface reconstruction. It can be seen that the reconstruction effect is better, not only no false surface generation, but also no surface voids. Figure 24 is a comparison diagram before and after the three-dimensional reconstruction of the point cloud. From the comparison diagram, it can be seen that even if the unclosed surface or the point cloud surface contains a lot of detail features, the improved surface reconstruction algorithm proposed in this paper can restore and rebuild the surface details of the point cloud well. 

 ![avatar]( cc85fd9296164c91ab4efede756ccf84.png) 

 Figure 23 Schematic diagram of software surface reconstruction experiment 

 ![avatar]( 9902206c3fd04331867c6d1c0c13c10f.png) 

 Figure 24 Comparison of point cloud surface reconstruction before and after 

##  4.4 Point cloud segmentation function test 

 The point cloud segmentation function of this software integrates 10 different types of point cloud segmentation algorithms, such as plane segmentation, cylinder segmentation, European distance segmentation and regional growth segmentation, etc. Different segmentation algorithms are suitable for different point cloud scenarios and segmentation requirements. Due to the limited space of this paper, this subsection only selects the point cloud plane segmentation function and cylinder segmentation function in the software for testing. 

 ![avatar]( 2ccc1142052a463e81bfe565498d3c9d.png) 

 Figure 25 Planar segmentation of the table point cloud 

 ![avatar]( 4812c3ea003241708110f82990766e38.png) 

 Figure 26 Schematic diagram of table point cloud plane segmentation result 

 ![avatar]( fce8076cf44a4dce83a13b292269b13a.png) 

 Figure 25 is a schematic diagram of the table point cloud being divided by the software in this paper. It can be seen from the figure that the software searches for two planes in the table point cloud image and marks them with red and green respectively. Let the red one be plane 1 and the green one be plane 2. Click the "OK" button to extract the searched point cloud plane and save it locally. As shown in Figure 26, it is the division result of the table point cloud, Figure 26 (a) is the effect diagram of the point cloud division, Figure 26 (b) and Figure 26 (d) are the plane 1 and plane 2 obtained by the plane division of the software from the table point cloud. The result after extracting the two planes is shown © Figure 26. It can be seen that both planes are completely extracted. Not only that, the equation of the plane in the three-dimensional space is shown in the formula (5.1) [79]:  

 According to this formula, the plane equations of plane 1 and plane 2 in the three-dimensional point cloud space can be fitted respectively. The parameters of the two plane equations are shown in Table 8: 

 Table 8 Table point cloud plane segmentation data results 

 In addition, the software in this paper can also perform multiple segmentation of point cloud data, that is, by using different point cloud segmentation algorithms to segment the point cloud in turn. Figure 27 (a) is a top view of another original point cloud data used for point cloud segmentation testing, and Figure 27 (b) is a side view. It can be seen from the two figures that the scene described by the point cloud image is: a water cup is placed on the table plane, and the water cup has a semi-circular water cup handle. From the overall perspective, it can be found that the original point cloud contains a plane (table) and a cylinder (water cup). 

 ![avatar]( 664f43f9f9454dedbb51b03a98fb38d4.png) 

 Fig. 27 Planar segmentation and cylinder segmentation processing 

 The original point cloud is divided by plane and cylinder in sequence using the software in this paper. The plane segmentation result is shown in Figure 27 ©, and Figure 27 (d) is the cylinder segmentation result. As can be seen from the plane segmentation result, the software in this paper can completely extract the point cloud plane. From the segmentation result of the cylinder, the cylinder of the visible water cup is completely extracted, and the water cup is not extracted. In addition, the equation of the cylinder in the three-dimensional point cloud space is shown in the equation (5.2): 

 ![avatar]( 569dcd41bc1a4dd7aca8473036d32657.png) 

 Wherein, is any point on the axis C of the cylinder, is the direction vector of the axis C, and is the radius of the cylinder. According to this formula, the parameters of the cylinder equation can be obtained by fitting: 

 In addition, according to equation (5.1), the parameters of the plane equation can be obtained as follows: 

##  4.5 Point cloud attribute computing function test 

 The point cloud attribute calculation function of this software supports the calculation of six attributes including the surface area, volume, circumscribed circle, and point cloud centroid of the point cloud. This test will mainly calculate the two attributes of surface area and volume. 

 ![avatar]( 50203378fcca4da58d1d101fe14ca72f.png) 

 Figure 28 Chinese Dragon Point Cloud Attribute Computing 

 ![avatar]( e7820293bd8e4740ab19625438d1c85e.png) 

 Figure 29 Monkey point cloud attribute calculation 

 Figure 28 (a) is a schematic diagram of the software work for calculating the surface area and volume of the Chinese Dragon Point Cloud. Figure 28 (b) is the calculation result of the surface area and volume. It can be seen from the results that the surface area of the Chinese Dragon Point Cloud is 0.0725956 square meters, its volume is 0.00478281 cubic meters, and its AABB bounding box volume is 0.00271155 cubic meters, and the OBB bounding box volume is 0.00298459 cubic meters. Figure 29 (a) is a working diagram of the software's surface area and volume calculation of the monkey point cloud. It can be seen from the calculation result Figure 29 (b) that the surface area of the monkey point cloud is 10.7531 square meters, its volume is 2.45824 cubic meters, and its AABB bounding box volume is 8.14628 cubic meters, and the OBB bounding box volume is 8.11579 cubic meters. 

#  Fifth, summarize 

 The software in this paper has three functional modules: point cloud IO, point cloud processing and 3D visualization, among which there are 12 main functions in total. Then introduce the specific function development of the software in this paper, including the development platform of the software, the design of the main interface, the data structure related to the software and the related functions of point cloud processing. The related functions of point cloud processing are the core functions of this software, which cover 78 excellent point cloud processing related algorithms at home and abroad, including the improved algorithm in this paper, and there are as many as 156 related function functions. Not only that, each point cloud processing algorithm can set input parameters independently, and different algorithms can be freely used together, and users have a high degree of freedom in choosing the algorithm. Finally, different point cloud data are used to test the software's functions such as point cloud preprocessing, point cloud registration, point cloud surface reconstruction, point cloud segmentation, and point cloud attribute calculation. The software test results show that the software designed and developed in this chapter has high practicality. 



--------------------------------------------------------------------------------

Recently, I found that many CSDN blogs are reprinting my articles to attract attention. Here, I have to move my original articles from Bogayuan to CSDN's columns again. At the same time, I hope that the students will respect the results of their labor and indicate the source of the reprint!!! 

 In the application of laser-based autonomous driving or mobile robots, the ability to extract individual objects from a moving scene is very important. Because such systems need to perceive changing or moving objects in a dynamic sensing environment, in the sensing system, preprocessing the image or point cloud data into individual objects is the first step for further analysis. 

 In this paper, a very efficient segmentation method is proposed. First, the scanned point cloud is removed from the plane for processing, and then the point cloud data within a certain range after removing the plane is segmented into different objects. The paper focuses on solving the problem of efficient segmentation on most systems under the condition of small computation. It avoids direct calculation of 3D point clouds and operates directly on 2.5D depth images. This scheme can solve the problem of processing sparse 3D point cloud data well. The author uses a new Velodyne VLP-16 scanner, and the code implements this method in C++ and ROS, and the code is open-source. This method can be run using a core solo CPU and a frame running rate higher than the sensor, and can produce high-quality segmentation results. 

 ![avatar]( 20191219231851395.jpg) 

 Left: Objects (e.g. people, cars, and trees) generated after segmentation using sparse 3D point cloud data obtained by the Velodyne VLP-16 scanner. Different colors correspond to different segmentation results. Right: Clearpath Husky robot used for experiments. 

 Separating individual objects in 3D laser point cloud data is an important task for autonomous navigation by mobile robots or autonomous vehicles. Autonomous vehicles navigating in unknown environments are faced with the complex task of reasoning about their surroundings., On busy streets with cars and pedestrians, maps can be affected by erroneous data associations resulting from the dynamic nature of the environment. A key step in being able to better reason about such objects and ignore possible dynamic objects during scan registration and mapping is to split 3D point cloud data into different objects so that they can be tracked individually 

 Therefore, the important contribution of this paper is to achieve fast reading, efficient and robust segmentation of 3D sparse point clouds. (I personally tested it, it was really fast, my computer's configuration was really bad, but it ran super fast) On a mobile CPU, it can handle Velodyne sensors over 70HZ (64 lines) or 250HZ (16 lines). 

 Ground removal 

 Before segmentation, the ground needs to be removed from the scanned point cloud data. This ground removal method simply removes the 3D points below the height of the vehicle. This method works in simple scenarios, but fails if the pitch or roll angle of the vehicle is not equal to zero or the ground is not a perfect plane. But the situation can be improved using RANSAC's plane fitting method. 

 The lidar provides the distance value of each laser beam, the timestamp, and the direction of the beam of light as the original data source. This allows us to directly convert the data into a depth image. The number of rows in the image is defined by the number of beams of light in the vertical direction. For example, for the Vdyelone scanner, there are 16 lines, 32 lines, and 64 lines, while the number of columns in the image has the distance value obtained by the laser rotation every 360 degrees. Each pixel of this virtual image stores the distance between the sensor and the object. To speed up the calculation, it is even possible to consider combining multiple readings in the horizontal direction into a single pixel if necessary. 

 ![avatar]( 20191219231942296.jpg) 

 Top left: Part of the depth image. Center left: Image generated by displaying the alpha angle. Bottom left: Angle after applying Savitsky-Golay smoothing. Top right: Illustration of the alpha angle. Bottom right: Smooth illustration of the alpha angle column marked in the left image. 

 Using the generated combined image to process instead of directly processing and computing the 3D point cloud can effectively accelerate the processing speed. For other scanners that do not provide distance values, the 3D point cloud can also be projected onto a cylindrical image to calculate the Euclidean distance of each pixel. The method proposed in this paper can still be used. 

 In order to identify the ground, there are three assumptions: 

 1. Assume that the sensor is roughly mounted on a horizontally moving base. 

 2. Assume that the curvature of the ground is low. 

 3. The mobile robot or vehicle observes the ground plane at least at the pixel of the lowest row in the depth image 

 The distance values of each column (c) pixel of the depth image are first converted into angle values ®, which represent the angle of inclination connecting the two points. And respectively represent the depth values adjacent to the row. Knowing the two individual laser beam depth values that are continuously perpendicular, the angle α can be calculated using trigonometry rules as follows: 

 ![avatar]( 20191219232119550.jpg) 

 Where the angles of a and b are the vertical angles of the laser beam corresponding to rows r-1 and r, and since two depth values are required for each α calculation, the resulting angle map size is 1 smaller than the number of rows in the depth map range. It is assumed that all these angles are expressed as the angle values at the r-row and c-column (row and column) coordinates. 

 ![avatar]( 20191219232126184.jpg) 

  Ground recognition algorithm. According to the above algorithm, the ground is marked in light blue. 

 However, since lidar also has error points, it is also necessary to deal with some outliers in the depth range. For details, please refer to the paper. In order to achieve the effect of angular smoothing, the Savitsky-Golay filtering algorithm is used to process each column. After obtaining the filtered angle graph, we start to perform ground recognition on this basis, using breadth-first search to mark similar points together. Breadth-first search (BFS) is a popular graph search traversal algorithm. It starts traversing from a given point in the graph and first starts to explore directly adjacent nodes before moving to the next level. In this paper, we use the N4 domain value on the grid to calculate the angle difference to determine whether two adjacent elements of matrix M satisfy the angular constraint, Delta a, set to 5 °. 

 Fast and efficient segmentation using laser depth images 

 The vertical resolution of the sensor has a very important impact on the difficulty of the segmentation problem. We need to determine whether the laser beam is reflected by the same object for adjacent points. To solve the problem of whether the laser beam is reflected by the same object, here is the method based on angle measurement. The advantage of this method is that the advantages of this method are repeatedly mentioned in the text: First, we can directly use the well-defined neighborhood relationship in the depth image, which makes the segmentation problem easier. Second, we avoid generating 3D point clouds, which makes the overall method faster. 

 The following figure shows the effect of segmentation 

 ![avatar]( 20191219232224978.jpg) 

 This is the result of using this segmentation scheme. (A) The graph is from the Velodynede point cloud. (B) The depth image is created from the original values of the sensor and the ground points have been removed. (C) The graph is the result of the segmentation performed on the basis of the generated depth map. (D) The segmented depth map is restored as a point cloud and displayed in different colors. 

 Here is a detailed explanation of how to implement segmentation using angle constraints: 

 An example scenario as shown in the figure below, in which two people walk close to each other in front of a cyclist, who passes between them and a parked car. The Velodyne VLP-16 scanner used here recorded this scene. The middle image shows the results of two arbitrary points A and B measured from the scanner located at O, indicating the laser beams OA and OB. Without loss of generality, we assume that the coordinates of A and B lie in a coordinate system centered on O, with the y-axis following the longer of the two laser beams. We define the angle β as the angle between the laser beam and the line connecting A and B, which is generally away from the scanner. In practice, angle β proves to be valuable information that can be used to determine whether points A and B are located on the same object. 

 ![avatar]( 20191219232336641.jpg) 

 Then based on the measurement value of the laser, we know the distance value OA of the first measurement and the corresponding second measurement value OB. The measurement results of these two times are marked as d1 and d2 respectively. Then using the above information, the angle can be measured by the following formula: The right illustration in the following figure shows the calculation in the xy plane from the top view of the scene. Note that we can calculate the angle β of the pair of points A and B that are adjacent in the row or column direction in the range image. In the first case, the angle corresponds to the angle increment in the row direction, while in the other case it corresponds to the increment in the column direction. Left: The example scene has two pedestrians, a cyclist and a car. Middle: Assuming the sensor is at point O and the lines OA and OB represent two laser beams, then points A and B produce a line that estimates the surface of the object if they both belong to the same object. We make the judgment of whether it is the same object based on the angle β. If β > theta, where theta is a predetermined threshold, the points are considered to represent an object. Right: Top view of a pedestrian in an example scenario. The green line represents the points where β > theta, while the red line represents the angle below the threshold, so the objects are marked as different. 

 The segmentation method based on the threshold value of β is experimented in experimental evaluation. The actual situation can be the case where the object being scanned is flat, such as a wall, and is almost parallel to the laser beam direction. In this case, the angle β will be small, so the object may be divided into multiple segments. This basically means that if β is less than theta, it is difficult to determine whether the two points originate from two different objects, or are merely located on a flat object that is almost parallel to the beam direction. However, despite this drawback, our experiments show that the method is still useful in practice. The above behavior rarely occurs, and if so, it will usually lead to over-segmentation of particularly inclined planar objects. 

 ![avatar]( 2019121923242596.PNG) 

  The above is about the segmentation algorithm used after going to the ground. It can be seen that the most important formula is the solution of the β angle value 

 experimental part 

 The algorithm (i) performs all calculations quickly, even when running on the core solo of a mobile CPU at approximately 70 Hz. 

 (Ii) can obtain 3D original data sources from mobile robots to generate depth data and segment them into meaningful individuals 

 ![avatar]( 20191219232454275.PNG) 

 (Iii) The method performs well on sparse data, e.g. sparse data obtained from a 16-beam of light Velodyne Puck scanner. In experiments, Euclidean clustering implemented in the Point Cloud Library PCL is used. In all experiments, we use the default parameter theta = 10 °.  

 The code is open source (https://github.com/PRBonn/depth_clustering), and the editor personally tested it, and attached the test video. Those who are interested pay attention to the WeChat official account, and the editor has simplified and optimized the code. Those who are interested can contact and communicate. The original text is on the blog at: https://www.cnblogs.com/li-yao7758258/p/9937704.html 

 And you can recommend valuable code or papers related to point clouds that you think are better, and send them to the group owner's mailbox (dianyunpcl163.com), so that you can communicate and discuss together!! 

 Interested small partners can follow the WeChat official account, join the QQ or WeChat group, and communicate and share with everyone (this group is mainly a communication and sharing group related to point cloud 3D vision, everyone is welcome to join and share) 

 ![avatar]( 20191219232602296.PNG) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  Demo display 

 ![avatar]( 882d262a5bee413e8c7f9d30996d0cf6.gif) 

#  Project address 

 github:Almost 3d point segmetation 

 Paper address: Paper 

#  paper effect 

 Reference: Interpretation of the article 

 ![avatar]( 8b8e7ce9f8b84aa7966c7d0ad9fdcbb2.png) 

 Effect: 

#  Reproduction process 

 ![avatar]( 430ecb6e4b8a47f48465fa78a5044e14.png) 

 1. Source code download, method 1: I tried cmake again, but there were many errors, so I gave up. 

 ![avatar]( 86616d495b2f404b8f27514fe09e7823.png) 

 Method 2: Create a new VS project 1) Copy the relevant files from the source code to the new project and compile. 2) As shown below 3) Set the attribute list and add opencv and pcl related attributes. Another attribute list adds the relevant supervoxel folder as shown below.  

 4) Error message 

#  follow-up 

 Run the test: 

 ![avatar]( bde0ebfc0ae24a3491f90a6a7efc0b40.png) 

 ![avatar]( 0c8efd6d8db24b4aac2cf2a7250bd708.png) 

  The segmentation effect is still OK, and it will be added to the PCL + QT related software later. 



--------------------------------------------------------------------------------

#  First, the demo 

 ![avatar]( 40ee3d12b57046cf84b96667cb638dd0.gif) 

#  Project address 

 github链接：Fast Ground Segmentation for 3D LiDAR Point Cloud Based on Jump-Convolution-Process 论文链接：Fast Ground Segmentation for 3D LiDAR Point Cloud Based on Jump-Convolution-Process 论文下载：csdn论文下载 

#  III. Reproduction process 

 ![avatar]( 74592b1778914cf2af016ac08288693b.png) 

 1. Download the source code 2. Create a new vs project, including jpc_groundremove .cpp and jpc_groundremove files. Run the main function. The details are as follows: 

 ![avatar]( a9acd29afa794c6cb02adef12ef97a7e.png) 

 1) Add opencv and pcl to the attribute list 2) Add relevant existing files 

 3) Run the main function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573789535
  ```  
#  test data 

 ![avatar]( 6a635291eca6469eb6ccbf5f9fe1c044.png) 

  After running, green is the ground, red is the non-ground part. non-ground part, ground part  

#  follow-up 

 Study together and make progress together. 



--------------------------------------------------------------------------------

##  Simple factor graph optimization test 

 ![avatar]( 20200729110933958.png) 

 The diagram shows that this is an example of 2D pose map optimization on the official website. It probably means that there are a total of 5 stations on the right. First, the robot passes through x2, x3 in the same direction from point x1, and then the x3 station rotates 90 degrees to reach the station x4, and then the station 4 rotates 90 degrees to reach the x5 point. X rotates 90 degrees again and finds that "this place seems to have been" - establishing a constraint relationship between x2 and x5. ps: The robot chassis odometer calculates that the distance between each two stations is 5m, but in fact it is not 5m. The actual arrival of each station may be a little bit worse, so the cumulative error is relatively large, which is why it is necessary to loop back to detect and then optimize the graph. Source Code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Process Analysis: Step 1: Building a Factor Graph Model 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 2: Initialize the vertex value 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 3: Fix the first vertex, add a system prior, unary factor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 4: Add pose constraints, binary factors 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 5: Add inter-loop constraints, binary factors 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 6: Problem Solving, using the Gauss-Newton Method 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Step 7: Marginalization, calculate the covariance matrix for each variable 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Run result: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 cmakeLists.txt file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 Reference: 1. Official tutorial: https://gtsam.org/tutorials/intro.html#listing_OdometryOptimize 

##  Second, the factor graph optimization logic in LeGo-LOAM 

 1) Series header file 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 2) Series declaration and initialization 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 3) In the loop detection thread, when a closed loop is found, add the loop factor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 4) In saving key frames and factors, first add fixed prior factors 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 5) Then add the binary factor between poses 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 6) Update ISAM and calculate pose 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  
 7) Visit the final corrected position 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573734554
  ```  


--------------------------------------------------------------------------------

#  1. HDL-graph-SLAM ground point extraction 

 Before reading the ground removal algorithm, in order to help understand the principle of ground normal verification, do a simple test on the matrix calculation involving Eigen 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957359346
  ```  
 Test results: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957359346
  ```  
 After the test, start looking at the code of the ground extraction algorithm 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957359346
  ```  
 The whole idea is relatively simple and can be easily implemented using PCL. 

#  2.LeGo-LOAM Ground Point Extraction 

 ![avatar]( 20200710234559612.png) 

 The processing idea of the ground point cloud in LeGo-LOAM is also very simple. It can be understood directly in the above figure combined with the code: that is, the pitch angle between the two lines is obtained from the XYZ position of the point between the upper and lower lines (considered to be the ground point cloud circle). If the pitch angle is within 10 degrees, it is determined that (i, j) is the ground point. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957359346
  ```  


--------------------------------------------------------------------------------

Maps built for autonomous driving are often called high-definition maps. These maps are at the centimeter level and generally have extremely high accuracy. Read this article to learn some basic content about high-definition maps. You will learn about the definition of high-definition maps, why high-definition maps are needed for autonomous driving, how to make high-definition maps, how to store high-definition maps, and other basic issues, and have a comprehensive and basic understanding of high-definition maps. 

 ![avatar]( 20200407185400107.jpg) 

 What is a high definition map? High-precision maps refer to electronic maps with higher accuracy and more data dimensions. High accuracy generally refers to the centimeter level. Data dimensions refer to more than general electronic maps, not only road information, but also static information related to traffic. 

 Why does autonomous driving need such an accurate map form? In most cases, autonomous driving may have a high tolerance for errors, but in some cases, when driving on a road leading to a certain place, one side is actually a cliff, and autonomous driving has no room for error there. Therefore, we believe that maps must be very accurate and contain more environmental information. These maps not only contain the location of lanes, the location of the boundary of the road, but also want to know the position of the boundary curve and the height. 

 ![avatar]( 20200407185507763.png) 

 Why do you need high-precision maps? The digital maps used in navigation devices and mobile phones are obviously no longer sufficient for autonomous driving, because these maps are simple and mainly for human use. The maps used in these mobile phones can understand simple instructions when navigating. In this era of autonomous driving, machines and robots need to make decisions on the road, so a new set of maps built specifically for robotic systems is required. 

 Although robots have the ability to do some things more efficiently than humans, humans are still much smarter. In terms of driving and navigation, real-time decision-making ability is a unique advantage for humans. For example, human decisions in the face of emergencies at intersections are very difficult for robots. Then having high-precision maps can help vehicles make better decisions based on centimeter-level positioning 

 How to create a high definition map? 

 ![avatar]( 20200407185530711.png) 

 Making maps with high precision is a complex and labor-intensive job, with both hardware and software components. Hardware components usually refer to having a lot of sensors around the roof. These sensors are very useful for map creation and map updates. For example: cameras, LiDAR, GPS, IMU and radar sensors are combined together. These sensors also often help provide redundant information to autonomous cars without sensors. Vision sensors such as cameras are often limited when precise positioning of autonomous cars is required. LiDAR sensors are here to accurately measure depth or distance in 3D space. Therefore, LiDAR and cameras can often work together and run quickly multiple times per second. If the car is usually traveling at 70 mph, the sensors are also collecting a lot of data at that speed. In this case, the car will use and create maps simultaneously. 

 ![avatar]( 20200407185552463.png) 

 The other part is the software. The software part provides the data collection and recording for the hardware, and the data information is generally shareable. Advanced sensors enable autonomous cars to use the combination of sensors more efficiently, helping to capture the data needed to create high definition maps. The main types of sensors include cameras, long-range radar, short- and medium-range LiDAR, and ultrasound. 

 High definition map composition? 

 According to Lyft, the high definition map is divided into five layers. They are the basic map (standard definition map), the geometric map, the semantic map, the graph prior map, and the real-time knowledge map 

 ![avatar]( 20200407185636776.png) 

  The geometric map is composed of raw sensor data collected from raw sensor data from lidar, various cameras, GPS, and IMU. The output is a dense 3D point cloud, and this data is post-processed to generate derived map objects stored in the geometric map. 

 The semantic map layer is built on top of the geometric map layer by adding semantic objects. Semantic objects can be 2D or 3D, such as lane boundaries for safe driving, intersections, parking spaces, stop signs, traffic lights, etc. These objects contain rich information such as traffic speed, lane change restrictions, etc. 

 The map prior layer contains dynamic information and human behavior data. For example, the order of change of traffic lights, the average waiting time of traffic lights in a typical day, the probability of vehicles in a parking lot, the average speed of vehicles in a parking lot, etc. Autonomous algorithms usually consume this prior information. Models serve as inputs or functions and are combined with other real-time information. 

 The real-time knowledge layer is the topmost layer in the map and can be dynamically updated to contain real-time traffic information. This data can also be shared in real time between autonomous fleets. 

 What is the significance of high definition maps in autonomous driving? 

 At a high level, the software that runs an autonomous car consists of four components, or modules. The first part is the perception system; you can think of it as the human eye. It tries to see things in the road where the car is traveling, for example, see someone crossing the road, see the signal change from red to green, etc., 

 The other part is called the locator module: the locator module tells the car where you are in 3D space and what is actually going on around you. For example, the system says you are 150cm from the sidewalk, at which point the "Planning and Control" module will activate and say: "Okay, I'm going to slow down and stop at the next intersection." 

 Then the fourth component is the mapping component. You can imagine the mapping system on top of the three components, as mentioned earlier. Mapping and localization are tightly integrated, constantly comparing your position on the map. It needs to know where it should be in and tell the difference. For example, if I know there should be an intersection and a crosswalk, and see a moving object across it, it could be a pedestrian. 

 How many cars does it take to create a high definition map? 

 ![avatar]( 20200407185703317.png) 

 One car cannot really map the entire world. The problem is not only how to create the map, but also how to maintain the map to reflect changes on the road. For this, multiple cars need to be driven on the same road, and this data will be aggregated from multiple drives on multiple cars. The more cars you have on the road, the more data is collected, and the higher the quality of the high definition map. The cost incurred in creating high definition maps is a huge challenge because we cannot send large amounts of data over cellular networks. The solution to this challenge is to categorize information that is shared in real time with information that does not need to be shared in real time. Therefore, things that truly affect driving behavior need to be shared and distributed with other cars that may be affected, such as known road accidents, landslides during the rainy season, ongoing road construction, and so on. 

 How are HD maps stored? 

 A lot of data is being collected right now, and more will be collected in the future once we have more autonomous cars on the road. This is where cloud computing comes in, and 99% of computing is done there. 

 ![avatar]( 20200407185721288.png) 

 However, each car will continue to have its own storage unit or storage, which people refer to as edge computing. Therefore, each car will have its own storage and computing power, so each car can make its own decisions independently and should be able to function properly even if it is offline. In that case, the map will be called several times per second in a row by other software stacks (e.g. perception system, planning and control system). The change detection module needs to be launched to check how the map looks different from what already exists in the system and determine if it is a really important change that is distributed in real time or sent to the edge computing process, then activate the proactive data collection process and share that data in the cloud.  

 What are the legal issues with HD maps? 

 Maps always have issues of land laws, place names, legal issues, maps of where can be displayed, maps of where can't be displayed, etc. Although digital maps are now widely used, there are still some countries around the world that strictly regulate their geospatial data and even prohibit the export of geospatial data. 

 For high definition maps, this will be a huge challenge as government regulations are not yet clear. As cars have high resolution LiDAR and then cameras constantly scan streets and see areas such as private driveways, there will be various sensitivities. So being able to protect people's privacy and comply with government regulations from a security perspective, and ensuring that data is sufficiently encrypted to ensure that no accidental leaks are made, are some of the key areas that need to be addressed. In certain countries, governments are now starting to get active, both in terms of protecting privacy and advancing autonomous driving technology in this regard. It will be a few years before the dust settles and we see the technology and policy positions will take action. 

 Why are maps exploding in the era of high definition maps? Over the years, we've tended to simplify maps as much as possible. To geographic boundaries, to oceans, to roads. But now that maps are exploding in different directions, and reducing the actual time difference between using and creating maps, cars will have the ability to share information, which was not possible in previous mapping situations. With the ability to continuously collect high definition maps, mapping will now come to life. 

 Resources, Overview of Semantic Segmentation of 3D Point Clouds in Large Scenes outofcore module in PCL - Display of large-scale point clouds based on off-core octree, Target segmentation based on local concavo-convex properties, Point cloud labeling based on 3D convolutional neural networks, SuperVoxel of point clouds Large-scale point cloud segmentation based on hyperpoint graphs, Introduction to SLAM method based on fisheye camera, A summary of historical articles on point cloud learning 

 ![avatar]( 20200407185832302.png) 



--------------------------------------------------------------------------------

Data Types of Point Clouds in ROS 

 The data structures that represent point clouds in ROS are: sensor_msgs :: PointCloud sensor_msgs :: PointCloud2 pcl :: PointCloud < T > 

 For the structure of PCL data in ROS, please refer to wiki.ros.org/pcl/Overview 

 About sensor_msgs :: conversion between PointCloud2 and pcl :: Point Cloud < T > using pcl :: from ROS Msg and pcl :: toROS Msg  

 sensor_msgs :: between PointCloud and sensor_msgs :: PointCloud2 

 使用sensor_msgs::convertPointCloud2ToPointCloud 和sensor_msgs::convertPointCloudToPointCloud2. 

 So how to use PCL in ROS? (1) Add dependencies under the CMakeLists.txt file under the created package 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMzMTEzMDUwODUyNC04NDU4Mzk5NjgucG5n) 

 In the package.xml file, add: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 Create a new .cpp file in the src folder 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 Add in the CMakeLists.txt file: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 After catkin_make generate the executable, run the following command 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 Run RVIZ to visualize the following, and the topic of the point cloud published by the program can be displayed. At the same time, you can also use the display function visualization that comes with PCL (I won't go into details here) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 So if we want to realize the filtering processing of the acquired point cloud data, here is a simple voxel grid sampling experiment 

 Also create a new .cpp file in the src folder, and then our program is as follows. That is, to implement the filtering of the acquired point cloud in the callback function, but we need to pay special attention to the data format of the point cloud in each program and how we use the function to realize the conversion of ROS and PCL. 

 The procedure is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 Take a look at the results shown in the figure. This is the result displayed in RVIZ. Of course, it can also be visualized using the PCL library (note that the data format of the point cloud we displayed in rviz is all 

 To distinguish between PCL :: PCL Point Cloud 2, which is a data format defined in the PCL Point Cloud Library and cannot be displayed in RVIZ.) 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMzMTE3MDUwMDgzNi0xNTU3MDY3Mjg0LnBuZw) 

 /************************************************************************** example application using pcl/PointCloud < T >. This type of data format is a data format defined in the PCL library, which uses two data transformations from 

                       sensor_msgs/PointCloud2       到        pcl/PointCloud<T>                      pcl::ModelCoefficients                到         pcl_msgs::ModelCoefficients.   

 code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721210
  ```  
 Extract the parameters of the plane in the point cloud and publish it 

  PCL Summary of the Interface to ROS 

 For example:  

 The PCL interface to ROS provides the conversion of PCL data structures through the message-based conversion system provided by ROS. There are a series of conversion functions provided to convert raw PCL data types to message types. Some of the most useful and commonly used message types are listed below. 

 : This is not a real message type, but is used in every part of the Ros message. It contains the time the message was sent and the serial number and box name. PCL is equal to pcl :: Header type 

 This is the most important type., PCL :: PCL Point Cloud 2 This type is also important because previous versions may be deprecated. 

 : This type stores the subscript of the point in the point cloud, which is equal to 

 This type includes messages that need to describe polygonal mesh, that is, vertices and edges, which are equal to 

 : This type contains a series of vertices as an array subscript to describe a polygon. In pcl equal to 

 : This stores the different coefficients of a model, e.g. 4 coefficients are required to describe a plane. in PCL equal to 

 The above data can be converted from PCL to PCL in ROS... The following functions are provided in the pcl_conversions namespace 

 The following functions are provided in the pcl_conversions namespace 

 It sums it up 

 void fromPCL(const <PCL Type> &, <ROS Message type> &); void moveFromPCL(<PCL Type> &, <ROS Message type> &); void toPCL(const <ROS Message type> &, <PCL Type> &); void moveToPCL(<ROS Message type> &, <PCL Type> &); 

 The PCL type must be replaced with the previously specified PCL type and the corresponding type in ROS. sensor_msgs :: PointCloud2 has a specific set of functions to perform the conversion 

 void toROSMsg(const pcl::PointCloud<T> &, sensor_msgs::PointCloud2 &);                     转换为ROS的点云sensor_msgs::PointCloud2类型 void fromROSMsg(const sensor_msgs::PointCloud2 &, pcl::PointCloud<T>&);                 转为PCL中的pcl::PointCloud<T>类型 void moveFromROSMsg(sensor_msgs::PointCloud2 &, pcl::PointCloud<T> &);               转换为pcl::PointCloud<T> 类型 

 ************** 

 Interested parties can follow the WeChat official account or join the QQ group 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzA0Lzk3NjM5NC0yMDE3MDQwODE3NTMxNjMwMC0yNTU2NDM5ODUucG5n) 



--------------------------------------------------------------------------------

![avatar]( abfbd451f7914fdbbb8d9adaf0703ef7.png) 

 In the fusion positioning of GNSS and Lidar, there is such a problem that if an accurate static external parameter of the map coordinate system relative to the world coordinate system is obtained, GNSS and lidar positioning on the same carrier can be mapped to the same coordinate system, and the positioning deviation of the two does not exceed 20cm, so as to meet the conditions of data fusion. The general approach is to record the warp and latitude heights and heading of the initial location of the map as the static external parameters of map to world during the lidar global positioning process, but we will find that if we only refer to this one location point, the two trajectories that run out will be like this: green: gnss positioning, yellow: lidar positioning, the reason for the deviation may be the deviation between the size of the mechanical external parameters installed by lidar and inertial navigation, or it may be a problem of map accuracy. How to ensure that the two trajectories are as consistent as possible? 

 ![avatar]( 7b069474b9dd4508a7d287cb9de72a84.png) 

 You can observe and manually adjust the static external parameters of map2world. The method here is to register the static external parameters through the position registration of GNSS and LIDAR positioning to compensate the static external participants. The essence is a least squares problem. The position of lidar matching is close to the gnss position. Here, use the ICP in PCL to solve R, t. Green: gnss positioning, red: radar position after registration. The R and t obtained by solving are: trans: -0.00119538, -0.00497306, 0.000654312 rpy: -171.906, -177.667,177.856. Compensation for this parameter to the map2world static external parameters can make the lidar matching pose consistent with gnss to the greatest extent. Key source code: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573757037
  ```  


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

              How to extract a subset of a point cloud based on a segmentation algorithm. 

 code parsing 

 Result: 

 ![avatar]( 976394-20170227123124235-1989913264.png) 

 Show it: 

 ![avatar]( 976394-20170227123224376-297713890.png) 

                         Figure 1 Original point cloud image, Figure 2 Downsampled point cloud data 

 ![avatar]( 976394-20170227123656782-468223961.png) 

                          The first plane model obtained by segmentation in Figure 3, and the second plane model obtained by segmentation in Figure 4 

 (2) Use ConditionalRemoval or RadiusOutlinerRemoval remove outliers 

    How to remove outliers using several different methods in the filter module, for the ConditionalRemoval filter, all data points that satisfy one or more conditional indicators set for the input point cloud can be deleted at one time, RadiusOutlinerRemoval filter, it can delete all data points that do not reach at least enough nearest neighbors within a certain range of the input point cloud. 

    Regarding the understanding of RadiusOutlinerRemoval, in point cloud data, it is set that there are at least enough close neighbors around each point within a certain range, and it will be deleted if it is not satisfied 

    Regarding ConditionalRemoval, this filter removes data points in the point cloud that do not meet one or more conditions specified by the user 

 New file remove_outliers cpp 

 The result of compiling and running is 

 ![avatar]( 976394-20170227141318032-1451379900.png) 

 You can see the difference between ConditionalRemoval and RadiusOutlinerRemoval 

 RadiusOutlinerRemoval is more suitable for removing individual outliers ConditionalRemoval is more flexible and can be filtered flexibly according to the conditions set by the user 

  WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303134940673-1204856584.jpg) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

With the gradual development of machine vision, autonomous driving and other disruptive technologies, the use of 3D cameras for object recognition, behavior recognition, scene, modeling, and related applications are increasing. It can be said that the depth camera is the end point and the robot's eyes. So what is a depth camera? Compared with the previous ordinary camera (2D), what are the differences? The depth camera is also called a 3D camera. As the name suggests, it can detect the depth of field distance of the shooting space through this camera, which is also the biggest difference from ordinary cameras. 

 The pictures taken by ordinary color cameras can see all the objects in the camera's perspective and record them, but the recorded data does not include the distance of these objects from the camera. Only through the semantic analysis of the image can we determine which objects are farther away and which are closer, but there is no exact data. However, the depth camera just solves this problem. Through the data obtained by the depth camera, we can accurately know the distance between each point in the image and the camera. In this way, plus the (x, y) coordinates of the point in the 2D image, we can obtain the three-dimensional spatial coordinates of each point in the image. Through the three-dimensional coordinates, the real scene can be restored, and applications such as scene modeling can be realized. 

 ![avatar]( 2019122018593330.jpg) 

 The methods of depth cameras are classified as shown in the following table: There are three types of depth camera solutions currently available on the market. (1) Structured-light, representing companies such as Obi Zhongguang, Apple (Prime Sense), Microsoft Kinect-1, Intel RealSense, Mantis Vision, etc. (2) Binocular Vision (Stereo), representing companies Leap Motion, ZED, DJI; (3) Time-of-Flight (TOF), representing companies Microsoft Kinect-2, PMD, SoftKinect, Lenovo Phab. 

 Of course, there is also a light field camera. If you are interested, you can follow the WeChat official account article. 

 The following describes the principles of these three depth cameras in detail: 

 Structured light depth camera 

 Structured light, called Structured light in English, is based on the principle that a near-infrared laser is used to project light with certain structural characteristics onto the object to be photographed, and then it is collected by a special infrared camera. This light with a certain structure will acquire different image phase information due to different depth areas of the subject, and then convert this structure change into depth information through an arithmetic unit to obtain a three-dimensional structure. In simple terms, the three-dimensional structure of the object to be photographed is obtained by optical means, and then the obtained information is applied in greater depth. Usually, an invisible infrared laser of a specific wavelength is used as the light source. The light emitted by it passes through a certain coding and is projected on the object. The distortion of the returned coding pattern is calculated by a certain algorithm to obtain the position and depth information of the object. According to the different coding patterns, there are generally: 

 ![avatar]( 20191220190031781.PNG) 

 Stripe structured light, representing sensor enshape, encoding structured light, representing sensor Mantis Vision, Realsense (F200), speckle structured light, representing sensor apple (primesense), Obi medium light. The following figure is a schematic diagram of a typical structured light camera: The advantages of structured light (speckle) are mainly: 1) The scheme is mature, and the camera baseline can be made relatively small, which is convenient for miniaturization. 2) The resource consumption is low, and the depth map can be calculated with a single frame IR map, and the power consumption is low. 3) Active light source, which can also be used at night. 4) High accuracy and high resolution within a certain range, the resolution can reach 1280x1024, and the frame rate can reach 60FPS. 

 ![avatar]( 2019122019005913.jpg) 

 The disadvantages of speckle structured light are similar to those of structured light: 1) It is easily interfered by ambient light and has poor outdoor experience. 2) As the detection distance increases, the accuracy will deteriorate.  

 At present, there are several variants of structured light technology: one is a monocular IR + projected infrared lattice, and the other is a binocular IR + projected infrared lattice, which is equivalent to the fusion of structured light + binocular stereo, and the depth measurement effect will be better than the former. For example, the Intel RealSense R200 uses a binocular IR + projected infrared lattice, which has the disadvantage of being larger in size. Although the monocular IR + projected infrared lattice scheme is smaller in size, the effect will be a little worse. 

 TOF 

 As the name suggests, it is to measure the flight time of light to obtain the distance. Specifically, it is to continuously emit laser pulses to the target, and then use a sensor to receive the reflected light, and to obtain the exact distance of the target by detecting the flight time of the light pulse. Because the speed of light laser is not practical to measure the flight time directly, it is generally realized by detecting the phase shift of the light wave after being modulated by certain means. The TOF method can generally be divided into two types according to the different modulation methods: Pulsed Modulation (Pulsed Modulation) and Continuous Wave Modulation (Continuous Wave Modulation). Pulse modulation requires a very high-precision clock for measurement, and high-frequency and high-intensity lasers need to be emitted. At present, most of the detection phase shift methods are used to realize the TOF function. In simple terms, a processed light is emitted, and it will be reflected back when it touches an object, capturing the back and forth time. Since the speed of light and the wavelength of the modulated light are known, the distance to the object can be quickly and accurately calculated. 

 ![avatar]( 20191220190135877.jpg) 

 Schematic diagram of its principle: Because TOF is not based on feature matching, the accuracy will not decrease rapidly when the test distance becomes longer. At present, unmanned driving and some high-end consumer Lidars basically use this method to achieve. The main advantages of TOF are: 1) The detection distance is long. It can reach tens of meters when the laser energy is sufficient. 2) The interference from ambient light is relatively small. 

 However, TOF also has some obvious problems: 

 1) High requirements on equipment, especially the time measurement module. 2) High resource consumption. This scheme requires multiple sampling integrals when detecting phase shift, and the computation is large. 3) Low edge accuracy. 4) Limited to resource consumption and filtering, the frame rate and resolution cannot be achieved high. 

 ![avatar]( 20191220190205897.jpg) 

 At present, the largest consumer is VGA. From the above three mainstream 3D camera imaging solutions, each has its own advantages and disadvantages, but from the perspective of practical application scenarios, in the non-unmanned field, structure, light, and especially speckle structured light are the most widely used. Because from the perspective of accuracy, resolution, and application scenarios, binocular and TOF cannot achieve the greatest balance. And for structured light, which is easily interfered by ambient light, especially sunlight, given that such cameras have infrared laser emission modules, it is very easy to transform into active binocular to make up for this problem.  

 Contrast between structured light and TOF 

 In comparison, structured light technology consumes less power, is more mature, and is more suitable for static scenes. The TOF solution has lower noise at long distances and higher FPS, so it is more suitable for dynamic scenes. 

 ![avatar]( 2019122019023212.jpg) 

 At present, structured light technology is mainly used in unlocking and secure payment, and its application distance is limited. TOF technology is mainly used for smart phone rear photography, and has a certain role in AR, VR and other fields (including 3D photography, somatosensory games, etc.). 3D structured light and TOF actually have their own advantages and disadvantages. The biggest advantage of structured light is that it is more mature and the cost is relatively low, and the disadvantage is that it is only suitable for medium and short distance use. ToF has the advantage of good anti-interference, wide viewing angle, high power consumption, high cost, and low accuracy and depth map resolution. The two technologies each have their own focus and adaptation to use scenarios. 

 binocular stereo vision 

 Binocular Stereo Vision (Binocular Stereo Vision) is an important form of machine vision. It is based on the principle of parallax and uses imaging equipment to obtain two images of the measured object from different positions, and obtains three-dimensional geometric information of the object by calculating the position deviation between the corresponding points of the image. 

 Of course, the complete binocular depth calculation is very complicated, mainly involving the feature matching of left and right cameras, and the calculation will consume a lot of resources. The main advantages of binocular cameras are: 

 1) Low hardware requirements and low cost. Ordinary CMOS cameras are enough. 2) Suitable for both indoor and outdoor. As long as the light is right, it should not be too dim. 

 But the disadvantages of binocular are also very obvious: 1) It is very sensitive to ambient lighting. Light changes lead to large image bias, which in turn can lead to matching failure or low accuracy 2) It is not suitable for scenes with monotonous lack of texture. Binocular vision performs image matching according to visual features, and no features will lead to matching failure. 3) High computational complexity. This method is a pure visual method, which requires high algorithm requirements and requires a large amount of calculation. 4) The baseline limits the measurement range. The measurement range is proportional to the baseline (two camera spacing), resulting in the inability to miniaturize. 

 ![avatar]( 201912201903045.jpg) 

 Comparison of three depth cameras  

 ![avatar]( 20191220190326547.png) 

 The above is the whole content. There may be some wrong welcome instructions, and you can send emails to communicate. You can follow the WeChat official account. Join our translation team or join the WeChat official account group, and also join the technical exchange group to communicate with more friends.  



--------------------------------------------------------------------------------

