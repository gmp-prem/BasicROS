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
> Step 7&8 only for real robot

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
1. Follow real robot installation except step 7&8.
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

4. Launch xarm-gazebo
```
roslaunch xarm_gazebo xarm7_beside_table.launch 
```
5. On the other terminal, launch Xarm-Moveit-Gazebo 
```
roslaunch xarm7_moveit_config xarm7_moveit_gazebo.launch
```
6. Try Move the simulated robot with Moveit


## Tutorial

### Command Xarm7 with Moveit-Python Interface
> official moveit guide: 
> http://docs.ros.org/en/melodic/api/moveit_tutorials/html/doc/move_group_python_interface/move_group_python_interface_tutorial.html

1. Bring up the real robot
```
roslaunch xarm7_moveit_config realMove_exec.launch
```
or bring up the simulation robot with Moveit interface
```
roslaunch xarm_gazebo xarm7_beside_table.launch
roslaunch xarm7_moveit_config xarm7_moveit_gazebo.launch

```
2. Create new package for locating the commander script
```
cd ~/catkin_ws
catkin_create_pkg beginner rospy roscppp
catkin build
cd ~/catkin_ws/src/beginner
mkdir scripts
cd ~/catkin_ws/src/beginner/scripts
code .
```
3. In scripts folder, create new python file xarm7_commander.py (name is up to you) and add the following code to your file
> https://drive.google.com/file/d/1wVBjbc_S27vWbqFxaZw-OkaOEE_XPNar/view?usp=sharing

4. In terminal, make the script executable
```
chmod +x cd ~/catkin_ws/src/beginner/scripts/xarm7_commander.py
```
5. Run the commander scripts
```
rosrun beginner xarm7_commander.py
```


## Homework

1. Add oreintation of the end effector as an input in euler angle relative to the world coordinate frame
> Hint edit this part of commander
```
def get_pose_from_(self,target): # <-- add more argument or more object in target list
        goal = Pose()

        goal.position.x = target[0]
        goal.position.y = target[1]
        goal.position.z = target[2]
        
        quaternion = Some_Euler_to_Quaternion_Function(Euler Angle)
        
        #goal.orientation.x = quaternion[0] 
        #goal.orientation.y = quaternion[1]
        #goal.orientation.z = quaternion[2]
        #goal.orientation.w = quaternion[3]
        
        
        return goal
```

> Google Hint : ros euler to quaternion

2. Check by commanding the robot to move to hold up position you can find the position of the end effector in RVIZ
![Screenshot from 2021-08-01 13-35-58](https://user-images.githubusercontent.com/47204875/127759470-efde3965-d54a-48b5-a471-60f7d11b8afb.png)



## Add Virtual Camera

1. under ~/xarm_ros/xarm_description add xarm7_virtual_hand_camera.xacro
> https://drive.google.com/file/d/1a5tet8f5SHVwsSoi5mFjCeiatutRuMwq/view?usp=sharing

2. edit gazebo bring up file 
3. 
