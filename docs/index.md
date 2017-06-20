# Roboy Error Detection

I participate this year at the Roboy lap course and this is the documentation
for this year. I prepare the topic `Error Detection` in the `Control` group.
This year, a new Roboy should be developed.


## Roboy 1.0

![Roboy 1.0][roboy]

Roboy 1.0 is a humanoid robot, which is able to talk, move as well as react to the environment.
The code is mostly written in `C++` and is maintained by a student group of the TUM. More information can
be found at the website http://roboy.org/.

## Problem statement

Roboy 1.0 is working well but the software as well as the hardware is outdated and hard to
maintain. Therefore, Roboy is working but it is hard to add new features. Another problem is that
Roboy is not able to walk. Therefore, a new Roboy version should be developed.

One new feature of the new Roboy version should be that the maintainability should be increased. Therefore,
the following features (just an excerpt!) should be implemented

 * Improved Calibration
 * Error detection

### Improved Calibration

With the old Roboy 1.0, the calibration process is a pain because everything should be made manually. Therefore,
this process should be automated. The main part is to find automatically the initial state of each motor and angle.

Nevertheless, Calibration is not the main part of this documentation but the current state of the motors and angles is
required for the error detection process. The reason for this is explained in the following.

### Error detection

Apart from the improved calibration, another feature of Roboy 2.0 should be to detect errors. This means that it is possible to
display motor / joint state errors (or messages in general) to external applications. One use case could be that an application
is developed, which displays all Roboy states. This includes also different messages, which should help the developers to debug errors.
That means if a motor state changed to an unnormal behavior, then the developers should be notified.

Therefore, the tasks for this semester are:

1. [Familiarize with motors and joints](./1-familiarize-with-motors-and-joints.md)
2. [Define possible motor and joint states depending on the starting points](./2-define-possible-motor-and-joint-states.md)
3. Create ROS topic to publish the error messages
4. Define possible error patterns to detect more complex patterns
5. Implement a mechanism to track these complex patterns
6. Send these patterns over ROS

More information can be found here: [https://devanthro.atlassian.net/wiki/display/CO/Research+-+Interface+to+Middleware](https://devanthro.atlassian.net/wiki/display/CO/Research+-+Interface+to+Middleware)

[roboy]: http://www.3dnatives.com/de/wp-content/uploads/sites/3/210217_Roboy2.jpg