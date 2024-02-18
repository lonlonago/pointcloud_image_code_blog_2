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

