# Object Detection and Recognition with kinect

标签（空格分隔）： Detection Recognition Kinect

---

[TOC]

## 2d Using Kinect

### Install find_object_2d

> sudo apt-get install ros-kinetic-find-object-2d

Then `git clone https://github.com/introlab/find-object.git` in src.

### Open kinect

> roslaunch freenect_launch freenect.launch depth_registration:=true

### Start Detection

>roslaunch find_object_2d find_object_3d.launch

add the object and it will start detection.
![kinect_detection.png-571.5kB][1]

Get the position of object.
>rosrun find_object_2d print_objects_detected

![image.png-62.5kB][2]

Check the `/objects` topic can get more information.
>rostopic echo /objects

![image.png-48.2kB][3]

The data includes [object id, Width, Height, 3x3 homography matrix`?`].

Using rviz can visualize the distance information.
![rviz_detection.png-172kB][4]

## 3d Detection

### Main Steps
1. Building a CAD(Computer Aided Design) model of the object or capturing its 3D model
2. Training the model
3. Detecting the object using the trained model

### Training using 3D models of an object
add an entry to the object database 
>agent@vcchzhpc14:~/ros_project_dependencies_ws/src/ork_tutorials$ rosrun object_recognition_core object_add.py -n "coke" -d "A universal coke" --commit

output is 
>Stored new object with id: 929c0287a015e9f0a0665eb45600032b

upload the mesh file of the object to the created entry(notice the change in dir):
>agent@vcchzhpc14:~/ros_project_dependencies_ws/src/ork_tutorials/data$ rosrun object_recognition_core mesh_add.py 929c0287a015e9f0a0665eb45600032b coke.stl --commit

output is
>updating model: 929c0287a015e9f0a0665eb45600115d
Stored mesh for object id : 929c0287a015e9f0a0665eb45600032b

upload the model:
install `couchapp`. The object recognition package uses `couchdb` as the database. So we need the following application to view the model from the database.
> sudo pip install git+https://github.com/couchapp/couchapp.git

then push the commit`?`
>rosrun object_recognition_core push.sh

![image.png-26.4kB][5]

![image.png-32kB][6]


![image.png-54.7kB][7]

To train the model:
first find the path of `object_recognition_linemod`
>rospack find object_recognition_linemod

then train it
>rosrun object_recognition_core training -c [the path you get]/conf/training.ork

### Training from Captured 3D models

> roscore

> roslaunch freenect_launch freenect.launch

set parameteres for the Kinect ROS driver:
> rosrun dynamic_reconfigure dynparam set /camera/driver depth_registration True
rosrun dynamic_reconfigure dynparam set /camera/driver image_mode 2
rosrun dynamic_reconfigure dynparam set /camera/driver depth_mode 2

The `topic_tools relay` parameter basically subsribes to the first topic and republished it in another name
> rosrun topic_tools relay /camera/depth_registered/image_raw /camera/depth/image_raw
> rosrun topic_tools relay /camera/rgb/image_rect_color /camera/rgb/image_raw

what it does
![image.png-13.2kB][8]
![image.png-28.5kB][9]

To build the object:
> rosrun object_recognition_capture capture --seg_z_min 0.01 -o object.bag

`An error occur`:
>Registration? 1
Sync? 0
python: /usr/include/boost/smart_ptr/shared_ptr.hpp:641: typename boost::detail::sp_dereference<T>::type boost::shared_ptr<T>::operator*() const [with T = xn::NodeInfo; typename boost::detail::sp_dereference<T>::type = xn::NodeInfo&]: Assertion `px != 0' failed.
Aborted (core dumped)

I can't solve it, and no solution found in google.

### Recognizing Object
>roscore
roslaunch freenect_launch freenect.launch
rosrun dynamic_reconfigure dynparam set /camera/driver depth_registration True 
rosrun dynamic_reconfigure dynparam set /camera/driver image_mode 2 
rosrun dynamic_reconfigure dynparam set /camera/driver depth_mode 2

>rosrun topic_tools relay /camera/depth_registered/image_raw /camera/depth/image_raw 
rosrun topic_tools relay /camera/rgb/image_rect_color /camera/rgb/image_raw

![coke_detection.png-140kB][10]
![image.png-45.4kB][11]

Notice the parameters in the left side board.
![image.png-39.3kB][12]

Nodes Graph
![rosgraph.png-770.5kB][13]


  [1]: http://static.zybuluo.com/Counting/nt4ye7q168iiox01zevw6wwa/kinect_detection.png
  [2]: http://static.zybuluo.com/Counting/belbq3pf5x0j7kpfohc43fkl/image.png
  [3]: http://static.zybuluo.com/Counting/uoc744n9d7he3x7zvw0pkmmf/image.png
  [4]: http://static.zybuluo.com/Counting/chs4cl4i957njpq2ugty880x/rviz_detection.png
  [5]: http://static.zybuluo.com/Counting/2ttyky7nqndo0zb3eglkfjyg/image.png
  [6]: http://static.zybuluo.com/Counting/0w9qxc2ljs3bovdxippcs2og/image.png
  [7]: http://static.zybuluo.com/Counting/0cd5s39gtvpq4qkk5c5qhokr/image.png
  [8]: http://static.zybuluo.com/Counting/zyc1hh7lxx4yj7ogfbprggmp/image.png
  [9]: http://static.zybuluo.com/Counting/i9i6sltw6vbosb8uhvsc9q3z/image.png
  [10]: http://static.zybuluo.com/Counting/5q0ycs1gf4i2gwmywh5z83es/coke_detection.png
  [11]: http://static.zybuluo.com/Counting/xf3r8mhjv57ujob94lpd6qe7/image.png
  [12]: http://static.zybuluo.com/Counting/yggxh9g61ppf08w7x0cnjqn9/image.png
  [13]: http://static.zybuluo.com/Counting/phvz7aqydfh4r2a3oi3e20oe/rosgraph.png