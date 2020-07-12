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
  - Clone Unreal in your favorite folder and build it (this may take a while!). **Note**: We recommend using Unreal 4.24.
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
  - Clone AirSim and build it:
  ```
  bash
   # go to the folder where you clone GitHub projects
   git clone https://github.com/Microsoft/AirSim.git
   cd AirSim
  ```

