# Notification Module Messages

For the notification module, the definition of the ROS messages is required. Therefore, 
I defined the following messages to ensure that the notification module can be used for 
mostly all required system notifications. It is now able to send `Debug`, `Info`, `Error`, `Danger`
and `Warning` messages. For all of these message kinds, a special message format was introduced and 
modeled in the [roboy_communication module](https://github.com/CapChrisCap/roboy_communication/tree/master/roboy_communication_control/msg). 