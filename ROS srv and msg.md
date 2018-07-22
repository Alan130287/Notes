# ROS srv and msg

标签（空格分隔）： ROS

---

[TOC]

? The changes in files "CMakeLists.txt" and "Package.xml" after adding msgs and srvs file mean what?

## 添加了msg srv 文件后，的后续配置

### 添加了 msg 文件后
#### package.xml 中
```
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```
取消注释(uncomment)

#### CMakeLists.txt 中
```
# Do not just add this to your CMakeLists.txt, modify the existing text to add message_generation before the closing parenthesis
find_package(catkin REQUIRED COMPONENTS
   roscpp
   rospy
   std_msgs
   message_generation
)
```
加入 `message_generation`

---
```
catkin_package(
  ...
  CATKIN_DEPENDS message_runtime ...
  ...)
```
加入`CATKIN_DEPENDS message_runtime`

---
```
# add_message_files(
#   FILES
#   Message1.msg
#   Message2.msg
# )
```
改成
```
add_message_files(
  FILES
  [name].msg
)
```
[name]为添加的msg文件名

---
```
# generate_messages(
#   DEPENDENCIES
#   std_msgs
# )
```
取消注释

---

### 添加了srv文件后
#### package.xml 中
```
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```
取消注释(uncomment)

#### CMakeLists.txt 中
```
# Do not just add this to your CMakeLists.txt, modify the existing text to add message_generation before the closing parenthesis
find_package(catkin REQUIRED COMPONENTS
   roscpp
   rospy
   std_msgs
   message_generation
)
```
加入 `message_generation`

---

```
# add_service_files(
#   FILES
#   Service1.srv
#   Service2.srv
# )
```
改为
```
add_service_files(
  FILES
  [name].srv
)
```
其中[name]为srv文件名

### 最后一定要做
```
# generate_messages(
#   DEPENDENCIES
# #  std_msgs  # Or other packages containing msgs
# )
```
取消注释

---

在package所属的workspace里(e.g catkin_ws)，进行编译
```
cd [catkin_ws]
catkin_make install
```
这样做的目的:
Any .msg file in the msg directory will generate code for use in all supported languages. The C++ message header file will be generated in ~/catkin_ws/devel/include/beginner_tutorials/. The Python script will be created in ~/catkin_ws/devel/lib/python2.7/dist-packages/beginner_tutorials/msg. The lisp file appears in ~/catkin_ws/devel/share/common-lisp/ros/beginner_tutorials/msg/.

## 

有时间可以了解一下这样操作的原理