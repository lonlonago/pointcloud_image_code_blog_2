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

