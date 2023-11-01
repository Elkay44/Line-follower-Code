# Line-follower-Code
This code is designed for an Arduino-powered robot with motor control and sensors. It configures motor and sensor pins and enables the robot to perform basic obstacle avoidance. The robot moves forward when the extreme left and extreme right sensors detect values below 700,If the extreme left sensor detects a value above 700.


Configuration and Pin Setup
Motor Control Pins: The code initializes variables (Left_p, Left_n, Right_p, Right_n) to store pin numbers for controlling the motors.
Setup Function: In the setup() function, it configures these pins as output for motor control (Left_p, Left_n, Right_p, Right_n) and also sets analog input pins (A0 to A4) for reading sensor data.
Main Program Logic (Loop)
The primary logic is contained within the loop() function, which continuously runs on the microcontroller:

Reading Sensor Inputs:

It reads sensor values from five analog input pins (A0 to A4), which likely correspond to different infrared sensors used to detect a line on the ground.
Motor Control based on Sensor Readings:

Both extreme sensors below 700: If both extreme sensors (ex_left and ex_right) read values below 700, it implies that the robot is on the line. In this case, it activates both motors to move forward.
Only extreme left sensor above 700: If the extreme left sensor (ex_left) reads a value above 700, it suggests that the robot has deviated to the right of the line. It then instructs the robot to turn left by activating the left motor in reverse and the right motor forward.
Only extreme right sensor above 700: If the extreme right sensor (ex_right) reads a value above 700, indicating deviation to the left of the line, it makes the robot turn right by activating the left motor forward and the right motor in reverse.
Summary
This code implements a simple line-following algorithm for a robot. It continuously reads sensor values from the ground and uses this data to make decisions about how to control the motors to keep the robot following a specific line path. The robot adjusts its movement based on the readings from the extreme left and extreme right sensors to stay on track.
