# **Model Predictive Controller**

## Overview
-------------------



## Model Predictive Controller Project Goals
-------------------------------------------------------------

**The goals / steps of this project are the following:**

  1.  
  2. 
  3. 

[//]: # (Image References)

[image1]: ./PID_Design.png
[video1]: ./PID_Output.mp4

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


### 3. Reflection:
------------------------------

#### PID Description


##### 1. Proportional Controller


##### 2. Integral Controller



##### 3. Derivative Controller



#### Tuning PID Coefficients



Following are my chosen Coefficients:

| PID Coefficients | Coefficients Values  |
|:----------------:|:--------------------:|
| KP_coff          |          0.1         |
| KI_coff          |          0.001       |
| KD_coff          |          1.4         |

For the throttle, I have designed a PID controller for it as well, but I found that setting it by 0.25 with the above parameters is working perfectly.

This ![video][video1] shows a full lap using the above PID controller.
