# Target-Tracking-for-Humanoids

# Implementation
Model Initialization, Control Algorithm, Least Squares Minimization, Rendering and Visualization, and Multi-Target Optimization.

# 1) Model Initialization:
We begin by initializing the model of the humanoid robot in the MuJoCo simulation environment. This involves loading an XML file that contains information about the robot’s physical properties, including joint constraints, actuator control ranges, and body dynamics. We modified the XML file from the MuJoCo documentation, adjusting the dimensions and color of the robot.

# 2) Control Algorithm: 
The reach() function defines the control algorithm used to optimize the robot's movements towards target positions. It starts by resetting the simulation to a predefined keyframe to ensure consistency for each optimization iteration. The function positions a target object within the simulation environment and extracts the initial and final control vectors from the ctrl0T parameter. These vectors guide the interpolation of intermediate control values throughout the optimization process. During the rollout phase, the function iterates over time steps, applying the interpolated control inputs to the robot model. The goal is to minimize the discrepancy between the desired and actual hand-target trajectories while considering actuator torques. The function also computes the residual between the robot's hand position and the target position, as well as the torque exerted by the actuators. If trajectory storage is enabled, the robot's state at each time step is saved for later analysis or visualization. Finally, residuals are normalized for consistent scaling across different rollout lengths.

# 3) Least Squares Minimization:
This technique is crucial for minimizing the residual between the robot's final state and the target position by adjusting control inputs. The optimization process iteratively adjusts the control inputs to minimize the squared differences between the robot's final state and the target position. The process evaluates control inputs against an objective function, refining them iteratively to minimize the residual error. This method's versatility makes it suitable for complex control problems with nonlinear constraints and objective functions. The least squares optimization is initiated using the minimize.least_squares() function from the scipy.optimize module. The function takes the target position, initial guess for control inputs, and bounds on the control inputs, iteratively adjusting them to minimize residual error and yield optimized control inputs stored in the x_optimal variable.

# 4) Rendering and Visualization: 
The render_solution() function visualizes the robot’s movements towards the target position using the optimized control inputs. The resulting frames are stored and compiled into a video, demonstrating the optimization outcome and the robot's trajectory towards the target.

# 5) Multi-Target Optimization: 
We implemented multiple targets for the robot to capture using its right hand, successfully obtaining the desired results.



# Conclusion
This project presents a comprehensive framework for controlling 
humanoid robots in the MuJoCo simulation environment. By defining the robot's physical 
characteristics and dynamics using XML representation, implementing control algorithms to 
optimize its movements towards target positions, and visualizing simulation results through 
rendering functions, we have created a platform for studying and controlling robotic behaviour. 
Leveraging the least squares optimization algorithm, we determined optimal control inputs to 
minimize the residual between the robot's state and target positions. Moreover, our project 
demonstrates adaptability to handle multiple targets. Through seamless integration of 
simulation, optimization, and visualization techniques, our project offers valuable insights into 
the design and optimization of robotic systems in virtual environments
