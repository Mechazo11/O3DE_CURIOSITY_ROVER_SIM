# O3DE_ROVER_SIMULATION

All pertinent notes, assets related to the curiosity rover O3DE project



### Resources for figuring out how to get started with a robot Asset

* [ROS2FleetRobotTemplate project.json file](https://github.com/o3de/o3de-extras/blob/development/Templates/Ros2ProjectTemplate/Template/project.json)



### Full workflow in creating a new robot AssetGem

[optional] Add 16gb swap

```
sudo fallocate -l 16G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

* Setup [O3DE-Project centric](https://www.docs.o3de.org/docs/welcome-guide/setup/setup-from-github/) from Github

* Register this engine
```
cd $O3DE_ENGINE
./scripts/o3de.sh register --this-engine
```

* Build the engine [optional]
```
cd $O3DE_ENGINE
./python/get_python.sh
cmake -B build/linux -S . -G "Ninja Multi-Config"
```

* Add ROS2 Gem and related Gems to use in all O3DE projects: 

```
$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_EXTRAS/Gems/ROS2
$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_EXTRAS/Gems/RosRobotSample
$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_EXTRAS/Gems/WarehouseAssets
$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_EXTRAS/Gems/WarehouseSample
$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_EXTRAS/Gems/ProteusRobot
```

* If already built, just register the project: ```$O3DE_ENGINE/scripts/o3de.sh register --project-path $O3DE_DIR/Projects/$PROJECT_NAME```

* Start the **RobotSim** O3DE Project from ROS2: ```$O3DE_ENGINE/scripts/o3de.sh create-project --project-path $O3DE_DIR/Projects/$PROJECT_NAME --template-path ${O3DE_EXTRAS}/Templates/Ros2ProjectTemplate```

* Create the NasaCuriosityRoverGem: ```$O3DE_ENGINE/scripts/o3de.sh create-gem -gp $O3DE_DIR/Gems/NasaCuriosityRoverGem --template-name AssetGem```

* Update gem.json of NasaCuriosityRoverGem in VSCode to add proper dependenceies

* Register NasaCuriosityRoverGem to ```RobotSim``` project: ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_DIR/Gems/NasaCuriosityRoverGem```

* Unregister NasaCuriosityRoverGem to ```RobotSim``` project: ```$O3DE_ENGINE/scripts/o3de.sh unregister --gem-path $O3DE_DIR/Gems/NasaCuriosityRoverGem```

* Manually modify ```project.json``` to add ```NasaCuriosityRoverGem```  to the project: Open project with VSCode and add them similar to the Robotec.Ai's [ROSCon2023](https://github.com/RobotecAI/ROSCon2023Demo/blob/development/Project/project.json) sample.

* Source ROS 2 workspace: ```source ~/spaceros_ws/install/setup.bash```

* **Build the project** using the following commands


* Change path to project root directory: ```cd $PROJECT_PATH```

* Run cmake: ```cmake -B build/linux -G "Ninja Multi-Config" -DLY_DISABLE_TEST_MODULES=ON -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DLY_STRIP_DEBUG_SYMBOLS=ON -DAZ_USE_PHYSX5:BOOL=ON``` 

* Build project: ```cmake --build build/linux --config profile --target ${PROJECT_NAME} Editor ${PROJECT_NAME}.Assets```


* Change middleware to CycloneDDS RMW as recommended by MoveIT2: ```export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp```

* Launch Project manager: ```$O3DE_ENGINE/bin/Linux/profile/Default/o3de```

* Start ```RobotSim``` project: ```${PROJECT_PATH}/build/linux/bin/profile/Editor```

## RobotImporter

* Copied URDF, assets and prefab are placed in ```$PROJECT_PATH/Assessts``` folder

* Husarion robot's gazebo [urdf files](https://github.com/husarion/husarion_gz_worlds)
```$(find rosbot_xl_description)/urdf/rosbot_xl_macro.urdf.xacro```


* "If the Source asset field is marked as failed, then Robot Importer cannot find a reference to the mesh file in the file system. In such a situation, ensure that the robot’s description package is built and sourced correctly. You can try to give a custom way to resolve prefixes in Point 4."

## Troubleshooting

* Create the ArmTestGem: ```$O3DE_ENGINE/scripts/o3de.sh create-gem -gp $O3DE_DIR/Gems/ArmTestGem --template-name AssetGem```

* ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_DIR/Gems/ArmTestGem```

# Resources

* [O3DE Editor](https://docs.o3de.org/docs/user-guide/editor/)

* [How to Configure a ROS 2 Project in O3DE](https://development--o3deorg.netlify.app/docs/user-guide/interactivity/robotics/project-configuration/)

* [RobotImporter](https://docs.o3de.org/docs/user-guide/interactivity/robotics/importing-robot/)

* [ProteusRobot Asset Gem](https://github.com/o3de/o3de-extras/tree/development/Gems/ProteusRobot)

* [Project Creation with Open 3D Engine](https://www.docs.o3de.org/docs/welcome-guide/create/creating-projects-using-cli/creating-linux/)

* [Add/Delete Gems](https://www.docs.o3de.org/docs/user-guide/project-config/add-remove-gems/)