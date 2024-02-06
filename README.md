# casadi_ros2
Tested on Ubuntu 22.04 and ROS 2 Humble.

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
## Example
### include

```c++
// casadi
#include "casadi/casadi.hpp"
```

### package.xml

```xml
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>mpc_path_planning</name>
  <version>0.0.0</version>
  <description>TODO: Package description</description>
  <maintainer email="eieioeiji0501@gmail.com">f11</maintainer>
  <license>TODO: License declaration</license>

  <buildtool_depend>ament_cmake</buildtool_depend>

  <depend>rclcpp</depend>
  <depend>rclcpp_components</depend>
  <depend>std_msgs</depend>
  <depend>tf2</depend>
  <depend>tf2_ros</depend>
  <depend>tf2_geometry_msgs</depend>
  <depend>geometry_msgs</depend>
  <depend>visualization_msgs</depend>
  <depend>sensor_msgs</depend>
  <depend>nav_msgs</depend>

  <depend>casadi_ament</depend>

  <test_depend>ament_lint_auto</test_depend>
  <test_depend>ament_lint_common</test_depend>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>
```

### CMakeLists.txt

```
cmake_minimum_required(VERSION 3.5)
project(mpc_path_planning)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_add_executable(${PROJECT_NAME} src/main.cpp)

ament_auto_package()
```
