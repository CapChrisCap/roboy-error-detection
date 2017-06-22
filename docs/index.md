# Roboy Error Detection

## Problem statement

One new feature of the new Roboy version will be a increased maintainability. Therefore,
the following features (just an excerpt!) will be implemented this semester (SS2017):

 * Improved Calibration
 * Error detection

### Improved Calibration

With the old Roboy 1.0, the calibration process is a pain because everything have to be made manually. Therefore,
this process has to be more automated. The main part is to find automatically the initial state of each motor and angle.

Nevertheless, Calibration is not the main part of this documentation but the current state of the motors and angles is
required for the error detection process. The reason for this is explained in the following.

### Error detection

Apart from the improved calibration, another feature of Roboy 2.0 should be to detect errors. After this semester, the 
following use-cases should be implemented: 
 - An API is provided to send and publish notifications to other network participants (like sharing motor error messages)
 - A new ROS node should be created, which listens to joints and motors to evaluate them and send/publish/share error messages
   to other network participants
 - The errors, published over ROS, should be uniquely identifiable (e.g. by an error ID) and the send should be able to define 
   the part of Roboy, which causes the error (e.g. by providing a part/equipment ID)

Therefore, the tasks for this semester are:

1. [Familiarize with motors and joints](./1-familiarize-with-motors-and-joints.md)
2. [Define possible motor and joint states depending on the starting points](./2-define-possible-motor-and-joint-states.md)
3. [Create ROS topic to publish the error messages](./3-define-ros-topic-for-error-messages.md)
4. Define possible error patterns to detect more complex patterns
5. Implement a mechanism to track these complex patterns
6. Send these patterns over ROS

More information can be found here: [https://devanthro.atlassian.net/wiki/display/CO/Research+-+Interface+to+Middleware](https://devanthro.atlassian.net/wiki/display/CO/Research+-+Interface+to+Middleware)
