# Sending Goals to Turtlebot3 Navigation Stack
>Adapted From Sending Goals to the Navigation Stack --> https://hotblackrobotics.github.io/en/blog/2018/01/29/action-client-py/

## Navigation Stack --> navigation-ROSwiki
<p align="center">
<img src="https://user-images.githubusercontent.com/86387081/123408785-5fb8af00-d5e8-11eb-9712-c77ad8606a31.png" width="640" height="360" />
</p>

This tutorial will teach you how to send the simple goal to move_base node with python code.
## ActionLib --> AcionLib-ROSwiki
* goal
* result
* feedback
## Try it yourself
0.Launch Turtlebot Simulation and Navigation
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
roslaunch turtlebot3_navigation turtlebot3_navigation.launch
```

1. Create new package
```
cd ~/your_ws/src
catkin_create_pkg my_package std_msgs rospy roscpp
```
2. Make scripts folder in src of the beginner_tutorials package
```
cd ./my_package
mkdir scripts
```
3. Put the following code in to ~/your_ws/src/beginner_tutorials/scripts
```
#!/usr/bin/env python
# license removed for brevity

import rospy

# Brings in the SimpleActionClient
import actionlib
# Brings in the .action file and messages used by the move base action
from move_base_msgs.msg import MoveBaseAction, MoveBaseGoal
from geometry_msgs.msg import PoseStamped


class Turtlebot3():
  def __init__(self):
    # For movebase
    # Create an action client called "move_base" with action definition file "MoveBaseAction"
    self.client = actionlib.SimpleActionClient('move_base',MoveBaseAction)

    # Waits until the action server has started up and started listening for goals.
    self.client.wait_for_server()


  def trajectory_execute(self,pose): 
      
    self.group.set_pose_target(pose, end_effector_link="tool_ee_link")
    self.group.go(wait=True)
    self.group.stop()
    self.group.clear_pose_targets()

  def get_movebaseGoal_from(self,target_list):
    goal = MoveBaseGoal()
    goal.target_pose.header.frame_id = "map"
    goal.target_pose.header.stamp = rospy.Time.now()
    goal.target_pose.pose.position.x = target_list[0]
    goal.target_pose.pose.position.y = target_list[1]
    goal.target_pose.pose.position.z = target_list[2]

    goal.target_pose.pose.orientation.w = 1.0
    return goal




  def commander(self):
    print("process start")
    while not rospy.is_shutdown():
        print("Enter target spearated with comma")
        target = input()
        movebaseGoal = self.get_movebaseGoal_from(target)
        self.client.send_goal(movebaseGoal)
        # Waits for the server to finish performing the action.
        wait = self.client.wait_for_result()
        # If the result doesn't arrive, assume the Server is not available
        if not wait:
            rospy.loger("Action server not available!")
            rospy.signal_shutdown("Action server not available!")
        else:
        # Result of executing the action
            print("Goal Reached")
        

if __name__ == '__main__':
    try:
        rospy.init_node('spaghetti_grasping_rgbd_execute', anonymous=True)
        turtle = Turtlebot3()
        turtle.commander()
    except rospy.ROSInterruptException:
        pass
    

```
4. make the file executable
```
cd ~/your_ws/src/my_package/scripts
chmod +x ./yourfilename.py
```
5. run the commander script
```
rosrun my_package yourfilename.py
```

## Your Homework
Make a publisher node publishing Pose message to this commander node


<p align="center">
<img src="https://user-images.githubusercontent.com/55285546/123536339-b5b26180-d764-11eb-8ce9-0a2f293f54b0.png"  />
</p>

Edit commander node to subscribe Pose message as follow

```
def commander(self):
    print("process start")
    while not rospy.is_shutdown():
        print("Enter target spearated with comma")

        #target = input() # <--- Change This
        target = rospy.wait_for_message("your_topic", PoseStamped) # <--- To This


        movebaseGoal = self.get_movebaseGoal_from(target) #target is a Pose message contaning position and orientation

        self.client.send_goal(target) #<-- Can pass target directly since target is now PoseStamped

        # Waits for the server to finish performing the action.
        wait = self.client.wait_for_result()
        # If the result doesn't arrive, assume the Server is not available
        if not wait:
            rospy.loger("Action server not available!")
            rospy.signal_shutdown("Action server not available!")
        else:
        # Result of executing the action
            print("Goal Reached")
```            
```
def get_movebaseGoal_from(self,target_pose): #Now target_list become target_pose
    goal = MoveBaseGoal()
    goal.target_pose.header.frame_id = "map"
    goal.target_pose.header.stamp = rospy.Time.now()
    goal.target_pose.pose.position.x = target_pose.position.x
    goal.target_pose.pose.position.y = target_pose.position.y
    goal.target_pose.pose.position.z = target_pose.position.z

    goal.target_pose.pose.orientation.w = target_pose.orientation.w
    return goal
```

>Google Hint: rospy pose publisher

