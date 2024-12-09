# O3DE_Installation

Open 3D Engine (O3DE) is a real-time, cross-platform, Apache 2.0-licensed 3D engine that enables developers and content creators to build AAA games, cinema-quality 3D worlds, and high-fidelity simulations without any fees or commercial obligations. Some of its features include: the Atom renderer, visual and Lua scripting, physics simulations, and the white box tool.

O3DE license is Apache 2.0. So it is closely compatible with Space ROS. Under the hood uses Atom: Cross-platform, data driven, multi-threaded renderer

* [O3DE Renderer Technical Review](https://www.youtube.com/watch?v=_EDU0TMLMjo)

* [O3DE Robotics Simulator with Adam Dabrowski](https://www.youtube.com/watch?v=n8a_3vaW4Ag)

* [Robotics and Simulation](https://o3de.org/industries/robotics-and-simulations/)

* [O3DE Robotics Warehouse Demo](https://www.youtube.com/watch?v=Zx-6VhxqLKc)

## Overview of tool

![alt text](image.png)

O3DE is a sandbox of development tools and assets, provided by Gems, that you can combine and use within your project. You only need to include the Gems that provide the features and functionality that your project requires.

* [ROS 2 Gem](https://docs.o3de.org/docs/user-guide/gems/reference/robotics/ros2/)

* [ROS 2 Concepts and Structure](https://docs.o3de.org/docs/user-guide/interactivity/robotics/concepts-and-components-overview/)

* [ROS 2 API](https://docs.o3de.org/docs/api/gems/ros2/)

* [Useful templates](https://github.com/o3de/o3de-extras/tree/development/Templates)

---

# Core resources

* [Installing gazebo_ros_pkgs in ROS 2](http://classic.gazebosim.org/tutorials?tut=ros2_installing&cat=connect_ros)

* [Getting Started Guide](https://docs.o3de.org/docs/welcome-guide/)

* [Creating a Robotic Simulation](https://docs.o3de.org/docs/user-guide/interactivity/robotics/creating-robotic-simulation/)

* [Simulating Physics Behavior with PhysX System](https://docs.o3de.org/docs/user-guide/interactivity/physics/nvidia-physx/)

* [Robotic Simulation Project Template for ROS 2](https://github.com/o3de/o3de-extras/tree/development/Templates/Ros2ProjectTemplate)

* [ROS2 Fleet Template](https://github.com/o3de/o3de-extras/tree/development/Templates/Ros2FleetRobotTemplate)

* [Guide to starting your first simulation project](https://robotec.ai/how-to-start-robotics-simulation-projects-in-open-3d-engine-o3de/)

* [O3DE ROSbot XL tutorial](https://husarion.com/tutorials/simulations/o3de-rosbot-xl-slam-toolbox/)

* [robotec.ai tutorial of 36 robot simulation](https://robotec.ai/how-we-built-a-robotic-simulation-in-open-3d-engine/)

* [Roscon2023demo](https://github.com/RobotecAI/ROSCon2023Demo/blob/development/README.md) has the tutorial of building O3DE from source.

* [Install prerequisits](https://docs.o3de.org/docs/welcome-guide/requirements/#software-prerequisites)

**Main** tutorial

* https://docs.o3de.org/docs/user-guide/interactivity/robotics/project-configuration/

## Suggested Robotics simulation workflow

```
* Create a new O3DE project
    It is best to use one of Project Templates for robotics to start quickly.
* Registering ROS2 Gem for your Project guide.
* Create or import Assets for your robots and environment.
    You can use formats supported by O3DE.
    You can import your robot from URDF/XACRO.
    Imported models might require some adjustments to be simulation-ready.
    Mobilize robot with Vehicle Dynamics controllers.
* Determine which sensors you need to simulate.
    Some sensors are already implemented in this Gem.
        They might require specialization (implementation specific for particular models).
        You might like to consider tradeoffs between performance and realism in each case.
    Use ROS2SensorComponent as a base class if you are implementing a new sensor.
* Develop necessary sensors and their prefabs.
* Develop your scene and simulation scenario, placing Assets and configuring components.
* Run the simulation with your ROS 2 robot stack. You can build quickly one with some of many * ROS 2 packages and projects in ROS 2 ecosystem .
```

## Deleting a Project

* Delete project folder: ```rm -rf path/to/your_project```
* Remove project name from o3de_manifest.json: ```code . ~/.o3de/o3de_manifest.json```

---

## Setup O3DE to use the demo project:

This is the Husarion RobotXL project.

* Setup some path variables

```
export PROJECT_NAME=test_proj
export O3DE_EXTRAS_HOME=${HOME}/o3de_dir/o3de-extras
export PROJECT_PATH=${HOME}/o3de_dir/test_proj
```

* Ensure all path variables are correctly setup

```
echo $PROJECT_PATH $O3DE_EXTRAS_HOME
```


* [Build O3DE for linux](https://www.docs.o3de.org/docs/welcome-guide/setup/setup-from-github/building-linux/)

    * GNU C++ library: ```sudo apt install libstdc++-12-dev clang``` 
    * Additional dependencies: ```sudo apt install libglu1-mesa-dev libxcb-xinerama0 libxcb-xinput0 libxcb-xinput-dev libxcb-xfixes0-dev libxcb-xkb-dev libxkbcommon-dev libxkbcommon-x11-dev libfontconfig1-dev libpcre2-16-0 zlib1g-dev mesa-common-dev libunwind-dev libzstd-dev```
    * git-lfs: ```sudo apt install git-lfs```

* Install **o3de** engine

```console
cd ${WORKDIR}
git clone --branch 2310.1 --single-branch https://github.com/o3de/o3de.git
cd o3de
git lfs install
git lfs pull
python/get_python.sh
scripts/o3de.sh register --this-engine
```

* Install **o3de-extras**

```console
cd ${WORKDIR}
git clone --branch 2310.1 --single-branch https://github.com/o3de/o3de-extras
cd o3de-extras
git lfs install
git lfs pull
```

* Setup enviornment variables

* Change directory into ```o3de_dir```: ```cd ~/o3de_dir```


## Create project and use ROS2 Template demo

* 08/31 this part is **depricated**

* Register Gem

```
cd ~/o3de_dir
./o3de/scripts/o3de.sh register --gem-path ${O3DE_EXTRAS_HOME}/Gems/ROS2
./o3de/scripts/o3de.sh register --gem-path ${O3DE_EXTRAS_HOME}/Gems/RosRobotSample
./o3de/scripts/o3de.sh register --gem-path ${O3DE_EXTRAS_HOME}/Gems/WarehouseAssets
./o3de/scripts/o3de.sh register --gem-path ${O3DE_EXTRAS_HOME}/Gems/WarehouseSample
```

* Create a Project: git clone or create project folder in home 

```console
cd ~ 

mkdir o3de_dir && cd o3de_dir
```

* Create new project from template:

```./o3de/scripts/o3de.sh create-project --project-path ${PROJECT_PATH} --template-path ${O3DE_EXTRAS_HOME}/Templates/Ros2ProjectTemplate```

* Source ROS workspace: ```source ~/spaceros_ws/install/setup.bash```

* Change middleware to CycloneDDS RMW as recommended by MoveIT2: ```export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp```

* Source ROS workspace: ```source ~/spaceros_ws/install/setup.bash```

* Build project:

```
cd $PROJECT_PATH

cmake -B build/linux -G "Ninja Multi-Config" -DLY_DISABLE_TEST_MODULES=ON -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DLY_STRIP_DEBUG_SYMBOLS=ON -DAZ_USE_PHYSX5:BOOL=ON 

cmake --build build/linux --config profile --target ${PROJECT_NAME} Editor ${PROJECT_NAME}.Assets 
```

* Run editor: ```{PROJECT_PATH}/build/linux/bin/profile/Editor```
or ```./build/linux/bin/profile/Editor```

* Test run the [level](https://husarion.com/tutorials/simulations/o3de-rosbot-xl-slam-toolbox/)

## Create New O3DE gems

* [Coding Gems](https://www.youtube.com/watch?v=eteg4uLAZlM)

* [Ros2RobotFeelTemplate](): Has a short tutorial on changing the warehouse layout

* [ROSCon2023 Demo](https://vimeo.com/879001753)
  * ROS 2 Gem uniquely added interactive engine.
  <!-- * ![alt text](image-1.png) -->

  * Best fit of open-source, ROS and Photorealistic 3D engine

* [How Prefab works?](https://www.youtube.com/watch?v=mdvRCfyuMEk)

* [O3DE Editor101](https://www.youtube.com/watch?v=9SvNesdCPps)
