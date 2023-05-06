Download Link: https://assignmentchef.com/product/solved-ee209as-computational-robotics-3
<br>



<h1>Objectives</h1>

The goal of this lab is to explore Kalman Filtering (KF) to estimate the state of a simple two-wheeled non-holonomic robot with realistic hardware. You will develop and implement a mathematical model of the robot sensor and actuator behavior and use it to evaluate a state estimation algorithm.




<h1>Preliminaries</h1>

0(a). What is the link to your (fully commented) github repo for this pset?

0(b). Who did you collaborate with?

0(c). What other resources did you use?

0(d). What was the aggregate % contributions of each team member?

<h1>1        Robot model</h1>

<h2>1.1       Ideal state dynamics</h2>

You will again consider a two-wheeled robot from last lab, shown in Fig. 1. It has two wheels of radius <em>r </em>= 25<em>mm</em>, separated by a distance <em>w </em>= 90<em>mm</em>. It drags a tail for stability, at a distance <em>l </em>= 75<em>mm </em>behind the centerpoint of the wheels. The position of this robot in the environment is defined relative to the centerpoint of the wheels.

Each wheel is powered independently by a continuous rotation servo, with the angular velocity of the wheel controlled by a PWM signal from the microcontroller. Assume each input prescribes the respective angular speed of the wheel, from -60 to +60 RPM. This allows the robot to drive forwards or backwards at variable speed, or turn with any turning radius.

<h2>1.2       Real state dynamics</h2>

Each wheel is powered independently by a bi-directional continuous rotation servo—part number FS90R—with the angular velocity of the wheel controlled by a signal from the microcontroller. There may be slippage between the wheels and the floor or sticking in the gears of the motor; assume the resulting effective angular speed of each wheel is normal and i.i.d. with a standard deviation of 5% of the max motor speed.

Figure 1: Two wheeled tank-drive robot, with dimensions as specified

<h2>1.3       Sensing model</h2>

The robot has two laser range sensors—part number VL53L0X—and an inertial measurement unit (IMU)—part number MPU-9250. The output of these sensors will be a function of the state of the robot within its environment. Use data sheets for these specific sensors to determine their sensor response and noise models.

The output from the laser range sensors will consist of 1) the distance to a wall in a straight line in front of the robot, and 2) the distance to a wall in a straight line to the right of the robot. The IMU will return 1) an absolute bearing indicating the angle of the robot with respect to magnetic north, and also 2) an measurement of the rotational speed from a angular rate (gyro) sensor. We will ignore the accelerometer on the IMU. Thus the robot system will produce 4 output values.

<h1>2        Mathematical setup</h1>

The robot will be driving within a rectangular environment of length <em>L </em>= 750<em>mm </em>and width <em>W </em>= 500<em>mm</em>, consisting of 4 walls bounding an open space.

2(a). Define the complete system model. You will need to derive and present the mathematical equations describing this robot plant, including the appropriate sensor and actuator models and system dynamics. Note that you will need to amend the state of your robot from the previous lab in order to accomodate this specific collection of sensors. Be sure to clearly define and describe all variables and equations, and produce illustrative diagrams as necessary.

2(b). Include realistic noise terms into the model as appropriate, and numerically quantify their parameters.

2(c). Create a Kalman Filter based state estimator to take the motor commands and sensor measurements and generate a state estimate. You will likely want to to implement an Extended Kalman Filter (EKF), but you could choose an Unscented Kalman Filter (UKF) instead. Be sure to explain which algorithm you chose and why, and generate the resulting mathematical expressions.

<h1>3        Evaluation</h1>

You should evaluate your algorithms in a simulated environment. You should implement several pre-programmed trajectories; you can also get arbitrary control inputs from a human driver.

3(a). Define and describe several reference trajectories (that in turn generate control input sequences) that capture the abilities and limitations of a state estimator in this environment.

3(b). Implement a simulation, including models of your sensor and actuator response (especially including noise), to generate realistic sensor traces given the above control inputs. Present and explain the simulated sensor traces.

3(c). Implement your KF based state estimator on these examples, demonstrating the performance (in terms of accuracy and efficiency) of your computed state estimate over time as the robot is issued commanded input sequences. Consider both perfect knowledge of the initial state as well as no knowledge of the initial state on the same traces. Clearly describe the experiments that were run, the data that was gathered, and the process by which you use that data to characterize the performance of your state estimator. Include figures; you may also refer to animations uploaded to your git repo.

3(d). How might you accomodate more realistic system models? For example, the gyro sensor doesn’t have zeromean additive noise; rather, the mean of the gyro noise is a slowly varying non-zero bias value. The actuator uncertainty (process noise) typically depends on the commanded speed itself. Describe the updates to the system model in these and other cases, and how that would impact your state estimator.

3(e). Qualitatively describe some conclusions about the effectiveness of your state estimator for potential tasks your robot may encounter, and tradeoffs regarding yours vs other possible state estimation algorithms.