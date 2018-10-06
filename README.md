# **Model Predictive Controller**

## Overview
-------------------

The main aim in this Project is to control a vehicle in a track using Udacity Simulator by design a Model Predictive Controller (MPC). We will make use of IPOPT & CPPAD Libraries to get the most correct trajectory by feeding a 3rd polynomial function with the waypoints received from Udacity Simulator and then feed them into our model to be able to return the correct Steering angle and acceleration.

[//]: # (Image References)

[image1]: ./MPC_Model.png
[video1]: ./MPC_OutputVideo.mp4

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.

* **Ipopt and CppAD:** Please refer to [this document](https://github.com/udacity/CarND-MPC-Project/blob/master/install_Ipopt_CppAD.md) for installation instructions.
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page). This is already part of the repo so you shouldn't have to worry about it.
* Simulator. You can download these from the [releases tab](https://github.com/udacity/self-driving-car-sim/releases).
* Not a dependency but read the [DATA.md](./DATA.md) for a description of the data sent back from the simulator.


## Rubric points:
-------------------------------------------------------------

### 1. Compilation
-----------------------------

The code compiled successfully using cmake and make.

### 2. Implementation:
-----------------------------

#### **The Model**

The model equations are constructed based on a Kinematic model, The following are the used equations in the model.

![alt text][image1]

#### **Timestep Length and Elapsed Duration (N & dt)**

The number of points **N** and the time interval **dt** define the prediction area and completely affect the MPC Performance. I have tried a large value of **N** but that made the vehicle runs slowly and also drifted away from the track. So I kept decreasing the values until I reached the most optimal values that made the vehicle inside the track. Then I tried to increase the max. speed values from 40 till I reached the max speed of 70.

Following are my chosen Variables Values :

| Variable Name    | Variable Value  |
|:----------------:|:---------------:|
|         N        |       14        |
|        dt        |      0.04       |
|       ref_v      |       70        |

#### **Polynomial Fitting and MPC Preprocessing**

The incoming waypoints from the simulator are transformed to be in the vehicle coordinates. These points are then fitted to a 3rd order polynomial equation so we can get the right coefficients to be able to calculate CTE & EPSI.

#### **Model Predictive Control with Latency**

As the kinematic equations depend on the previous time stamps and as our system can suffer from several delays such as communications delays or actuators delays, We have introduced some delay (100ms) in order to make our system more realistic.


### 3. Simulation:
-----------------------------

The following ![video][video1] shows a full lap using the above MPC controller.
