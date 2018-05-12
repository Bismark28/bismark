# Turtlebot_arm project

## Introduction

### Explanation about the complete project

The project for the class is about implementing a **scenario** where two robots that is the **turtlebot** and **PhantomX Pincher Arm** will work together to perform a particular task. We have the turtlebot arm standing on a table at the **load** and the turtlebot on the other hand will be a distance away from the Pincher arm that is the **drop** area. 
The turtlebot needs to navigate its way to the **load** area where the arm is, then the arm **Picks** a cube from the table with its **gripper** after it has received a command and **place** it on top of the turtlebot. After the placing is done, the turtlebot then needs to navigat its way to the the **drop** area. The setup looks like this:

![alt setup of project](https://i.ytimg.com/vi/jgKtQxnRqao/maxresdefault.jpg)

## About this repository

This repository contains all the packages and the codes needed to allow the turtlebot arm PhantomX Pincher to perform its task properly: That is picking a cube from the table and placing the cube. We will use the arbotix driver to bring up the Pincher arm to make the arm subscribe to any velocity topic it will be commanded to perform.


## Contents of this readMe file

This readMe file includes explanations of the following:

* Codes used for the Pincher arm.
* brief explanations of the codes.
* Caliberations of the arm to make sure it was working properly using arbotix gui
* Path planning simulation
* Path planning with real arm
* Running and testing my code.
* changing the parameters of my code to make sure it was working up to its task.
* Results obtained.
* Problems encountered.
* Suggested improvements
* Conclusion.
* References.


## Codes for the Pincher arm

* turtlebot_arm_bringup

* turtlebot_arm_description

* turtlebot_arm_moveit_config

* turtlebot_arm_moveit_demos




## Brief explanations of the codes

### turtlebot_arm_bringup

This folder includes the important configutation files that make the turtlebot arm work effectively

### turtlebot_arm_description

This folder contains files that ensures that there is a virtual model of our robots

### turtlebot_arm_moveit_config

This folder contains the codes that are necessary for the turtlebot arm to move

### turtlebot_arm_moveit_demos

This folder contains a demonstration that we can run when we want to test how the arm moves.


## Caliberations of the arm to make sure it was working properly using arbotix gui

In order to be sure the turtlebot arm is working effectively, we caliberate it using the arbotix gui launching arbotix_python arbotix_gui. 
During the caliberations, we try to manipulate all the five servos of turtlebot arm that is the ***arm_elbow_flex, arm_shoulder_lift, arm_shoulder_pan, arm_wrist_flex and the gripper.***


![alt setup of project](https://alliance.seas.upenn.edu/~cis700ii/dynamic/team4/wp-content/uploads/sites/6/2015/11/arbGui.png)



## Path planning simulation

Path simulation helped to know how the turtlebot arm works virtually and also helped us to plan on how we want the turtlebot to work. This is launched by using roslunch **turtlebot_arm_moveit_demos** 


![alt setup of project](https://github.com/Bismark28/bismark/blob/master/Screenshot%20from%202018-05-09%2010:19:06.png)

## Path planning with real arm

After planning the movement of the turtlebot using simulation, we then compared the real arm to the simulation and check if it works as expected. in planning with the real arm, we used the lauch file. That is the pick and place.


![alt setup of project](https://github.com/Bismark28/bismark/blob/master/20180508_162039.jpg)


## Running and testing my code.

my codes are in my repository but some of the necessary codes in my project would be shown here.
The necessary codes operate on the gripper and the motors of the servos of turtlebot arm. These codes help the turtlebot arm to be able to caliberate well to pick a cube and place it on the turtlebot. 


 ~~~python code
 
  table_pose = PoseStamped()ffe
        table_pose.header.frame_id = REFERENCE_FRAME
        table_pose.pose.position.x = 0.36
        table_pose.pose.position.y = 0.0
        table_pose.pose.position.z = (table_ground + table_size[2] / 2.0)-0.081
table_pose.pose.orientation.w = 1.0
~~~

This code helps to adjust the table pose position with respect to the turtlebot arm. it helps the turtlebort arm's gripper to be able to reach on the surface of the table where the cube is placed and picks it.


After turtlebot arm has been able to reach on the surface of the table, the gripper has to pick the cube and place it on the turtlebot. The gripper can be able to pick the cube effectively only by adjusting the length, width and height of the cube with respect to the gripper.


### The dimension of the target box

~~~python code
  target_size = [0.05, 0.015, 0.03]
~~~


## Changing the parameters of my code to make sure it was working up to its task.

The scripts used for the operation of the turtlebot arm is a python script. By default, the parameters do not work up to expectation like caliberating the turtlebot servos down to the surface of the table and making the grippers open and pick the cube and place the cube on the turtlebot. I will say this default code was to help us test our caliberations. You can open a new file with your new parameters that will make the turtlebot arm work effectively by being able to caliberate to the surface of the table, pick the cube and place it on the turtlebot.

some of the parameters i changed was:

#### default parameter

~~~python code
 # Set the target size [l, w, h]
target_size = [0.02, 0.005, 0.12]

~~~

#### new parameter

~~~python code
# Set the target size [l, w, h]
        target_size = [0.05, 0.015, 0.03]
~~~

#### default parameter

~~~python code
 # Add a table top and two boxes to the scene
        table_pose = PoseStamped()
        table_pose.header.frame_id = REFERENCE_FRAME
        table_pose.pose.position.x = 0.36
        table_pose.pose.position.y = 0.0
        table_pose.pose.position.z = table_ground + table_size[2] / 2.0
        table_pose.pose.orientation.w = 1.0
        scene.add_box(table_id, table_pose, table_size)
~~~

#### new parameter

~~~python code
 # Add a table top and two boxes to the scene
        table_pose = PoseStamped()
        table_pose.header.frame_id = REFERENCE_FRAME
        table_pose.pose.position.x = 0.36
        table_pose.pose.position.y = 0.0
        table_pose.pose.position.z = (table_ground + table_size[2] / 2.0)-0.081
        table_pose.pose.orientation.w = 1.0
        #scene.add_box(table_id, table_pose, table_size)

~~~


## Results obtained.

We obtained a very nice and successful results that can be seen in the video below:

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/6IrjdGcrWH8/0.jpg)](http://www.youtube.com/watch?v=6IrjdGcrWH8)




## Problems encountered.

During the course of the project work, we encountered so many problems. Talking about the turtlebot arm:

* After installing all the packages needed for the turtlebot arm to caliberate, the turtlebot arm was working perfect in the beginning with the default parameters but after i started manipulating the parameters so that the arm can be able to perform its task thus picking cube and placing, the arm started giving problems of getting stucked sometimes during caliberations. At a point in time, some of the servos was affected so i taught the problem was from the arm. To overcome this problem, i tried to manipulate the codes and also had to unplug the arm, adjust the it to a good state and then lauch it again.

* After manipulating the codes and being able to caliberate the turtlebot arm to pick the cube, i encountered problems because after the turtlebot arm picked the pick cube from the table, it gets stucked when trying to place the cube on the turtlebot. To overcome this problem, i realised that the cube was bigger than the gripper so even though the gripper was able to pick it, it was not able to place it. so i changed the width of the cube with respect to the gripper in my code which was able to widen the gripper according to the cube's width and it worked successfuly.


## Suggested improvements

There are many improvements that could be made to this project such as:

***Both pincher arm and turtlebot having the same lauch file:*** In our project, the turtlebot and the pincher arm have different launch files so first, we lauch the turtlebot to navigate to the pincher arm then we lauch the Pincher arm to pick the cube and place it on the turtlebot. i suggest both the Pincher arm and the turtlebot have same lauch file so that the moment we launch the file, all the operations would be done successfully.

***The gripper of the arm should not be able to pick the cube at all when the its width is smaller than the cube:*** During the project, the turtlebot arm got stucked after picking the cube because the width of the space between the gripper was smaller than the cube. this made me think it was a problem with the Pincher arm but until i modified my code. i suggest the gripper should not be pick the cube at all to in order to create full awareness that the problem comes from the codes and therefore need to be modified.

## Conclusion

In this project, we were able to implement the expected scenario where the ***turtlebot*** navigates from the drop area towards the ***PhantomX pincher arm*** at the load area, and the Pincher arm picks the cube from the table and place it on top of the turtlebot then the turtlebot returns the cube its destination.


## References

* ROS official website
* Turtlebot Arm PhatomX Pincher with ROS
* Youtube



