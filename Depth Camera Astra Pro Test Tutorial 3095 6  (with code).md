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

