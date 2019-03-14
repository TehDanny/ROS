# ROS Notes

## General Commands

Finding ROS

	printenv | grep ROS

## File system
Packages: Packages are the lowest level of ROS software organization. They can contain anything: libraries, tools, executables, etc.
Manifest: A manifest is a description of a package. Its most important role is to define dependencies between packages.
Stacks: Stacks are collections of packages that form a higher-level library.
Stack Manifest: These are just like normal manifests, but for stacks.

The build folder is the default location of the build space and is where cmake and make are called to configure and build your packages. The devel folder is the default location of the devel space, which is where your executables and libraries go before you install your packages.

### Commands

Finding packages and stacks

	rospack find [package_name]
	rosstack find [stack_name]

Change directory to package

	roscd [locationname[/subdir]]

List the files in a folder 

	rosls [locationname[/subdir]]

Create package

	roscreate-pkg [package_name]

Directly edit a file within a package

	rosed [package_name] [filename]

## Graphs
Nodes: A node is an executable that uses ROS to communicate with other nodes.
Messages: ROS data type used when subscribing or publishing to a topic.
Topics: Nodes can publish messages to a topic as well as subscribe to a topic to receive messages.
Master: Name service for ROS (i.e. helps nodes find each other)
rosout: ROS equivalent of stdout/stderr
roscore: Master + rosout + parameter server

Rosrun

	rosrun [package_name] [node_name]

## Topics

Show topic type

	rostopic type [topic]

Get topic info

	rostopic type /turtle1/cmd_vel | rosmsg show

## Services 
Services allow nodes to send a request and receive a response. 

	rosservice list         print information about active services
	rosservice call         call the service with the provided args
	rosservice type         print service type
	rosservice find         find services by service type
	rosservice uri          print service ROSRPC uri

## Messages and services

msg: Msg files are simple text files that describe the fields of a ROS message. They are used to generate source code for messages in different languages. Stored in directory of a package.
srv: An srv file describes a service. It is composed of two parts: a request and a response. Stored in the srv directory.

Show a message

	rosmsg show beginner_tutorials/Num

Copy a service from one package to another

	roscp [package_name] [file_to_copy_path] [copy_path]

Example:

	roscp rospy_tutorials AddTwoInts.srv srv/AddTwoInts.srv


## Bags
Record a topic and save the messages published to the topic in a bag.

	rosbag record
	rosbag record -a # records all topics

Read bagfile

	rosbag info <your bagfile>

Play bagfile

	rosbag play <your bagfile>

## Simulation

Run Rviz

	rosrun rviz rviz

Run Gazebo for ros

	source /opt/ros/%YOUR_ROS_DISTRO%/setup.bash
	roslaunch gazebo_ros empty_world.launch

Possible augments for the gazebo launch file are mentioned in empty_world.launch

	rosed gazebo_ros empty_world.launch

Gazebo API notes:
"The function approach would create a new public function that adjusts the velocity. For this to work, a new plugin would inherit from our current plugin. The child plugin would be instantiated by Gazebo instead of our current plugin, and would control the velocity by calling our function. This type of approach is most often used when interfacing Gazebo to ROS."
From http://gazebosim.org/tutorials?cat=guided_i&tut=guided_i5

## Source

	source ~/catkin_ws/devel/setup.bash 

Or when in the workspace directory:
	
	source devel/setup.bash 

## Links

rosws

	https://wiki.ros.org/rosws


catkin

	https://wiki.ros.org/catkin

## Unit tests

Run all tests

	cd ~/catkin_ws
	catkin_make run_tests

Run one test

	rostest [package_name] [test_launch_file]

## Error handling

Roswtf (Where's The Fire) diagnostic tool can find problems in ros configurations and ros applications

	roswtf
	roswtf myfile.launch

## Environment variables

ROS_ROOT sets the location where the ROS core packages are installed. 

	export ROS_ROOT=/home/user/ros/ros
	export PATH=$ROS_ROOT/bin:$PATH

ROS_MASTER_URI tells nodes where they can locate the master

	export ROS_MASTER_URI=http://mia:11311/

PYTHONPATH

	export PYTHONPATH=$PYTHONPATH:$ROS_ROOT/core/roslib/src


ROS_PACKAGE_PATH. It's possible to add multiple paths when seperating them with :

	export ROS_PACKAGE_PATH=/home/user/ros/ros-pkg:/another/path

## Misc

You can call a service with a remote procedure call.
You can publish a topic and subscribe to it. The publisher then sends messages to the topic and any subscribers of the topic receives said messages.
You can build a package with catkin_make, when entering the command in the workspace.
You can record a topic and save the messages published to the topic in a bag.

http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf
Conversion specifiers i bunden på side 289 og på nogle af de tidligere sider