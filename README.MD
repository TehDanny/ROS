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

Keywords: roscore, rosnode, and rosrun

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

msg: msg files are simple text files that describe the fields of a ROS message. They are used to generate source code for messages in different languages. Stored in directory of a package.
srv: an srv file describes a service. It is composed of two parts: a request and a response. Stored in the srv directory.

Show a message

	rosmsg show beginner_tutorials/Num

Copy a service from one package to another

	roscp [package_name] [file_to_copy_path] [copy_path]

Example:

	roscp rospy_tutorials AddTwoInts.srv srv/AddTwoInts.srv

## Source

	daniel@daniel-Lenovo-Z50-75:~$ source catkin_ws/devel/setup.bash 
	daniel@daniel-Lenovo-Z50-75:~$ roscd beginner_tutorials/
	daniel@daniel-Lenovo-Z50-75:~/catkin_ws/src/beginner_tutorials$

## Links

rosws

	https://wiki.ros.org/rosws


catkin

	https://wiki.ros.org/catkin