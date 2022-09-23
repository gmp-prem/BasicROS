**ROS Computational graph**

ROS computational graph is where the data is processing in ROS workspace, this concept consist of nodes, Master, Parameter Server, messages, services, topics, and bags. [Here](https://github.com/gmp-prem/BasicROS/blob/main/Images/roscompgraph.png) is the link to full concept of computation graph diagram, and [Here](http://wiki.ros.org/ROS/Concepts#:~:text=services%20in%20ROS.-,ROS%20Computation%20Graph%20Level,the%20Graph%20in%20different%20ways.) is the link to full detail
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rospubsub.png" width="500" height="120">
</p>

ROS message is a simplified messages description language for describing the data values (aka messages) that ROS nodes publish, it has a structure.

Go to catkin_ws/src/my_package and create folder scripts
```
cd catkin_ws/src/my_package
```
Create a folder
```
mkdir scripts
```
Go to scripts
```
cd scripts
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rosdiagram.png" width="500" height="120">
</p>

Now, we will create two python scripts for our first 2 ROS programs
```
touch publisher.py
touch listener.py
```
Since you are going to execute the script, you are gonna need to make it executable
```
chmod +x publisher.py
chmod +x listener.py
```

To start coding, you could use your favorite text editer, or gedit as you would like to

Writing a publisher
```
code is [here](publisher_subscriber/publisher.py)
```

Writing a subscriber
```
code is [here](publisher_subscriber/subscriber.py)
```
To run the code, please do the following
```
roscore
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/roscore.png" width="500" height="300">
</p>

Run the publisher node
```
rosrun my_package publisher.py
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/pub.png" width="500" height="300">
</p>

Run the subscriber node 
```
rosrun my_package listener.py
```
Here you can see that in the subsciber terminal, it will show something up
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/sub.png" width="500" height="300">
</p>

**ROS Visualization tool**

ROS Visulization (Rviz) is the ROS application, it provieds many advantages when you work with your robot such as robot model, sensor information, camera. Here is the [link](http://wiki.ros.org/rviz/Tutorials) to the full description from ROS wiki
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rviz_plugin_head.png" width="500" height="300">
</p>

Thank you very much

## Mutiple Workspace with catkin tool
1. Create new work space with src folder (or copy src folder of other workspace)
2. Create empty build and devel folder
```
cd ~/new_ws
mkdir build
mkdir devel
```
3. Initialize catkin workspace
```
catkin init -w .
```
4. Build the src of the workspace
```
rosdep install --from-paths src --ignore-src -r -y
catkin build
```
5. source the devel setup
```
source ~/new_ws/devel/setup.bash
```