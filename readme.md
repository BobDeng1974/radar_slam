## radar_slam:
Implementation of SLAM using automotive radars. Currently under development.

### ROS	Dependencies:

As always, running:

```bash
rosdep install --from-paths src --ignore-src --rosdistro=ROSDISTRO -y
```

with ```ROSDISTRO``` set to ```kinetic```, ```melodic``` etc. This should install all ROS dependencies, including:

PCL-related packages - Install using apt: ```ros-kinetic-pcl-conversions ros-kinetic-pcl-msgs ros-kinetic-pcl-ros```
tf2_eigen - Required for PCL, install using apt: ```sudo apt install ros-kinetic-tf2-eigen```

However, we way need to install a few packages manually; see below.

#### ethz_piksi_ros

The [ethz_piksi_ros](https://github.com/ethz-asl/ethz_piksi_ros) is a ROS package provided by ETH Zurich for the Piksi Multi GPS. Clone it with:

```bash
cd CATKIN_WS/src
git clone https://github.com/ethz-asl/ethz_piksi_ros.git
cd ethz_piksi_ros
git checkout v1.11.0
```

where we need to checkout a non-master branch which doesn't have external dependencies [based on this issue](https://github.com/ethz-asl/ethz_piksi_ros/issues/122).

### Misc Notes

These notes document installing other dependencies which shouldn't be needed, but were previously required by some packages.

#### Installing libsbp

Following the instructions [here](http://wiki.ros.org/swiftnav_ros#Build_And_Install_libsbp) and [this issue](https://github.com/swift-nav/libsbp/issues/705), we build libsbp from source:

```bash
cd /tmp
git clone https://github.com/swift-nav/libsbp
cd libsbp/c
mkdir build
cd build
git submodule update --init --recursive # solution from github issue
cmake ../
make
sudo make install   # install headers and libraries into /usr/local
```

