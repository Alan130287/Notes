# Kinect 和 turtlebot 

标签（空格分隔）： ROS Kinect Turtlebot





---

[TOC]

### ros初始化时,出错
 
> $ rosdep update
reading in sources list data from /etc/ros/rosdep/sources.list.d
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/python.yaml
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/ruby.yaml
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/releases/fuerte.yaml]:
	Failed to download target platform data for gbpdistro:
	<urlopen error [Errno 113] No route to host>
Query rosdistro index https://raw.githubusercontent.com/ros/rosdistro/master/index.yaml
Add distro "groovy"
Add distro "hydro"
Add distro "indigo"
Add distro "jade"
Add distro "kinetic"
Add distro "lunar"
Add distro "melodic"
updated cache in /home/agent/.ros/rosdep/sources.cache
ERROR: Not all sources were able to be updated.
[[[
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/releases/fuerte.yaml]:
	Failed to download target platform data for gbpdistro:
	<urlopen error [Errno 113] No route to host>
]]]

尝试关闭防火墙http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment

> $ sudo service iptables stop
[sudo] password for agent: 
Failed to stop iptables.service: Unit iptables.service not loaded.

防火墙根本就没开

把ros卸了重装就好，我也不知道为什么。`但是rosdep update 的报错可能是一个隐藏的问题`

---

### 打开kinect 
[参考](https://blog.csdn.net/huapiaoxiang21/article/details/73830913)
> roslaunch freenect_launch freenect.launch
rosrun rviz rviz
rostopic echo /camera/depth/points  # 检测数据流，有数据说明Kinect正常运行

修改“Fixed Frame”为/camera_rgb_color（`但是我没有这个选项`），接着点击add，选择camera类型。添加成功后选择camera菜单下的Iamge Topic选项，选择/camera/rgb/image_color。

![image.png-102.6kB][1]
 
---
### turtlebot

#### Python环境设置问题
在创建workplace时
> $ catkin_make 

报错，是因为Python环境问题，anaconda修改了默认Python版本，要把默认Python版本改成系统的Python版本，再安装其它没有装的包。

下载包的时候
> The following packages have unmet dependencies:
 ros-kinetic-turtlebot : Depends: ros-kinetic-turtlebot-bringup but it is not going to be installed
                         Depends: ros-kinetic-turtlebot-teleop but it is not going to be installed
 ros-kinetic-turtlebot-apps : Depends: ros-kinetic-turtlebot-actions but it is not going to be installed
                              Depends: ros-kinetic-turtlebot-calibration but it is not going to be installed
                              Depends: ros-kinetic-turtlebot-follower but it is not going to be installed
                              Depends: ros-kinetic-turtlebot-navigation but it is not going to be installed

老是出现类似问题，因为utc源比清华源快很多，下载源就改成了utc，但是清华源才能解决这个问题，改回了清华源下载速度又特别慢。




## (Without sogou pinyin) Uninstall 16.04 and install 14.04 for stable operation !!!

### No devices connected.... waiting for devices to be connected 包依赖问题
> sudo apt-get install package_name

改为
> sudo aptitude install package_name

第一个选项是no，剩下的是yes

## 然后我又把14.04LTS 通过系统升级到16.04LTS，网速的问题就解决了？？？！！！

> sudo gedit 

报错，[参考](http://www.ethicalhackx.com/fix-gtk-warning-cannot-open-display/)

> xhost +

就解决了


## 安装ros-kinetic 的包依赖错误
> dpkg: error processing package ros-kinetic-desktop-full (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 libopenni0
 libpcl-io1.7:amd64
 libpcl-visualization1.7:amd64
 libpcl1.7
 libopenni-sensor-pointclouds0
 ros-kinetic-pcl-conversions
 ros-kinetic-pcl-ros
 ros-kinetic-perception-pcl
 openni-utils
 libopenni-dev
 libpcl-dev
 ros-kinetic-perception
 ros-kinetic-desktop-full
 
 [参考](https://askubuntu.com/questions/779938/dependency-issue-after-upgrading-to-xenial)
 把相关的包都用 sudo apt-get purge * 清除，然后重新安装
 
 
 ## how to use anaconda and ros at the same time
 [reference](http://wiki.ros.org/IDEs)
 When Anaconda installs, it will create a path in your .bashrc file. (press ctrl + h in home directory to view file)

example:

> \# added by Anaconda x.x.x installer
export PATH="/home/"user"/"anaconda version"/bin:$PATH"

Having an active Anaconda path in your .bashrc will cause errors when you try to use ROS.

The solution to the problem is to comment out the path:

> \# export PATH="/home/"user"/"anaconda version"/bin:$PATH"

In order to use Anaconda, simply paste in the Anaconda path when you start a new terminal; and hit enter. Then use as normal. This will allow you to use ROS and Anaconda on the same system.

## kinect environment variable to sovle "No Device Connected" error after installing the kinect driver

add 
> export TURTLEBOT_3D_SENSOR=kinect

in ~/.bashrc 





 




  [1]: http://static.zybuluo.com/Counting/enyna3vu0t0q3nibq8g8ey48/image.png
  
  
  
  
  
