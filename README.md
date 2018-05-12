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
During the caliberations, we try to manipulate all the five servos of turtlebot arm that is the ***arm_shoulder_flex, arm_shoulder_lift, arm_shoulder_pan, arm_wrist_flex and the gripper.***


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




