# Amber_B1
ROS package for Amber B1


# Guide
 First install ROS Noetic guide from here: http://wiki.ros.org/noetic/Installation/Ubuntu
 Create a workspace 
 
 ``source /opt/ros/noetic/setup.bash`` 
 
 ``mkdir -p ~/catkin_ws/src`` 
 
 ``cd ~/catkin_ws/``  
 ``catkin_make`` 
 
 
 Add amber_link 
 
 ``cd src`` 
 
 ``git clone https://github.com/shnx/Amber_B1.git``
 
 ``cd..`` 
 
 ``catkin_make``  
 
Create the ros1_bridge workspace. We build the bridge in a separate workspace because it needs to see both ROS1 and ROS2 packages in its environment and we want to make sure our application workspaces only see the packages from the distribution they are in.

``mkdir -p ~/ros1_bridge_ws/src``

``cd ~/ros1_bridge_ws/src``

``git clone -b dashing https://github.com/ros2/ros1_bridge.git``

``. ~/catkin_ws/devel/setup.bash``

``. ~/colcon_ws/install/setup.bash``

``echo $CMAKE_PREFIX_PATH | tr ':' '\n'``

``colcon build --packages-select ros1_bridge --cmake-force-configure --cmake-args -DBUILD_TESTING=FALSE``

``source install/local_setup.bash``

``ros2 run ros1_bridge dynamic_bridge --print-pairs``

