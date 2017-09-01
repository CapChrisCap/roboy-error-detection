# Implement error patterns

## Publish system notifications (errors, warnings)

### Requirements

As shown in the previous chapters, we want as a developer to be able to publish system notifications to other developers or 
system components, so that they can access them and know what's currently happening with Roboy. 

### Solution

We provide a [SystemNotification component](https://github.com/CapChrisCap/roboy_system_notification) for ROS, which allows you to publish messages with a 
simple API call over the network. 

Example: 

```c++
int MOTOR_DEAD_ERROR_CODE = 4;
int MOTOR_ID = 1;

RoboySystemNotification notificatier;
notificatier.sendErrorMessage(MOTOR_DEAD_ERROR_CODE, MOTOR_ID); 
```

Now the subscriber knows, that the motor one is dead. Nevertheless, this solution has the following limitations: 

 - Requires exchange of message codes
 - No error pattern detection logic included
 - Not reusable
 
 As a solution to these limitations, I implemented the Roboy Error Detection module, which can be accessed on Github: 
  - [Module source code](https://github.com/CapChrisCap/roboy_error_detection)
  - [Module documentation](http://roboy-error-detection-module.readthedocs.io/en/latest/)