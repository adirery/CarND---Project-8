# PID Controller

Goal of this project was to 
- implement a PID controller for steering and speed of the car on a race track. 
- tune hyperparameters of both PID controllers so car stays within the borders of the track (does not touch border)

Hyperparameters - Kp

The proportional part of the controller is responsible to quickly react to any "error" between current and desired state. Initially my parameter for Kp was too high bringing the car to an oscillation that quickly brought it out of track. Tuning the parameter I ended up quickly with a value around 0.01

Hyperparameters - Kd

The derivative part of the controller is responsible to reduce the oscillation implied by the proportional part and as a result "smooth" the control result. Initially I started without a Kd parameter but given that my car oscillated I eded up with a value around 0.0001

Hyperparameters - Ki

The integral part of the controller is responsible to cater for any "static" steering errors or to make the controller react quicker in higher-speed environments. I set the initial value at 4 based on the lectures and slightly reduced it during the parameter tuning ending up with a value around 3.0
