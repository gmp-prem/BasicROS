# ROS Tutorial
> Tutorial for beginner who wants to start using ROS on Ubuntu

## Topics
1. Getting started with Linux
   - What is a Linux?
   - Ubuntu interface
   - Performing task on Ubuntu
   - Basic commands
3. Basic robot operating system (ROS)
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
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-desktop-edited.png" width="500" height="300">
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/ubuntu-launchpad.png" width="500" height="300">
</p>

**File system level on ubuntu**

it is very important to understand the file system level on Ubuntu since you are going to work with it, many times you will use the terminal to access and manipulate your files, the picture shown below is the main file system level of Ubuntu that you should know

INSERT FILE SYSTEM LEVEL IMAGE

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
  <img src="https://github.com/gmp-prem/BasicROS/blob/main/Images/teminal_with_command.png" width="500" height="300">
</p>

You can see that on the terminal there is a `prem@prem:~$`

`prem` is the username indicated before @ symbol

`prem` is the hostname indicated after @ symbol

`~` is the directory you are working on

`$` is prompt symbol, this symbol will just tell where the command you type will begin

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

to use this command properly, we need to append sudo infront of the command
```
sudo apt update
```

### Why Ubuntu on developing Robotics? :fire:
- lightweightness, ubuntu is lightweight in its nature, ypu don't have to pay to get access, you can install along side with your existing operating system, just donwload, install and use!
- the distribution of ubuntu is a long-term support (usually 5 years)
- tons of community support, ubuntu has a great community whenever you have a problem, you could get help such as [ubuntu community](https://ubuntu.com/community) or [stackoverflow](https://stackoverflow.com/) and more communities++ out there

