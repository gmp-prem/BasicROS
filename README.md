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
### What is Linux?
[**Linux**](https://www.linux.com/what-is-linux/) is an open-source Unix-like OS that manages communication between hardward and software, since Linux is an open-source, many distributions(versions) have been developed, one of the most popular one is [**Ubuntu**](https://ubuntu.com/) we use today.

<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/interface.png" width="500" height="300">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-logo.png" width="120" height="120">
</p>

### Ubuntu interface
**Desktop elements**

<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-desktop-edited-fixed.png" width="500" height="300">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-launchpad.png" width="500" height="300">
</p>

### Performing task on Ubuntu
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

ls, ls will list what file are in the directory you are working on
```
ls
```

cd, cd is the command to change the directory that you want to go to work
```
cd ~/Desktop
```

If you want to edit the script or text file, Ubuntu has provided us the default text editor which is called **gedit**, of course there are more text editors, some text editor gives more functionality for coding such [visual studio code](https://code.visualstudio.com/docs/setup/linux), [vim](https://www.vim.org/), [nano](https://linuxize.com/post/how-to-use-nano-text-editor/#:~:text=GNU%20nano%20is%20an%20easy,%2D8%20encoding%2C%20and%20more.) and more
```
gedit my_text_editor
```

sudo, sudo stands for superuser do, this command gives ability to be an administrator or root privileges, some files could not be directly used local, so the sudo comes into this position
```
sudo
```

example of sudo command, from the command below, you could see that the terminal will warn us about the permission to update file repository
```
apt update
```

to use this command properly, we need to append sudo in front of the command
```
sudo apt update
```

These are just the basic commands, if you would like to know more, here is the [link](https://www.hostinger.com/tutorials/linux-commands) to my recommend page to read about command on Linux

### Why Ubuntu on developing Robotics? :fire:
- lightweightness, ubuntu is lightweight in its nature, ypu don't have to pay to get access, you can install along side with your existing operating system, just donwload, install and use!
- the distribution of ubuntu is a long-term support (usually 5 years)
- tons of community support, ubuntu has a great community whenever you have a problem, you could get help such as [ubuntu community](https://ubuntu.com/community) or [stackoverflow](https://stackoverflow.com/) and more communities++ out there

## Basic robot operating system (ROS)

### What is ROS?
Robot operating system or ROS for short, ROS is an open-source framework for developing a robotics, ROS has a simple concept and easy to understand, ROS has a lot of communities, so many engineers and researchers use this framework to develop their own works.

### ROS concept

**ROS filesystem level**

ROS filesystem level is the part of the ROS that consider the filesystem on the disk, the filesystem level mainly consists of packages, metapackages and message type, service types
<p align="center">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/rosfilesystemlevel.png" width="600" height="300">
</p>

**ROS Computational graph**

asdasd
