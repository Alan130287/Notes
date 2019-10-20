# Turtlebot Gazebo Navigation

标签（空格分隔）：ROS Turtlebot 

---

[TOC]

### 1. Launch Gazebo

> roslaunch turtlebot_gazebo turtlebot_world.launch

or launch your own world

> roslaunch turtlebot_gazebo turtlebot_world.launch world_file:=<full path to the world file>

### 2. Run navigation demo
I guess it serves as the global map and local map creator and execute the navigation funtion.

> roslaunch turtlebot_gazebo amcl_demo.launch

or the world you want to load the map you have created.

> roslaunch turtlebot_gazebo amcl_demo.launch map_file:=<full path to map yaml file>

### 3. Launch Rviz for visualization

> roslaunch turtlebot_rviz_launchers view_navigation.launch

### 4. Run the python script



### 5. Take photo 

> rosrun image_view image_view image:=/camera

Right click at the window can save the picture in the current path. But in my computer, the window will be hang and turn to black. Saw the solution [here](https://github.com/ros-perception/image_pipeline/issues/235) but I won't to do it. 

### 6. Using Python Script to Take Photo

> agent@vcchzhpc14:~/turtlebot_simple_py_code$ python take_photo.py 


> Warning! You should run the python script in the path where the take_photo.py is, or the photo taken will not appear in correct position.

#### Details
The line 
```
img_title = rospy.get_param('~image_title', 'photo.jpg')
```
means to get the parameters of `image_title`.(Because it is a private parameter in `take_photo` node, a `~` must add in front of it.)
If the parameter of `image_title` has not been setted. Return `photo.jpg` as default value.

If launch 

> python take_photo.py _image_title:="new_title.jpg"

the parameter will be setted.(`how does it work?`)

You can see it by launching

> rosparam get /take_photo/image_title

You can delete it by launching

> rosparam delete /take_photo/image_title

A testing Script:
```
import rospy


rospy.init_node('test', anonymous=False)
img_title = rospy.get_param('~everything', 'default')
print(img_title)
```
![image.png-12.3kB][1]

### 7. Record A Video

With all the environment settled, in the path where you want to store the video, launch

> rosrun image_view image_view image:=/camera/rgb/image_raw

It will start recording video, and you can press `Ctrl+C` to stop recording.

### 


 


  [1]: http://static.zybuluo.com/Counting/ru8uyecoaru24rba239hrl9o/image.png