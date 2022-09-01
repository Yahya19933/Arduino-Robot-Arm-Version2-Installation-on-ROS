# Arduino-Robot-Arm-Version2-Installation-on-ROS
Installing and configuring arm version2 package robot on ROS

This repository will cover the steps taken to install a different version of the Arduino arm which is shown below. Unlike the previous Arm which was a complete a package and only required to install the package, this one was diffrent. This repistory is a continuation of the previous one and depends on it. To go to the previous arm installation [Arduino-Robot-Arm-Installation-on-ROS](https://github.com/Yahya19933/Arduino-Robot-Arm-Installation-on-ROS.git) 


## Installation
1. Download the required [3D modeling](https://drive.google.com/drive/folders/18E0vgwkuOhObBcaOVkfFNj-FnycijkbE) files (.stl)

There are 7 .stl files, The first 6 represent different parts of the Robot Arm with the the entire robot arm being the 7th. The 7th won't be used in this tutorial

2. Now the idea is that the Old Aruino Arm will be used as a base instead of starting from scratch. First things first backup the old Arm so that if anything goes wrong you can go back to the start
```
catkin_**workspace name** -> src -> arduni_robot_arm  
```
and copy the robot_arm_pkg file somewhere else

3. Then, go to 
```
catkin_**workspace name** -> src -> arduni_robot_arm - > robot_arm_pkg -> meshes - > stl 
```

4. Delete all the files then add the 6 .stl files downloaded from step 1

![stl files](https://user-images.githubusercontent.com/90250848/187870149-e5794ec5-6e5c-4a81-8ba7-f245bbdc7f33.png)

5. Then, go to 
```
catkin_**workspace name** -> src -> arduni_robot_arm - > robot_arm_pkg -> urdf 
```

6. Open the .urdf file using a txt editor and replace it's content with the following
[document.txt](https://github.com/Yahya19933/Arduino-Robot-Arm-Version2-Installation-on-ROS/blob/main/document.txt)



7.  Now you're done all that's left is to remake the catkin file and run Rviz. Open the cmd and input the following commands
```
cd catkin_*workspace name*
catkin_make
source /home/*user name*/catkin_*workspace name*/devel/setup.bash
roslaunch robot_arm_pkg check_motors.launch 
```
**Change the workspace name and user name tags accordingly**




8. And that's it you can now view the new robot Arm in Rviz and move it freely using the joint state publisher

![184207078-5555315a-32e9-4172-bcf1-5b197d8b566e](https://user-images.githubusercontent.com/90250848/187873160-00e5521b-2ebf-488d-8059-7c43680becc9.gif)




### Controlling the robot arm by joint_state_publisher
```
roslaunch robot_arm_pkg check_motors.launch
```

![184198154-84eb6f68-dd91-4a15-b24c-46516c4d699f](https://user-images.githubusercontent.com/90250848/187872907-22d69ef8-5e0e-4dc6-85d7-49a302861801.png)


You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```

## Controlling the robot arm by  gazebo
```
roslaunch robot_arm_pkg check_motors_gazebo.launch
```

![Screenshot from 2022-08-31 12-44-51](https://user-images.githubusercontent.com/90250848/187872961-8a218d25-cb4d-4486-b851-733dc3771e57.png)


You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```


## Controlling the robot arm by movelet
```
roslaunch moveit_pkg demo.launch
```

![Screenshot from 2022-08-31 12-48-57](https://user-images.githubusercontent.com/90250848/187873040-96342a79-1089-442a-bb83-d19bd8d3cee3.png)


You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```

