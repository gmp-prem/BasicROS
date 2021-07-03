# High level control for Turtlebot3
>Adapted From Sending Goals to the Navigation Stack --> https://rsl.ethz.ch/education-students/lectures/ros.html

## Theory
- ROS publisher
- TF Transformation System 


## Homework2
1. Launch Turtlebot3 with the singlePillar.world

```
```

2. Extract the position of the pillar from the laser scan with respect to the robot.
```
```

3. Publish a visualization marker for RViz that shows the estimated position of the pillar.
(easy) Publish the point in the sensor frame (rslidar) as an RViz marker. RViz
will automatically transform the marker into the odom frame.
http://wiki.ros.org/rviz/DisplayTypes/Marker
OR
(more difficult) Implement a TF listener to transform the extracted point from
the laser frame to the odom frame.
http://wiki.ros.org/tf/Tutorials/Writing%20a%20tf%20listener%20%28C%2B%
2B%29
```
```


## Homework3


1. Create a publisher on the topic /cmd_vel to be able to send a twist command to Turtlebot3
```
```

2. Write a simple P controller that drives Turtlebot3 towards the pillar. 
Remember to use ROS parameters for your controller gains 
You can pass them as arguments to the turtlebot3_gazebo.launch
```
```





>Hint: https://answers.ros.org/question/198843/need-explanation-on-sensor_msgslaserscanmsg/

