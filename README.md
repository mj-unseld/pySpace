# pySpace

## Table of contents

- [pySpace](#pyspace)
  - [Table of contents](#table-of-contents)
- [1. What is it about?](#1-what-is-it-about)
- [2. How to Control](#2-how-to-control)
  - [Progress:](#progress)
- [3. Required packages](#3-required-packages)
- [4. Documentation](#4-documentation)
- [5. Further ideas](#5-further-ideas)
- [6. License](#6-license)
- [About the Author](#about-the-author)
    - [Knowledge/Recently used:](#knowledgerecently-used)
      - [Basic Knowledge/Got in touch with:](#basic-knowledgegot-in-touch-with)
      - [Interests/Want to do:](#interestswant-to-do)

# 1. What is it about?

This small 2D game emulates the Spaceship behavior in a force free space. The player can control the space ship by applying forces via booster (w/s/a/d). By using the Kalman filter, the spaceship estimates the applied force and therefore the acceleration, current velocity, position in space and the mass of the spaceship. It should predict the trajectory of the spaceship in the space. The player can collect power-ups, which increases the mass as load of the spaceship or the power of the booster. The spaceship can just measure the position directly through the radar connection to the earth. This and the applied booster have some noise.

<img style="display: block; margin-left: auto; margin-right: auto; width: 30%" src="source/doc/img/pySpace.png" alt="Green dot: real position, Blue dot: measured position, Red dots: Estimation over time, Yellow dots: 99% bubble, timestep is 1s/10=0.1s" />
<p style="display: block; margin-left: auto; margin-right: auto; width: 30%">Green dot: real position, Blue dot: measured position, Red dots: Estimation over time, Yellow dots: 99% bubble, timestep is 1s/10=0.1s</p>

# 2. How to Control

The spaceship is controlled by standard Keys W/S/A/D.
Changing parameters can be done on the input/output panel to the right side. Hit "update" to be able to control the spaceship again.
## Progress:

Goals for V1:
- [ ] UI
  - [ ] Playground
    - [x] Ship
      - [x] Real position
      - [x] Estimation cloud
      - [x] Transmitted position
    - [ ] Boosterflame
  - [ ] "Cockpit"-Computer view with estimated values such as
    - [x] Input
      - [x] Position (x/y)
      - [x] Velocity
      - [x] Booster force
      - [x] Mass
      - [x] Number of Predictors
      - [x] Update Time
      - [x] Measure Deviance
      - [x] Boosterforce Deviance
    - [ ] Output
      - [x] Spaceship parameters
        - [x] Position
        - [x] Velocity
      - [ ] Graphplots with real and estimated values for: 
        
        *Sidenote: QtQuick do not provide own Plot-integration. Matplotlib just works with QtWidgets and QtCharts have some missing dependencies. Postponed to end.*
        - [ ] Difference real position (x/y) vs. estimated position (x/y) over time
        - [ ] Difference real velocity vs. estimated velocity over time
- [ ] Kernel
  - [ ] Spaceship
    - [x] Ship
    - [ ] Kalman filter/Boardcomputer
      - [x] Position (x/y)
      - [ ] Orientation angle (\theta_{x,y}, \theta_{x,z}, \theta_{y,z}) 
        
        *Requires expanding Kalman Filter to Unscented Kalman Filter. Postponed to V1.5. Also want to compare with Expanded Kalman Filter and see the influence of linearization.*
  - [ ] Power Ups
    - [ ] Loads
    - [ ] Booster

# 3. Required packages

Besides python 3 is [pyQt6](https://pypi.org/project/PyQt6/) required. Whole UserInterface and Signal/Slot communication uses pyQt6. As IDE is VS Code used. The required settings for VS Code are attached.

# 4. Documentation

Documentation can be found [here](source/doc/hub.md).

# 5. Further ideas
Goals for V2:
Offer 3d Space"simulator" as own game type
- [ ] Menu
  - [ ] Offer V1
  - [ ] Add V2
- [ ] UI
  - [ ] Add 3d Game Engine (Panda3d?)
  - [ ] Playground
    - [ ] Add Planets
    - [ ] Astroids
  - [ ] Cockpit view with boardcomputer displaying estimated values such as. Requires expansion of State Space Model if Mass/Load and Boosterforce should be approximated.
    - [ ] Mass/Load
    - [ ] Velocity
    - [ ] Booster force
    - [ ] Current position (x/y/z)
    - [ ] Orientation
  - [ ] Moving Graphplot to submenu
- [ ] Kernel
  - [ ] Spaceship
    - [ ] different ship types
    - [ ] Warp engine
  - [ ] Galaxies
  - [ ] Planets
    - [ ] Movement
    - [ ] Rotation
    - [ ] Gravity

Goals for V3:

Add as further mode "Orrery" where you can watch movement of Plantes just like in a **orrery** with date


- AI calculating route and auto pilot
- add interstellar travelling (with fast forward)

# 6. License

This project uses the GPLv3 [License](LICENSE.md)
# About the Author


Michael Johannes Unseld is 25 years old and study [Medical Engineering](https://studium.hs-ulm.de/de/Seiten/Studiengang_MT.aspx)  at the [Ulm University of Applied Sciences](https://studium.hs-ulm.de/en) (THU). The focus of his studies is software development for Medical Devices, image acquisition and image analysis. During his internship and bachelor thesis, he has already wrote software for the [Institute for Laser Technologies in Medicine and Metrology at the University of Ulm](https://www.ilm-ulm.de/en/index.html) (ILM).

These are some software he has already realized :computer::

* :camera: Hyperspectral-Camera: Gaining images in realtime, read out their spectral data and compressed it into a three-dimensional data cube for data analysis in MATLAB.

* :camera: Optical Coherence Tomography: Control interfaces for a laser diode, spectrometer and three dimensional linear stage as probe table united in one Software. Establishing four different image acquisition procedures with their variants and a save system for data analysis afterwards.

### Knowledge/Recently used:

1. C++
2. Qt
3. MATLAB
4. CMake

#### Basic Knowledge/Got in touch with:

1. Java
2. C#
3. Python
4. OpenCV

#### Interests/Want to do:

* CUDA/GPU-Programming
* Learning Chess
* Study Maxwell's Equations (<- Maybe do a numerical solver to it as project)
* Using Object Identifier/Face Recognition of OpenCV
* Linux programming
* Building small robots based on a Raspberry Pi
* Expanding knowledge in astronomy

``` C++
void WorkLifeBalance() {
  do {
    doSleep();
    startWork();
    while(work) {
      if(coffee == CoffeeState::empty) {
        getCoffee();
      }
    }
  } while(isAlive == true);
}
```