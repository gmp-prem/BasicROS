# Learn ROS with Turtlebot3 Simulation
* Ubuntu Version : 18.xx
* ROS Version : melodic
## Installation
### Install with apt-get command
Follow the official quick start guide 

>[Turtlebot3 Quick Start Guide](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/)

### Building from Source
1. Clone main respiratory →ROS packages for Turtlebot3 (github.com)
```
cd ~/your_ws/src
git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
```
2. Clone simulation package → Simulations for TurtleBot3 (github.com)
```
git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
```
3. Build the loaded packages
```
cd ~/your_ws
catkin build
```



***
**In case some package is missing,Use rosdep and build again**


Install rosdep → rosdep - ROS Wiki

```
sudo apt-get install python-rosdep
```
Install dependency of all packages in the workspace
```
rosdep install --from-paths src --ignore-src -r -y
```

***

5. Source your workspace ***very important***
```
source ~/.bashrc
```

6. Export robot model
```
code ~/.bashrc
```
At the end of the .bashrc, add
>export TURTLEBOT3_MODEL=burger

7. source again
```
source ~/.bashrc
```

8.
```
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

<p align="center">
<img  src="https://user-images.githubusercontent.com/86387081/123275201-16605500-d53f-11eb-8d82-794475e67cc1.png" width="600" height="600"  />
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
