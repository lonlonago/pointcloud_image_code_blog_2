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

