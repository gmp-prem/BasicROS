# High level control for Turtlebot3
>Adapted From Sending Goals to the Navigation Stack --> https://rsl.ethz.ch/education-students/lectures/ros.html

## Theory
- ROS publisher
- Launch File
- TF Transformation System 

## Preparation
- Download Realated Files
https://teams.microsoft.com/_#/school/files/General?threadId=19%3Ae41dbea835b646b8affa25fa7a1f7c58%40thread.tacv2&ctx=channel&context=DownloadFiles&rootfolder=%252Fsites%252FYaskawa-research%252FShared%2520Documents%252FGeneral%252FHW2%252FDownloadFiles


- Add new launch file to launch the turtlebot3 gazebo with a singlePillarWorld.world

```
roscd turtlebot3_simulations
code .
```
Your VScode workspace should look like this
![vscodeWS](https://user-images.githubusercontent.com/55285546/124456445-a87d1e80-ddc5-11eb-93b4-8b954f5297aa.png)

- Create new file name singlePillarWorld.world in worlds folder and Copy the following code to the singlePillarWorld.world

<details open>
<summary>Code!</summary>

```xml
<?xml version="1.0" ?>
<sdf version="1.4">
  <world name="default">
    <!-- A global light source -->
    <include>
      <uri>model://sun</uri>
    </include>
    <!-- A ground plane -->
    <include>
      <uri>model://ground_plane</uri>
    </include>
    <!-- Cylinder -->
    <model name='unit_cylinder'>
      <pose frame=''>1 1 0.5 0 -0 0</pose>
      <link name='link'>
        <inertial>
          <mass>1</mass>
          <inertia>
            <ixx>0.145833</ixx>
            <ixy>0</ixy>
            <ixz>0</ixz>
            <iyy>0.145833</iyy>
            <iyz>0</iyz>
            <izz>0.125</izz>
          </inertia>
        </inertial>
        <collision name='collision'>
          <geometry>
            <cylinder>
              <radius>0.5</radius>
              <length>1</length>
            </cylinder>
          </geometry>
          <max_contacts>10</max_contacts>
        </collision>
        <visual name='visual'>
          <geometry>
            <cylinder>
              <radius>0.5</radius>
              <length>1</length>
            </cylinder>
          </geometry>
          <material>
            <script>
              <name>Gazebo/Grey</name>
              <uri>file://media/materials/scripts/gazebo.material</uri>
            </script>
          </material>
        </visual>
        <self_collide>0</self_collide>
        <kinematic>0</kinematic>
      </link>
    </model>


  </world>
</sdf>
```
</details>


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

