# ROS Notes

## General Commands

Finding ROS

	printenv | grep ROS

## File system
Packages: Packages are the lowest level of ROS software organization. They can contain anything: libraries, tools, executables, etc.
Manifest: A manifest is a description of a package. Its most important role is to define dependencies between packages.
Stacks: Stacks are collections of packages that form a higher-level library.
Stack Manifest: These are just like normal manifests, but for stacks.

### Commands

Finding packages and stacks

	rospack find [package_name]
	rosstack find [stack_name]

Change directory to package

	roscd [locationname[/subdir]]

List the files in a folder 

	rosls [locationname[/subdir]]

## Links

rosws

	https://wiki.ros.org/rosws


catkin

	https://wiki.ros.org/catkin