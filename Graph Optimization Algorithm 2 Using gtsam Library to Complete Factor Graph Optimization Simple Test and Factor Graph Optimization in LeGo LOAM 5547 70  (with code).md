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
