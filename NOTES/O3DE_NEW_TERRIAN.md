# O3DE New Terrinan

This markdown file contains pertinent information on how to create a new terrian.

* Change path to project root directory: ```cd $PROJECT_PATH```

* Run cmake: ```cmake -B build/linux -G "Ninja Multi-Config" -DLY_DISABLE_TEST_MODULES=ON -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DLY_STRIP_DEBUG_SYMBOLS=ON -DAZ_USE_PHYSX5:BOOL=ON``` 

* Build proejct: ```cmake --build build/linux --config profile --target ${PROJECT_NAME} Editor ${PROJECT_NAME}.Assets```

* Launch Project manager: ```$O3DE_ENGINE/bin/Linux/profile/Default/o3de```

* Start ```RobotSim``` project: ```${PROJECT_PATH}/build/linux/bin/profile/Editor```

* [How to Install](https://www.docs.o3de.org/docs/user-guide/gems/reference/environment/terrain/)

  * Add Terrain Gem: ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $HOME/o3de/Gems/Terrain```

  * Add GradientSignal: ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $HOME/o3de/Gems/GradientSignal```

  * Add LandscapeCanvas: ```$O3DE_ENGINE/scripts/o3de.sh register --gem-path $HOME/o3de/Gems/LandscapeCanvas```

* [Tutorial on creating Terrian from Images](https://www.docs.o3de.org/docs/learning-guide/tutorials/environments/create-terrain-from-images/)