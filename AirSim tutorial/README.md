# AirSim Tutorial
AirSim is a simulator for drones, cars and more, built on [Unreal Engine](https://www.unrealengine.com/en-US/?sessionInvalidated=true). It is open-source, cross platform, and supports hardware-in-loop with popular flight controllers such as PX4 for physically and visually realistic simulations. It is developed as an Unreal plugin that can simply be dropped into any Unreal environment.
- Latest release v1.3.1 for [Windows](https://github.com/microsoft/AirSim/releases/tag/v1.3.1-windows) and [Linux](https://github.com/microsoft/AirSim/releases/tag/v1.3.1-linux)
- Upgraded to Unreal Engine 4.24, Visual Studio 2019, Clang 8, C++ 17 standard.
- Support for [ArduPilot](https://ardupilot.org/ardupilot/) - [Copter, Rover vehicles](https://ardupilot.org/dev/docs/sitl-with-airsim.html)
- Updated airsim Python package, with lots of new APIs
- ROS wrapper for multirotors is available
- [Plotting APIs for Debugging](https://github.com/microsoft/AirSim/pull/2304)

## 1.1 How to Get It
Users can either use pre-compiled binaries or build the Unreal Engine and Airsim framework locally. 
- [Download binaries](https://microsoft.github.io/AirSim/use_precompiled/): You can simply download precompiled binaries and run to get started immediately. 
- [Build it locally on Windows](https://microsoft.github.io/AirSim/build_windows/) 


### 1.1.1 Precompiled Binaries
Precompiled binaries are provided for both [Linux](https://github.com/microsoft/AirSim/releases/tag/v1.3.1-linux) and [Windows](https://github.com/microsoft/AirSim/releases/tag/v1.3.1-windows). Users can just download the zip files and run the application. 

### 1.1.2	[Build Airsim Framework on Linux](https://microsoft.github.io/AirSim/build_linux/)
The current recommended and tested environment is **Ubuntu 18.04 LTS**. Theoretically, you can build on other distros as well, but we haven't tested it.

Following steps needs to be followed. 
- **Build Unreal Engine**
  - Make sure you are [registered with Epic Games](https://www.unrealengine.com/en-US/). This is required to get source code access for Unreal Engine.
  - Connect with your github under account settings.
  ![unreal_connect](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/unreal_connect.png)
  - Accept the invitation on: https://github.com/EpicGames
  ![accept_invi](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/accept_invi.png)
  - Clone [Unreal](https://github.com/EpicGames/UnrealEngine.git) in your favorite folder and build it (this may take a while!). **Note**: We recommend using Unreal 4.24.
  ```
  bash
   # go to the folder where you clone GitHub projects
   git clone -b 4.24 https://github.com/EpicGames/UnrealEngine.git
   cd UnrealEngine
   ./Setup.sh
   ./GenerateProjectFiles.sh
   make
  ```
  If user is building Unreal Engine on Ubuntu 20.04 LTS, use following trick to resolve the make error: ![ubuntu_lts_204](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/ubuntu_lts_204.png)

- **Build Airsim**
  - Clone [AirSim](https://github.com/Microsoft/AirSim.git) and build it
  ```
  bash
   # go to the folder where you clone GitHub projects
   git clone https://github.com/Microsoft/AirSim.git
   cd AirSim
  ``` 
  By default AirSim recommends using clang 8 to build the binaries as those will be compatible with UE 4.24. The setup script will install the right version of cmake, llvm, and eigen.
  ```
  bash
   ./setup.sh
   ./build.sh
  ```
### 1.1.3	[Build Airsim Framework on Windows](https://microsoft.github.io/AirSim/build_windows/)
### 1.2 Build Unreal Project
You will need an Unreal project that hosts the environment for your vehicles. AirSim comes with a built-in "Blocks Environment" which you can use, or you can create your own. Please see [setting up Unreal Environment](https://microsoft.github.io/AirSim/unreal_proj/). The Unreal Marketplace has [several environments](https://www.unrealengine.com/marketplace/en-US/content-cat/assets/environments?count=20&sortBy=effectiveDate&sortDir=DESC&start=0) available that you can start using in just few minutes. It is also possible to use environments available on websites such as [turbosquid.com](https://www.turbosquid.com/) or [cgitrader.com](https://www.cgtrader.com/) with bit more effort (here's [tutorial video](https://www.youtube.com/watch?v=y09VbdQWvQY&feature)). In addition there also several [free](https://github.com/Microsoft/AirSim/issues/424). 

Below we will use a freely downloadable environment from Unreal Marketplace called Landscape Mountain but the steps are same for any other environments. You can also view these steps performed in [Unreal AirSim Setup Video](https://www.youtube.com/watch?v=1oY8Qu5maQQ&feature=youtu.be).

**Step by step instructions:**

- Make sure AirSim is built and Unreal 4.24 or above is installed as described in above build instructions.
- Create a new C++ project in unreal editor.
![cpp_proj](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/cpp_proj.png)
- This will launch visual studio with new c++ project.   
![cpp_proj_panel](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/cpp_proj_panel.png)
- In **Epic Games Launcher** click the Learn tab then scroll down and find **Landscape Mountains**( User is free to choose any other environment). Click on **Create Project** and download this content (~2GB download)
- Merge the downloaded content with the my project content. Follow the video link instructions to know the steps to follow for merging. We will add both the original config files and changes files on github, so users can cross check whether they have merged all the required changes. 
- Go to your folder for AirSim repo and copy **Unreal\Plugins** folder in to your **my_project** folder. This way now your own Unreal project has AirSim plugin.
- Edit the **my_project.uproject** so that it looks like this
![my_project_uproject](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/my_project_uproject.png)
- Launch unreal editor, go to file menu to refresh visual studio
![launch_editor](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/launch_editor.png)
- Load visual studio. My project environment is setup now.
![load_VS](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/load_VS.png)
- In **Window/World Settings** as shown below, set the **GameMode Override** to **AirSimGameMode**
![airsim_mode](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/AirSim%20tutorial/src/airsim_mode.png)
