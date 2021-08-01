# Xarm 7 ROS

## Installation
> official site : https://github.com/xArm-Developer/xarm_ros

### Real Robot-Moveit
1. Install moveit : 
```
sudo apt install ros-melodic-moveit
```
2. Create a catkin workspace.
3. Build Ros-Xarm from src
```
cd ~/catkin_ws/src
git clone https://github.com/xArm-Developer/xarm_ros.git --recursive
cd ~/catkin_ws/src/xarm_ros
git pull
git submodule sync
git submodule update --init --remote
```
4. Install dependencies
```
rosdep update
rosdep install --from-paths . --ignore-src --rosdistro melodic -y
```
5. Build the package
```
cd ~/catkin_ws
catkin build
source ~/.bashrc
```
6. First try out in RViz
```
roslaunch xarm_description xarm7_rviz_display.launch
```
7. Config ip address in launcher file
```
roscd xarm7_moveit_config/
gedit realMove_exec.launch
<arg name="robot_ip" default="192.168.1.xxx"/> 
(current : 192.168.1.213)
```
8. Launch Xarm-Moveit
```
roslaunch xarm7_moveit_config realMove_exec.launch
```

### Gazebo-Moveit
1. Follow real robot installation.
2. Download the 'table' 3D model.
> open gazebo --> Insert --> Wait for database connection --> drag the Table to gazebo
> ![Screenshot from 2021-08-01 11-55-28](https://user-images.githubusercontent.com/47204875/127757600-ddbb33b2-254c-4464-9828-f51cee5e022c.png)



3. Install mimic-joint-plugin for gripper
```
git clone https://github.com/roboticsgroup/roboticsgroup_gazebo_plugins.git
cd ~/catkin_ws
catkin build
source ~/.bashrc
```

4. Check xarm-gazebo
```
$ roslaunch xarm_gazebo xarm7_beside_table.launch [run_demo:=true] [add_gripper:=true] [add_vacuum_gripper:=true] 
```
4. Install dependencies
```
rosdep update
rosdep install --from-paths . --ignore-src --rosdistro melodic -y
```
5. Build the package
```
cd ~/catkin_ws
catkin_make
source ~/.bashrc
```
6. First try out in RViz
```
roslaunch xarm_description xarm7_rviz_display.launch
```
7. Config ip address in launcher file
```
roscd xarm7_moveit_config/
gedit realMove_exec.launch
<arg name="robot_ip" default="192.168.1.xxx"/> 
(current : 192.168.1.213)
```
8. Launch Xarm-Moveit
```
roslaunch xarm7_moveit_config realMove_exec.launch
```

## Tutorial

### Command Xarm7 with Moveit-Python
1. bring up the robot
```
roslaunch xarm7_moveit_config realMove_exec.launch
```

