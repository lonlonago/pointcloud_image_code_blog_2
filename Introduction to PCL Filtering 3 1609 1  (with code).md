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

