# Learn ROS with Turtlebot3 Simulation
* Ubuntu Version : 18.xx
* ROS Version : melodic
## Installation

>[Turtlebot3 Quick Start Guide](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/)

In case 404 IP not found
https://answers.ros.org/question/325039/apt-update-fails-cannot-install-pkgs-key-not-working/

1. Clone main package → https://github.com/ROBOTIS-GIT/turtlebot3_msgs
```
cd ~/catkin_ws/src
git clone https://github.com/ROBOTIS-GIT/turtlebot3
```
2. Clone simulation package → https://github.com/ROBOTIS-GIT/turtlebot3_msgs
```
git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
```
3. Build the loaded packages
```
cd ~/catkin_ws
catkin build
```



***
**In case some dependencies is missing,Use rosdep and build again**


Install rosdep → rosdep - ROS Wiki

```
sudo apt-get install python-rosdep
```
Install dependency of all packages in the workspace
```
rosdep install --from-paths src --ignore-src -r -y
```

***

4. Source your workspace and Export robot model
```
gedit ~/.bashrc
```
In .bashrc, add
- source ~/catkin_ws/devel/setup.sh
- export TURTLEBOT3_MODEL=burger

5. source the bash script or re-open the terminal
```
source ~/.bashrc
```

6. Launch turtlebot simulation
```
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

<p align="center">
<img  src="https://github.com/gmp-prem/BasicROS/blob/main/Images/turtlebot3_empty_world.png"  />
</p>

## How to move the robot?
Run Teleop Node
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
Check the communication between ROS node
```
rqt_graph
```

<p align="center">
<img src="https://user-images.githubusercontent.com/86387081/123276239-f41b0700-d53f-11eb-936c-c93ca759ef30.png" width="720" height="720" />
</p>
