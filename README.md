# ROS Tutorial
> Tutorial for beginner who wants to start using ROS on Ubuntu

## Topics
1. Getting started with Linux
   - What is a Linux?
   - Ubuntu interface
   - Performing task on Ubuntu
   - Basic commands
2. Basic robot operating system (ROS)
   - What is ROS?
   - ROS concept

## Getting started with Linux
### _What is Linux?_
[**Linux**](https://www.linux.com/what-is-linux/) is an open-source Unix-like OS that manages communication between hardward and software, since Linux is an open-source, many distributions(versions) have been developed, one of the most popular one is [**Ubuntu**](https://ubuntu.com/) we use today.

<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/interface.png" width="500" height="300">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-logo.png" width="120" height="120">
</p>

### _Ubuntu interface_
**Desktop elements**

<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-desktop-edited-fixed.png" width="500" height="300">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-launchpad.png" width="500" height="300">
</p>

### _Performing task on Ubuntu_
**Shell** is a command-line interface that interprets what should the ubuntu perform from command of user, there are many shells out there but the default one of ubuntu is Bourne-Again shell or bash

As a developer, most of time we spend on ubuntu doing tasks will use what we called **terminal**, terminal is a power tool that uses shell to interprets the command and it gives us ability to
  - Navigating
  - Manipulating
  - Diagnosis
  - More++

You can start using **command prompt** or **terminal** by go to a launcher and type the following word and enter
```
terminal
```
or the another way is to use the short-cut which is way better and faster, just press `ctrl` + `alt` + `t`
then your terminal should appear as shown below
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-terminal.png" width="500" height="300">
</p>

You can see that on the terminal there is a `hayashi@lab:~$`

`hayashi` is the username indicated before @ symbol

`lab` is the hostname indicated after @ symbol

`~` is the directory you are working on (~ or "tilt" means the home directory)

`$` is prompt symbol, this symbol will tell where the command you type begin

**Basic commands**

**ls**, ls will list what file are in the directory you are working on
```
ls
```

**cd**, cd is the command to change the directory that you want to go to work
```
cd ~/Desktop
```

If you want to edit the script or text file, Ubuntu has provided us the default text editor which is called **gedit**, of course there are more text editors, some text editor gives more functionality for coding such [visual studio code](https://code.visualstudio.com/docs/setup/linux), [vim](https://www.vim.org/), [nano](https://linuxize.com/post/how-to-use-nano-text-editor/#:~:text=GNU%20nano%20is%20an%20easy,%2D8%20encoding%2C%20and%20more.) and more
```
gedit my_text_editor
```

**sudo**, sudo stands for superuser do, this command gives ability to be an administrator or root privileges, some files could not be directly used local, so the sudo comes into this position

example of sudo command, from the command below, you could see that the terminal will warn us about the permission to update file repository
```
apt update
```

to use this command properly, we need to append sudo in front of the command
```
sudo apt update
```

These are just the basic commands, if you would like to know more, here is the [link](https://www.hostinger.com/tutorials/linux-commands) to my recommend page to read about command on Linux

### _Why Ubuntu on developing Robotics?_ :fire:
- lightweightness, ubuntu is lightweight in its nature, ypu don't have to pay to get access, you can install along side with your existing operating system, just donwload, install and use!
- the distribution of ubuntu is a long-term support (usually 5 years)
- tons of community support, ubuntu has a great community whenever you have a problem, you could get help such as [ubuntu community](https://ubuntu.com/community) or [stackoverflow](https://stackoverflow.com/) and more communities++ out there

## Basic robot operating system (ROS)

### _What is ROS?_
Robot operating system or [ROS](https://www.ros.org/) for short, ROS is an open-source framework for developing a robotics, ROS has a simple concept and easy to understand, ROS has a lot of communities, so many engineers and researchers use this framework to develop their own robot applications.
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ros-logo.jpg" width="400" height="200">
</p>

### _ROS concept_

**ROS filesystem level**

ROS filesystem level is the part of the ROS that consider the filesystem on the disk, the filesystem level mainly consists of packages, metapackages and message type, service types.
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rosfilesystemlevel.png" width="650" height="300">
</p>

**ROS workspace**

ROS workspace is where you modify, build, and install catkin packages, the workspace will usually contain build, devel and src folder
- build is where the build file of the workspace is kept, all cache and information about build is here
- devel stands for development, it is where the built target is stored, after the build configuration
- src stands for source, it is where the source file of the workspace are kept, your script file, your package that follows the rule of the filesystem level 
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rosworkspace.png" width="500" height="300">
</p>

**Let's create ROS workspace !**

Before create the workspace, we must install the _catkin_tool_ package which contains the build tool for our workspace

Open up your terminal using `ctrl` + `alt` + `t`, and get ROS repository that contains the catkin_tool
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu `lsb_release -sc` main" > /etc/apt/sources.list.d/ros-latest.list'
```
Setup the key for the ROS repository
```
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
```
Update the latest version of packages from repositories
```
sudo apt-get update
```
Install catkin_tool package
```
sudo apt-get install python-catkin-tools
```
For additional info about the catkin_tool package, please visit this [link](https://catkin-tools.readthedocs.io/en/latest/index.html)

Now we are ready to create our ROS workspace !

To create ROS workspace, open the terminal using shortcut `ctrl` + `alt` + `t` or you can go open the launchpad and type _terminal_ to open your terminal

next, create the folder for your ROS workspace
```
mkdir -p ~/catkin_ws/src
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/createrosws-01.png" width="500" height="275">
</p>

Go to the catkin_ws directory
```
cd catkin_ws
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/createrosws-02.png" width="500" height="275">
</p>

Build your ROS workspace 
```
catkin build
```
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/createrosws-03.png" width="500" height="275">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/createrosws-04.png" width="500" height="275">
</p>

your workspace is built with this command then it is ready for your robot application, you could see 3 new folders which are build, devel and logs folder, the logs folder here will just log what catkin build did for you if you want to know what happened of last build

After the workspace has created, we will source our workspace to bashrc file (we will skip this detail for now), let's go back to home directory and type this command on your terminal
```
cd && echo "source ~/catkin_ws/devel/setup.sh" >> ~/.bashrc && source ~/.bashrc
```

For additional info about creating ROS workspace, please visit this [link](http://wiki.ros.org/catkin/Tutorials/create_a_workspace)

**Create the your first package**

Next we will create first ROS package, first let's change directory to src in catkin_ws
```
cd ~/catkin_ws/src
```
Create a package
```
catkin_create_pkg my_package rospy roscpp std_msgs
```
Your package has created, you could check the current directory by using `ls` command, next you have to go back to catkin_ws to build your workspace
- [ ] image after enter above create package command

`catkin_create_pkg my_package rospy roscpp std_msgs` has a form `catkin_create_pkg <package_name> [depend1] [depend2] [depend3]`

- catkin_create_pkg is the command the create the package in your ROS workspace
- package_name is the name of the package, you could name this package whatever you want
- dependency means ROS packages that your package depends on

```
cd ..
```
Then
```
catkin build
```
Now you will see the terminal shows that the package _my_package_ has been built
- [ ] image after build the workspace

For additional info about creating ROS package, please visit this [link](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

**ROS Computational graph**

ROS computational graph is where the data is processing in ROS workspace, this concept consist of nodes, Master, Parameter Server, messages, services, topics, and bags 
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rospubsub.png" width="500" height="120">
</p>



- [ ] image of concept
- [ ] ROS message
- [ ] publisher/subscriber

**ROS Visualization tool**

- [ ] explain what rviz is?
- [ ] example?
