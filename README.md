
# PID Controller

Goal of this project was to 
- implement a PID controller for steering and speed of the car on a race track. 
- tune hyperparameters of both PID controllers so car stays within the borders of the track (does not touch border)

---
## Background
[Source: Wikipedia] A proportional–integral–derivative controller (PID controller) is a control loop feedback mechanism (controller) commonly used in industrial control systems. A PID controller continuously calculates an error value as the difference between a desired setpoint and a measured process variable and applies a correction based on proportional, integral, and derivative terms (sometimes denoted P, I, and D respectively) which give their name to the controller type.
Depending on the PID parameters a control output is generated  to steer the system closer to the setpoint. In the present project we have two PID controllers - one for steering and one for speed control.
In the steering PID controller, the car simulator produces the error signal as the distance between the actual car position on the road and a reference trajectory, known as cross-track error (cte). The PID controller is designed to minimize the distance to this reference trajectory. The primary control output of the PID controller here is the steering angle. 
In the speed PID controller, the car simulator produces the error signal as the difference between the actual speed and the reference speed (set fix but can be optimized to be more dynamic, e.g. relating to steering angle.

### Hypermarameter - tuning
All parameters were tuned manually as outlined below for the individual Kp, Kd and Ki respectively. More automated tuning algorithms such as Twiddle can be used but it worked without as well. In general:

1. single P controller with K_i and K_d = 0
2. increase K_d until oscillations decrease. 
3. in case of crashes: find cause.
   a) if slow reactivity is the cause -> reduce steering angle smoothing, increase K_p or K_i
   b) if oscillations are the cause -> reduce K_p, K_i or brake 

### Hyperparameters - Kp
The proportional part of the controller is responsible to quickly react to any "error" between current and desired state. Initially my parameter for Kp was too high bringing the car to an oscillation that quickly brought it out of track. Tuning the parameter I ended up quickly with a value around 0.01



### Hyperparameters - Kd
The derivative part of the controller is responsible to reduce the oscillation implied by the proportional part and as a result "smooth" the control result. Initially I started without a Kd parameter but given that my car oscillated I eded up with a value around 0.0001



### Hyperparameters - Ki
The integral part of the controller is responsible to cater for any "static" steering errors or to make the controller react quicker in higher-speed environments. I set the initial value at 4 based on the lectures and slightly reduced it during the parameter tuning ending up with a value around 3.0
