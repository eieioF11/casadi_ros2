# casadi_ros2
Tested on Ubuntu 22.04 and ROS 2 Humble

## Dependencies

```bash
sudo apt install  coinor-libipopt-dev gfortran libblas-dev liblapack-dev libmetis-dev -y
```

## Installation

### casadi only

```
git clone https://github.com/eieioF11/casadi_ros2.git
colcon build --symlink-install --parallel-workers 3 --cmake-args -DCMAKE_BUILD_TYPE=Release
```

### When using the hsl library

```
git clone https://github.com/eieioF11/casadi_ros2.git
cd casadi_ros2
vcs import --recursive < hsl.repos
colcon build --symlink-install --parallel-workers 3 --cmake-args -DCMAKE_BUILD_TYPE=Release
echo "export LD_LIBRARY_PATH=$ROS_WORKSPACE/install/hsl_vendor/lib:$LD_LIBRARY_PATH" >> ~/.bashrc
```
