# Utra ROS

## Installation
> official site : https://github.com/UmbraTek/utra_ros

### Real Robot-Moveit
1. Install moveit : 
```
sudo apt install ros-melodic-moveit
```

2. Create a catkin workspace.
3. Build Ros-utra from src
```
cd ~/utra_ws/src
git clone https://github.com/UmbraTek/utra_ros
```
4. Install dependencies
```
cd ~/utra_ws
rosdep update
rosdep install --from-paths . --ignore-src --rosdistro melodic -y
```
4.5 Edit CMakeLists.txt file according for using catkin build tools

> https://github.com/UmbraTek/utra_ros/issues/1


5. Build the package
```
cd ~/utra_ws
catkin build
// Dont for get to source utra_ws/devel/setup.bash
source ~/.bashrc
```
6. First try out in RViz
```
roslaunch utra_description utra6_850_view.launch [gripper:=true] [vacuum_gripper:=true]
```
> Step 7&8 only for real robot

7. Add new moveit launch file
```
roscd utra6_850_moveit_config/launch/
gedit ./utra_bringup.launch
```
```
<launch>
    <arg  name="utra_ip" default="192.168.0.240"/>
    <include file="$(find utra_controller)/launch/utra_server.launch">
        <arg name="utra_ip" value="$(arg utra_ip)" />
    </include>

    <include file="$(find utra_controller)/launch/joint_trajectory_6.launch">
        <arg name="utra_ns" value="utra6_850/arm_joint_controller/follow_joint_trajectory" />
    </include>
    
    <include file="$(find utra_controller)/launch/joint_publisher_6.launch">
        <arg name="utra_ns" value="utra/joint_states_850" />
    </include>

    <include file="$(find utra6_850_moveit_config)/launch/demo.launch">
        <arg name="ompl" value="ompl_s"/>
    </include>
    
</launch>
```

8. Launch Utra-Moveit

`The package is in /worksp/utra/src/utra_ros/...`
```
roslaunch utra6_850_moveit_config utra_brinup.launch
```
or
```
roslaunch utra6_550_moveit_config utra_550_brinup.launch
```

### Gazebo-Moveit
1. Follow real robot installation except step 7&8.
2. Launch utra-gazebo
```
roslaunch utra6_850_gazebo gazebo.launch
```
5. On the other terminal, launch Utra-Moveit-Gazebo 
```
roslaunch utra6_850_moveit_config moveit_planning_execution.launch
```
6. Try Move the simulated robot with Moveit


## Tutorial

### Command Utra with Moveit-Python Interface
> official moveit guide: 
> http://docs.ros.org/en/melodic/api/moveit_tutorials/html/doc/move_group_python_interface/move_group_python_interface_tutorial.html

1. Bring up the real robot
```
roslaunch utra6_850_moveit_config utra_brinup.launch
```
or bring up the simulation robot with Moveit interface
```
roslaunch utra6_850_gazebo gazebo.launch
roslaunch utra6_850_moveit_config moveit_planning_execution.launch
```
2. Create new package for locating the commander script
```
cd ~/utra_ws
catkin_create_pkg rospy_moveit rospy roscppp
catkin build
cd ~/utra_ws/src/rospy_moveit
mkdir scripts
cd ~/utra_ws/src/rospy_moveit/scripts
code .
```
3. In scripts folder, create new python file utra_move.py (name is up to you) and add the following code to your file
> https://drive.google.com/file/d/1BcHe7QT1tpZbk_1zk5zoaaJeQ35FSYEW/view?usp=sharing

4. In terminal, make the script executable
```
chmod +x cd ~/utra_ws/src/beginner/rospy_moveit/utra_move.py
```
5. Run the commander scripts
```
rosrun rospy_moveit utra_move.py
```




