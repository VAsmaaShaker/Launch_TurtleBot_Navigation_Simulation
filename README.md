# Launch_TurtleBot_Navigation_Simulation
Launched TurtleBot3 simulation in Gazebo, SLAM, and navigation using ROS Noetic.

I followed the instructions via this link (just copy and paste):[turtlebot3.](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/)

## Step 0: Install ROS on Remote PC.
 ```
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
$ chmod 755 ./install_ros_kinetic.sh 
$ bash ./install_ros_kinetic.sh
 ```
![image](https://github.com/user-attachments/assets/6e084ec9-ef0d-4520-b082-33cf3242a641)

## Step 1: Install Dependencies.
copy and paste this command:
 ```
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
ros-noetic-rosserial-python ros-noetic-rosserial-client \
ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers

 ```
## Step 2: Install TurtleBot3 Packages
copy and paste this command:
 ```
$ sudo apt install ros-noetic-dynamixel-sdk
 ```
 ```
$ sudo apt install ros-noetic-turtlebot3-msgs
 ```
 ```
$ sudo apt install ros-noetic-turtlebot3
 ```
## Step 3: Install Simulation Package
Open a terminal and navigate to the src directory of your Catkin workspace, then copy and paste this command:
 ```
$ cd ~/catkin_ws/src/
$ git clone -b kinetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
 ```

## Step 4: Launch Simulation World
### 1. Gazebo 

**Three simulation environments are prepared for TurtleBot3. Please select one of these environments to launch Gazebo.**

1. Empty World

2. TurtleBot3 World

3. TurtleBot3 House

I have chosen the second option, which is TurtleBot3 World, so I will run this command.

 ```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
 ```
![image](https://github.com/user-attachments/assets/5c7fae41-ebc9-4412-b638-a35fe28f2fe5)

----------------------------------------------------------------------------------------
### 2. SLAM 

 ```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
 ```
![image](https://github.com/user-attachments/assets/f6fbee91-bc2e-48dd-abd4-92dd2ae5d207)

Next, navigate to generate a map and save it using this command:
 ```
$ rosrun map_server map_saver -f ~/map
 ```
To control, copy and paste this command: 
 ```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
``` 
![image](https://github.com/user-attachments/assets/31b21854-8bb0-44eb-aacd-26a9b198bb08)


----------------------------------------------------------------------------------------

### 3. Navigation 
**Note: launch the TurtleBot3 navigation with the saved map.**
```
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:='/home/vasmaa/map.yaml'
 ```
![image](https://github.com/user-attachments/assets/34ed0745-3ef8-497f-bc36-25a5af6f69e7)

