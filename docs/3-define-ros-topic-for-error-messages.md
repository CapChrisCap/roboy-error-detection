# Define ROS topic for error messages

## 1. Publish system notifications (errors, warnings)

### Requirements

As a developer, I want to be able to publish system notifications with other developers or 
system components, so that I can access them when I need them. 

### Solution

We provide a SystemNotification component for ROS, which allows you to publish messages with a 
simple API call over the network. 

Example: 

```c++
int MOTOR_DEAD_ERROR_CODE = 4;
int MOTOR_ID = 1;

RoboySystemNotification notificatier;
notificatier.sendErrorMessage(MOTOR_DEAD_ERROR_CODE, MOTOR_ID); 
```

Now the subscriber knows, that the motor one is dead. 

### Installation

1. Add the package `roboy_system_notification` ([https://github.com/CapChrisCap/roboy_system_notification](https://github.com/CapChrisCap/roboy_system_notification) to your CMakeFile
2. Implement the class like shown in the main example: [https://github.com/CapChrisCap/roboy_system_notification/blob/master/src/main.cpp](https://github.com/CapChrisCap/roboy_system_notification)

### ROS Topic information

Message: [https://github.com/CapChrisCap/roboy_communication/blob/feature/error-detection-msgs/roboy_communication_control/msg/SystemNotification.msg](https://github.com/CapChrisCap/roboy_communication/blob/feature/error-detection-msgs/roboy_communication_control/msg/SystemNotification.msg)
List of error codes: [https://github.com/CapChrisCap/roboy_communication/blob/feature/error-detection-msgs/middleware/include/common_utilities/CommonDefinitions.h#L16](https://github.com/CapChrisCap/roboy_communication/blob/feature/error-detection-msgs/middleware/include/common_utilities/CommonDefinitions.h#L16)

### Limitations

The package was not yet tested and compiled and is not production ready. 


## 2. Enable Error Detection

### Requirements

As a developer, I want to receive messages if a predefined error occurred, so that I can react to it. 
The errors are hardcoded and not changeable during runtime (only able to set parameters). 

Use-Cases: 
I want to be notified if motor 2 is dead but I do not care about the error detection, I just want to receive 
the message if the motor is dead. 

### Solution

The package `roboy_error_detection` ([https://github.com/CapChrisCap/roboy_error_detection](https://github.com/CapChrisCap/roboy_error_detection)) uses the 
`roboy_system_notification` package to publish errors. The `roboy_error_detection` provides you an API to 
subscribe to occurred errors (detected by patterns) in an easy way. 

### Example

```c++
int MOTOR_ID = 1;

RoboyErrorDetection handler = new RoboyErrorDetection();
handler.listenForDeadMotor(MOTOR_ID);
```

After that, a message will be published when the motor one is dead and you can 
receive it from the normal ROS topics of `roboy_system_notification` (routes depends of course on the log level). 

### API

#### listenForDeadMotor(int motorId, int logLevel=WARNING_LEVEL)

> Listen if the motor with the given id is dead. If the defined motor is really dead, a notification will be sent over ROS topic.

> * motorId id of the motor, which should be observed
> * logLevel message level of the published message, log levels are defined in 

### Limitations

The package was not yet tested and compiled and is not production ready. 
