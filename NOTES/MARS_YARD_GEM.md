# Mars Yard Gem / Mars like testbed

One or two Terrian asset gem inspired by the Mars Yard gem.

# Key definitions

* Shader:  A process of altering the color of an object/surface in the 3D scene, based on its angle to lights and its distance from lights to create a photo realistic effect.

# Resources 

* Create the NasaCuriosityRoverGem: ```$O3DE_ENGINE/scripts/o3de.sh create-gem -gp $O3DE_DIR/Gems/NasaCuriosityRoverGem --template-name AssetGem```
* Blender To Open3DE: Importing FBX 3D models with Textures: https://www.youtube.com/watch?v=8CcPbfvUOXM
* Physics Material in O3DE: https://docs.o3de.org/docs/user-guide/interactivity/physics/nvidia-physx/materials/
* Understanding shading in five minutes: https://www.youtube.com/watch?v=567FFSk23Io 
* How to add materials in Blender part 1: https://www.youtube.com/watch?v=Wg244y2f9Fw

* Parent-child object: https://www.youtube.com/watch?v=VnXW_r9tTvo

# Mars Yard video resources

* [Video Tour](https://www-robotics.jpl.nasa.gov/gallery/mars-yard-tour-video/)
* [mars yard details](https://www-robotics.jpl.nasa.gov/how-we-do-it/facilities/marsyard-iii/)
* [WareHouseSample Gem for Open 3D Engine](https://github.com/o3de/o3de-extras/tree/development/Gems/WarehouseSample)
* [Export fbx to Open 3D Engine](https://www.youtube.com/watch?v=xUwCf6B-rZQ&t=23s)

* Change units of measurement: https://www.youtube.com/watch?v=oWseWAoeMls

# Mars Yard Gem

High level steops
  * Create 3D models
  * Add mesh and then add texture
  * Export as both ```fbx``` and ```gltf```


* Create the MarsYardGem: ```$O3DE_ENGINE/scripts/o3de.sh create-gem -gp $O3DE_DIR/Gems/MarsYardGem --template-name AssetGem```.

* Register MarsYardGem to ```RobotSim``` project: ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $O3DE_DIR/Gems/MarsYardGem```

* Change path to project root directory: ```cd $PROJECT_PATH```

* Run cmake: ```cmake -B build/linux -G "Ninja Multi-Config" -DLY_DISABLE_TEST_MODULES=ON -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DLY_STRIP_DEBUG_SYMBOLS=ON -DAZ_USE_PHYSX5:BOOL=ON``` 

* Build project: ```cmake --build build/linux --config profile --target ${PROJECT_NAME} Editor ${PROJECT_NAME}.Assets```

* Open Project: ```${PROJECT_PATH}/build/linux/bin/profile/Editor```


