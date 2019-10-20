# Turtlebot 远程操作流程

标签（空格分隔）： ROS Turtlebot Kinect

---

1. 分别在主机和turtlebot上的笔记本的~/.bashrc 文件做如下修改
 * 主机：
>export ROS_MASTER_URI=http://IP_OF_TURTLEBOT:11311
export ROS_HOSTNAME=IP_OF_PC
 * turtlebot上的笔记本

>export ROS_MASTER_URI=http://localhost:11311
export ROS_HOSTNAME=IP_OF_TURTLEBOT

> 注意，就算已经修改过了，ip地址任可能改变，所以每次操作都要进行修改。当不需要远程操作的时候，要把主机的上述参数注释掉。


2. 在主机上通过ssh登陆turtlebot(就是turtlebot上的笔记本，之后提及的turtlebot操作都默认为主机ssh登陆下的操作，下同)
 * 在turtlebot笔记本上启动turtlebot，并打开导航包。这里打开的是1023房间的全局地图。
> roslaunch turtlebot_bringup minimal.launch
roslaunch turtlebot_navigation amcl_demo.launch map_file:=/map/1023.yaml

 * (选用)在turtlebot笔记本上启动键盘操控界面，可以用键盘操控turtlebot
>  roslaunch turtlebot_teleop keyboard_teleop.launch

在主机
* 打开navigator
> roslaunch turtlebot_rviz_launchers view_navigation.launch

在这个界面可以看到turtlebot位置和地图，大的是全局地图(globalmap，也就是加载的1023.yaml文件)，turtlebot周围的正方形是局部地图(localmap，由kinect感知)。
* 就可以可以运行下面部分的pyhton文件
https://github.com/markwsilliman/turtlebot






 

 



