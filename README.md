# MapMyWorld_Jupiter2.0
This project is part of the Udacity Nanodegree program for Robotics Engineering. It uses the rtabmap package to map an environment using data from cameras, and lasers. RTAB-map is based on loop closures, which help the robot decide whether it has seen certain features of an area before. As the robot travels through its environment, the camera pulls in images and compares those images to those previously stored, to see if the features are similar.

RTAB SLAM stands for real-time appearance based SLAM, another method for localization and mapping in robotics. The robot receives data from visual and odometry readings. For this project, my robot was using laser scan and an rgb cambera for visuals. Information from sensors is then passed into short term memory as nodes. While in short term memory (STM) nodes are given weights based on the time a robot has spent in a certain area. If an node has a similar weight to the one next to it, then the weight of the original node is increased by one, and a new node will not be created. 

Nodes/images are eventually moved into working memory (WM) where they can be used for loop closure. Images are compared, and older images can be moved to long term memory (LTM) if they are not being used. This means that RTAB is more memory efficient than some other mapping programs. If the robot is in a large environment or one with a lot of features, that could result in a lot of data that needs to be reviewed and processed. With RTAB-SLAM, constraints are placed on different memory buckets to prevent overload. Additionally if an item has been moved to LTM and the robot discovers a possible loop closure with additional images/nodes, the original node can be called back to WM through retrieval. Generally WM will contain nodes that have been seen for longer periods of time. 

This project builds on two previous projects in which I designed and built the wheeled robot Jupiter, and a sample apartment for him to move around in. He has been outfitted with an rgb camera as previously mentioned. This was done by making edits to his URDF file, which is located in the URDF folder. An additional launch file was created called mapping.launch to include the nodes and parameters for launching and using RTAB-MAP. 

Additional info can be found here: http://wiki.ros.org/rtabmap_ros

Note: For this project I actually cloned the teleop_twist_keyboard package for ROS in order to move my robot. If you clone this project, you may not be able to pull that package down because it is housed inside the catkin_ws folder. To clone it to your own repo, see here: https://github.com/ros-teleop/teleop_twist_keyboard
