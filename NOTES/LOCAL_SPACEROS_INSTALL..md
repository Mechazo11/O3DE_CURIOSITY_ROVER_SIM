# Build spaceros_ws for local build and test running rover demo

* Adding extra swap space if ram less than 16Gb

```
sudo fallocate -l 16G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

* Install the vcstool: ```sudo apt-get install python3-vcstool```

* Install these depenendencies

```
sudo apt-get update && \
      sudo apt-get install --yes \
        gcc \
        g++ \
        cmake \
        libgmp-dev \
        libboost-dev \
        libboost-filesystem-dev \
        libboost-thread-dev \
        libboost-test-dev \
        libsqlite3-dev \
        libtbb-dev \
        libz-dev \
        libedit-dev \
        python3 \
        python3-pip \
        python3-venv \
        llvm-14 \
        llvm-14-dev \
        llvm-14-tools \
        clang-14


space_ros_vision_opencv:
    type: git
    url: https://github.com/Mechazo11/space_ros_vision_opencv.git
    version: humble
```

* Install OGRE: ```sudo apt-get install libboost-python-dev build-essential cmake libboost-all-dev libois-dev libzzip-dev libfreeimage-dev libfreetype6-dev libx11-dev libxt-dev libxaw7-dev libsdl2-dev libpugixml-dev libglew-dev qtbase5-dev libspdlog-dev libfmt-dev libignition-gazebo6-dev libssl-dev build-essential devscripts debian-keyring fakeroot debhelper cmake libboost-dev libsasl2-dev libicu-dev libzstd-dev doxygen libtinyxml-dev libtinyxml2-dev python3-pyqt5 python3-rosinstall-generator lark```

* Install Gazebo classic: ```curl -sSL http://get.gazebosim.org | sh```

* Install gazebo6: ```sudo apt-get install libignition-gazebo6-dev```

* Install mongo-cxx-driver: Here is how to install it natively

* Install libmongoc-dev: ```sudo apt-get install libmongoc-dev -y```

* Intall these dependencies: ```sudo apt-get install libssl-dev build-essential devscripts debian-keyring fakeroot debhelper cmake libboost-dev libsasl2-dev libicu-dev libzstd-dev doxygen libtinyxml-dev libtinyxml2-dev python3-pyqt5 -y```

* Git clone the latest stable version:

* Install mongo-cxx-driver

```console
git clone https://github.com/mongodb/mongo-cxx-driver.git \
    --branch releases/stable --depth 1
cd mongo-cxx-driver/build
sudo cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local
sudo make
sudo make install
```

* ```cd ~/spaceros_ws/```

* Install rosintall-generator: ```sudo apt-get update -y && sudo apt-get install -y python3-rosinstall-generator```

* Install the lark library: ```pip3 install lark```

* Clone repositories into ```src``` folder: ```vcs import src < space-ros.repos```

* Clone simulation related packages: ```vcs import src < space-robot-sim.repos```

* Install all dependencies ```rosdep update && rosdep install --from-paths src --ignore-src -r -y --rosdistro humble --skip-keys urdfom_headers ikos```


* Build the workspace excluding the cobra static analyzer: ```colcon build --cmake-args -DCMAKE_BUILD_TYPE=Release -DCMAKE_EXPORT_COMPILE_COMMANDS=ON --no-warn-unused-cli --packages-ignore cobra_vendor```

* Source : ```source ~/spaceros_ws/install/setup.bash```

* Bringup mars rover demo: ```ros2 launch mars_rover mars_rover.launch.py```

---

# Things that did not build

* Install this dependency ```sudo apt install ros-humble-rosidl-typesupport-c```

* NASA's IKOS [DOES NOT WORK]:

```
cd ~/Downloads
git clone git clone -b v3.2 --depth 1 https://github.com/NASA-SW-VnV/ikos.git
cd ikos
mkdir build && cd build

cmake \
        -DCMAKE_INSTALL_PREFIX="/opt/ikos" \
        -DCMAKE_BUILD_TYPE="$build_type" \
        -DLLVM_CONFIG_EXECUTABLE="/usr/lib/llvm-14/bin/llvm-config" \
        ..

sudo make -j4
sudo make install
```

