PCA9685 ROS package
=======

`ros_pca9685` is a package  for talking to the PCA9685 I<sup>2</sup>C PWM driver by NXP

PCA9685 Highlights from [datasheet](http://www.nxp.com/documents/data_sheet/PCA9685.pdf)
--------

*	**16 individually controlled channels**
*	**12bit (4096 steps) registers both for on and off time**
*	**1MHz fast I<sup>2</sup>C bus interface with 30mA high drive capability on SDA output for driving high capacitive buses**
*	**40MHz to 1000MHz PWM frequency for all LEDs with internal 25MHz oscillator**
*	**Operating power supply voltage range of 2.3 V to 5.5 V**
*	**Six hardware address pins allow up to 62 devices on the same bus**

Usage on Raspberry PI

Install
===============

1. Creating workspace

```bash
    $ mkdir -p ~/pca_ws/src
    $ cd ~/pca_ws/src
    $ git clone https://github.com/dennn66/ros_pca9685
    $ 
    $ cd ~/pca_ws
    $ catkin_make_isolated
```
Run
================

```bash
    $ rosrun ros_pca9685 controller_sub
```

Pub/Sub
=================

Publish
-----------

Subscribe
-----------
* /servostate_to_controller (pca9685_msgs/ServoState): move servo (range: -Pi .. Pi)
* /pwmstate_to_controller   (pca9685_msgs/PwmState)  : set pulse margins (0..4096, 0..4096)

Test
=================

```
   $ rostopic pub /servostate_to_controller pca9685_msgs/ServoState '{servo_num: 1, servo_rot: 0.5}' --once
   $ rostopic pub /pwmstate_to_controller pca9685_msgs/PwmState '{port_num: 1, on_value: 0, off_value: 400}' --once

```
