# Robot Operating System (ROS)
* Follow this step by step for full process in detail.
## Installation guide

### Install ROS Kinetic on PC
* First, Install Linux(Ubuntu 18.04 , Ubuntu 20.04(recommended) or Linux mint) on your PC.
* Next, in order to develop source code from the remote PC, refer to the commands below.
* Open the terminal window on your PC by clicking on icon .Also ,Shortcut key for terminal is Ctrl-Alt-T.
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh
```
### Install ROS Kinetic on Rasberry Pi
* First, install Linux (Ubuntu MATE) on your Raspberry Pi.
* Next, in order to develop source code from the remote PC, refer to the commands below.
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic_rp3.sh && chmod 755 ./install_ros_kinetic_rp3.sh && bash ./install_ros_kinetic_rp3.sh
```
#### Initializing rosdep
* Be sure to initialize rosdep before using ROS. The rosdep is a feature that enhances user
convenience by easily installing dependent packages when using or compiling core components
of ROS.
```
$ sudo rosdep init
$ rosdep update
```
#### Installing package
* To install any ros package refer below command.
```
$  sudo apt-get install ros-kinetic-[NAME_OF_PACKAGE]
```
#### Installing rosinstall
* This program installs various packages of ROS. Be sure to install this useful tool that is frequently
used.
```
$ sudo apt-get install python-rosinstall
```
#### Loading Environment File
* This command imports the environment setting file. Environment variables such as ROS_ROOT,
ROS_PACKAGE_PATH, etc. are defined.
```
$ source /opt/ros/kinetic/setup.bash
```
### Creating and Initializing a Workspace Folder
* ROS uses a ROS dedicated build system called catkin. To use this, you need to create and initialize
a catkin workspace folder as follows. This configuration only needs to be performed once,
unless you create a new workspace folder.
```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
```
* Now that we have created the catkin workspace folder, let’s build it. Currently, the catkin
workspace only contains the ‘src’ folder and the ‘CMakeLists.txt’ file inside, but as a test use the
‘catkin_make’ command to build.
```
$ cd ~/catkin_ws/
$ catkin_make
```
* Lastly, we will import the setting file associated with the catkin build system.
```
$ source ~/catkin_ws/devel/setup.bash
```
### Testing
* The installation for ROS has been completed. The following command will verify whether the
installation was successful or not. Close all terminal windows and open a new terminal window.
Now enter the following command to run roscore.
```
$ roscore
```
If it runs like the following without errors, the installation is completed. Terminate the
process with [Ctrl+c].
```
... logging to /home/pyo/.ros/log/9e24585a-60c8-11e7-b113-08d40c80c500/roslaunch-pyo-5207.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.
started roslaunch server http://localhost:38345/
ros_comm version 1.12.7
SUMMARY
========
PARAMETERS
 * /rosdistro: kinetic
 * /rosversion: 1.12.7
NODES
auto-starting new master
process[master]: started with pid [5218]
ROS_MASTER_URI=http://localhost:11311/
setting /run_id to 9e24585a-60c8-11e7-b113-08d40c80c500
process[rosout-1]: started with pid [5231]
started core service [/rosout]
```
