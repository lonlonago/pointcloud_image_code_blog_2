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
