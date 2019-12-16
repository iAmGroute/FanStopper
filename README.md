# Fan Stopper
A simple circuit to turn a fan completely off instead of having it spin slowly.

When your pc's temperature is relatively low, the motherboard (usually) reduces the speed of the fans.  
Some motherboards have an option to turn the fans off completely, if the temperature is low enough. However, that is not very common.  
This circuit is used to add such functionality to motherboards that don't have it.  
It detects the voltage (or pwm signal) and if it is below the threshold that you set with the potentiometer, it cuts power to the fan, thus making it stop and not use any power. That also means the fan stays completely silent, producing no noise at all.  
If the voltage (or pwm signal) is above the threshold, it passes that transparently to the fan, thus turning it on and letting the motherboard control its speed.  

In short, the Fan Stopper acts like a switch that is OFF when the intended fan speed is too 'low' (you determine what speed that is), and ON otherwise.  
There is a small margin between the voltages at which it turns on and off (hysteresis) to prevent the fan from constantly switching on and off in a short amount of time.  

Revision `Rev0A` accomplices this using a `431` programmable voltage reference in an open loop configuration, while revision `0B` uses an analog comparator, in order to reduce the quiescent current used by the `431` and reduce the variations caused by the significantly wide input voltage range (`4~13 V`).

### Instructions

Let your pc idle for a while, to reach the temperatures you will consider low enough for the fans to turn off.  
The speed at which the fans are currently running is the speed at which you will set them to turn off.  
Disconnect a fan from the motherboard, then plug it into the Fan Stopper and finally connect the Fan Stopper to the motherboard.  
Turn the potentiometer clockwise all the way, so that the fan turns on (its speed will be determined by the motherboard).  
Then, turn the potentiometer slowly counterclockwise, until the fan turns off.  
Repeat this for all the fans you want to turn off (1 Fan Stopper per fan).  

To verify that everything is working, try running a stress test for quite some time, in order to raise the pc's temperature.  
The fans should start spinning again.  
After you stop the test, when the pc is idle and the temperature is back to low levels, the fans should stop spinning.  
(if not, try turning the potentiometer counterclockwise very slightly)  
