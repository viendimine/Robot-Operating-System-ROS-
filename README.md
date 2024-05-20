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
## Important:
* suppose you are using different wifi-networks at different time , so don't get stuck off, you will get error while using 'roscore' because different wifi will have different ip address so to ensure you are communicating with correct ip follow below commands.
```
ifconfig
```
you will get something like this.
```
enp3s0 Link encap:Ethernet HWaddr d8:cb:8a:f1:74:2b
 inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
 inet6 addr: fe80::60fc:7e2b:b877:f82b/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:52 errors:0 dropped:0 overruns:0 frame:0
 TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:10172 (10.1 KB) TX bytes:8917 (8.9 KB)
 Interrupt:19
lo Link encap:Local Loopback
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:65536 Metric:1
 RX packets:3520 errors:0 dropped:0 overruns:0 frame:0
 TX packets:3520 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1
 RX bytes:560728 (560.7 KB) TX bytes:560728 (560.7 KB)
wlp2s0 Link encap:Ethernet HWaddr 08:d4:0c:80:c5:00
 inet addr:192.168.11.19 Bcast:192.168.11.255 Mask:255.255.255.0
 inet6 addr: fe80::a60b:e157:4157:d9dc/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:675821 errors:0 dropped:0 overruns:0 frame:0
 TX packets:219992 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:919561165 (919.5 MB) TX bytes:46928931 (46.9 MB)
```
Here inet addr will be your ip address, So copy it or remember it.
then .
```
export ROS_MASTER_URI=http://ip_address:11311
export ROS_HOSTNAME=ip_address
```
or
```
export ROS_MASTER_URI=http://ip_address:11311
export ROS_IP=ip_address
```
Now , you can communicate with connected wifi network and ros master ,also keep in mind above command works only for single terminal session , for different sessions you have to write again this command.
