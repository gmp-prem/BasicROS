# High level control for Turtlebot3
>ETH Zurich ROS Tutorails --> https://rsl.ethz.ch/education-students/lectures/ros.html

## Theory
- ROS publisher
- Launch File
- TF Transformation System 

## Preparation
- Download Realated Files:

>https://drive.google.com/drive/folders/1MmvZWoe22qdzP9undzGr8FvS3xbCxXlt?usp=sharing

![screenshot-nimbus-capture-2021 07 05-19_47_44](https://user-images.githubusercontent.com/55285546/124460196-06136a00-ddca-11eb-8175-d68e383f4b33.png)


- Add new files to launch the turtlebot3 gazebo with a singlePillarWorld.world

```
roscd turtlebot3_gazebo
code .
```
Your VScode workspace should look like this
![vscodeWS](https://user-images.githubusercontent.com/55285546/124456445-a87d1e80-ddc5-11eb-93b4-8b954f5297aa.png)

- Add singlePillarWorld.world in worlds folder and turtlebot3_singlePillarWorld.launch in launch folder
- Launch turtlebot3 with singlePillarWorld
```
roslaunch turtlebot3_gazebo turtlebot3_singlePillar.launch
```
- Launch Rviz Visualizer
```
roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch
```
![Screenshot from 2021-07-05 19-59-56](https://user-images.githubusercontent.com/55285546/124461526-b6ce3900-ddcb-11eb-9660-f369954c9451.png)


## Homework2

1. Extract the closest (x,y) position of the pillar from the laser scan with respect to the laser coordinate.
>the range and degree of the laser is in r-theta coordinate so some calculation is required.
```
#!/usr/bin/env python
# license removed for brevity

import rospy

# Brings in the SimpleActionClient
import actionlib
# Brings in the .action file and messages used by the move base action
from move_base_msgs.msg import MoveBaseAction, MoveBaseGoal
from geometry_msgs.msg import PoseStamped
from sensor_msgs.msg import LaserScan

from visualization_msgs.msg import Marker

import numpy as np


class LaserScanner():
  def __init__(self, test_move = False):

    self.pillar_marker = Marker()


  def trajectory_execute(self,pose): 
      
    self.group.set_pose_target(pose, end_effector_link="tool_ee_link")
    self.group.go(wait=True)
    self.group.stop()
    self.group.clear_pose_targets()

  def get_pillar_pose_from(self,target_list):
    
    self.pillar_pose.pillar_pose.header.frame_id = "base_scan"
    self.pillar_pose.pillar_pose.header.stamp = rospy.Time.now()
    self.pillar_pose.pillar_pose.pose.position.x = target_list[0]
    self.pillar_pose.pillar_pose.pose.position.y = target_list[1]
    self.pillar_pose.pillar_pose.pose.position.z = target_list[2]

    self.pillar_pose.target_pose.pose.orientation.w = 1.0
    

  def laser_callback(self,msg): 
    
    #-----------Put Your Code HERE--------------------#
    
    print(x_scan,y_scan)
    
    
    self.pillar_marker.header.frame_id = "base_scan"
    self.pillar_marker.type = self.pillar_marker.SPHERE
    self.pillar_marker.action = self.pillar_marker.ADD
    self.pillar_marker.scale.x = 0.1
    self.pillar_marker.scale.y = 0.1
    self.pillar_marker.scale.z = 0.1
    self.pillar_marker.color.a = 1.0
    self.pillar_marker.color.r = 1.0
    self.pillar_marker.color.g = 1.0
    self.pillar_marker.color.b = 0.0
    self.pillar_marker.pose.orientation.w = 1.0
    self.pillar_marker.pose.position.x = x_scan
    self.pillar_marker.pose.position.y = y_scan 
    self.pillar_marker.pose.position.z = 0.0

    self.marker_pub.publish(self.pillar_marker)
    

  def read_scan(self):
    print("process start")

    #self.marker_pub = rospy.Publis('/scan', LaserScan, self.laser_callback)
    self.marker_pub = rospy.Publisher('goal', Marker, queue_size = 100)
    self.laser_sub = rospy.Subscriber('/scan', LaserScan, self.laser_callback)
    
    r = rospy.Rate(60) # 10hz 
    while not rospy.is_shutdown():
      #doint nothing here just looping
      r.sleep()
        

if __name__ == '__main__':
    try:
        rospy.init_node('spaghetti_grasping_rgbd_execute', anonymous=True)
        laser = LaserScanner()
        laser.read_scan()
    except rospy.ROSInterruptException:
        pass
```

2. Publish a visualization marker for RViz that shows the estimated position of the pillar.
(easy) Publish the point in the sensor frame (rslidar) as an RViz marker. RViz
will automatically transform the marker into the odom frame.
http://wiki.ros.org/rviz/DisplayTypes/Marker
OR
(more difficult) Implement a TF listener to transform the extracted point from
the laser frame to the odom frame.
http://wiki.ros.org/tf/Tutorials/Writing%20a%20tf%20listener%20%28C%2B%
2B%29
```
#!/usr/bin/env python
# license removed for brevity

import rospy

# Brings in the SimpleActionClient
import actionlib
# Brings in the .action file and messages used by the move base action
from move_base_msgs.msg import MoveBaseAction, MoveBaseGoal
from geometry_msgs.msg import PoseStamped
from sensor_msgs.msg import LaserScan

from visualization_msgs.msg import Marker

import numpy as np


class LaserScanner():
  def __init__(self, test_move = False):

    self.pillar_marker = Marker()


  def trajectory_execute(self,pose): 
      
    self.group.set_pose_target(pose, end_effector_link="tool_ee_link")
    self.group.go(wait=True)
    self.group.stop()
    self.group.clear_pose_targets()

  def get_pillar_pose_from(self,target_list):
    
    self.pillar_pose.pillar_pose.header.frame_id = "base_scan"
    self.pillar_pose.pillar_pose.header.stamp = rospy.Time.now()
    self.pillar_pose.pillar_pose.pose.position.x = target_list[0]
    self.pillar_pose.pillar_pose.pose.position.y = target_list[1]
    self.pillar_pose.pillar_pose.pose.position.z = target_list[2]

    self.pillar_pose.target_pose.pose.orientation.w = 1.0
    

  def laser_callback(self,msg): 
    
    #-----------Put Your Code HERE--------------------#
    
    
    
     #-----------Put Your Marker Publisher HERE--------------------#
    
    print(x_scan,y_scan)
    

  def read_scan(self):
    print("process start")

    #self.marker_pub = rospy.Publis('/scan', LaserScan, self.laser_callback)
    self.marker_pub = rospy.Publisher('goal', Marker, queue_size = 100)
    self.laser_sub = rospy.Subscriber('/scan', LaserScan, self.laser_callback)
    
    r = rospy.Rate(60) # 10hz 
    while not rospy.is_shutdown():
      #doint nothing here just looping
      r.sleep()
        

if __name__ == '__main__':
    try:
        rospy.init_node('spaghetti_grasping_rgbd_execute', anonymous=True)
        laser = LaserScanner()
        laser.read_scan()
    except rospy.ROSInterruptException:
        pass
```

```
rosrun my_package scanner.py
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

