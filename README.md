# easy_baxter_simulation
Easy to use Baxter simulation for ROS kinetic

## Setup 
### Install Gazebo 7
```
$ sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
$ wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install libignition-math2
$ sudo apt-get install libignition-math2-dev
$ sudo apt-get install gazebo7 libgazebo7-dev
```
### Install all build tools and dependency for the Simulation
```
$ sudo apt-get -y install python-rosdep python-catkin-tools python-wstool  
$ cd /easy_baxter_simulation
$ rosdep install -y --from-paths . --ignore-src --rosdistro kinetic --as-root=apt:false
$ catkin config --extend /opt/ros/kinetic --cmake-args -DCMAKE_BUILD_TYPE=Release
$ catkin build
``` 
Catkin build might take a while but be patient, it will finishing building in a few minutes.

## Running the simulator
```
$ cd /easy_baxter_simulation
$ source devel/setup.bash
$ roslaunch baxter_gazebo baxter_world.launch
```

## Demos
Run the following demo to see if the simulation is running correctly   
In another terminal:  
```
$ cd /easy_baxter_simulation
$ source devel/setup.bash
$ rosrun baxter_examples joint_velocity_wobbler.py
```
You should be able to see the Baxter wobbles its arm.


## Credit
This is a simple version of Vicarious' simulator, where I pre-downloaded all the necessary files
[Vicarious AI's Kinetic Baxter Simulator]: https://github.com/vicariousinc/baxter_simulator