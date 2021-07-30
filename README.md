Universal Robot UR3/UR3e
===
<img src="https://github.com/cambel/ur3/blob/master/wiki/ur3e.gif?raw=true" alt="UR3e & Robotiq Hand-e" width="250"><img src="https://github.com/cambel/ur3/blob/master/wiki/ur3.gif?raw=true" alt="UR3 & Robotiq 85" width="250">


Custom ROS packages for the UR3 Robot with a gripper Robotiq 85 and the UR3e robot with a gripper Robotiq Hand-e. 
Tested on ROS Noetic Ubuntu 20.04 with Python 3.6.

## Installation 

### [With docker](https://github.com/cambel/ur3/wiki/Install-with-Docker)

### [Compile from source](https://github.com/cambel/ur3/wiki/Compile-from-source-(This-repo))

## Examples

### Visualization of UR3 in RViz

To visualize the model of the robot with a gripper, launch the following:
  ```
  $ roslaunch ur3_description display_with_gripper.launch
  ```
You can then use the sliders to change the joint values and the gripper values.

### Simulation in Gazebo 7/9
<img src="https://github.com/cambel/ur3/blob/master/wiki/ur3-e.png?raw=true" width="500">
<!-- ![ur3/ur3e gazebo simulator](https://github.com/cambel/ur3/blob/master/wiki/ur3-e.png?raw=true) -->

To simulate the robot launch the following:
  ```
  $ roslaunch ur3_gazebo ur3_cubes.launch grasp_plugin:=1
  ```
or using ur3e:
  ```
  $ roslaunch ur3_gazebo ur3e_cubes.launch grasp_plugin:=1
  ```

By default the simulation starts paused. Unpause the simulation. You can then send commands to the
joints or to the gripper.

An example of sending joints values to the robot can be executed as follows:
  ```
  $ rosrun ur_control sim_controller_examples.py -m
  ```
To change the values of the joints, the file `sim_controller_examples.py` must be modified.

Similarly, the script include examples to control the robot's end-effector position, gripper and an example of performing grasping.
Execute the following command to see the available examples.
  ```
  $ rosrun ur_control sim_controller_examples.py --help
  ```

An easy way to control the robot using the keyboard can be found in the script:
  ```
  $ rosrun ur_control joint_position_keyboard.py
  ```
Press SPACE to get a list of all valid commands to control either each independent joint or the end effector position x,y,z and rotations.
To have access to the gripper controller include the option `--gripper`

Another option of easy control is using `rqt`

## MoveIt
To test the MoveIt configuration with the UR3/UR3e start one of the gazebo environments, such as:
```
roslaunch ur3_gazebo ur3e_cubes.launch
```

Then load the MoveIt configuration
```
roslaunch ur3e_hande_moveit_config start_moveit.launch
```

Then execute the tutorial
```
rosrun ur_control moveit_tutorial.py --tutorial
```
