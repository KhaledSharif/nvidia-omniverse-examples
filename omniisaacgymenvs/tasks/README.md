## Reinforcement Learning Tasks

### FrankaCabinetTask

This code defines a class FrankaCabinetTask which is derived from the RLTask class. It is designed to simulate a robotic task where a Franka robot arm interacts with a cabinet by opening its drawer. The task involves the robot arm grasping the handle of the drawer and pulling it open.
Here's a breakdown of the key components:

- Initialization: The __init__ method sets up various parameters and configurations related to the task, such as the number of environments, episode length, reward scales, and action scales.
- Scene Setup: The set_up_scene method creates instances of the Franka robot arm and the cabinet in the simulation environment. It also initializes views for rendering the scene and initializes the data required for the task.
- Observations: The get_observations method computes the observations for the task, which include the joint positions and velocities of the robot arm and the cabinet, as well as the positions and orientations of the robot's gripper and the drawer handle.
- Physics Step: The pre_physics_step method updates the target joint positions of the robot arm based on the actions received from the reinforcement learning agent.
- Reset: The reset_idx method resets the environment by resetting the positions and velocities of the robot arm and the cabinet, as well as the positions of any props (optional objects) in the scene.
- Reward Calculation: The compute_franka_reward method calculates the reward for the current state of the task. The reward is based on various factors, such as the distance between the robot's gripper and the drawer handle, the alignment of the gripper with the drawer, the distance of the robot's fingers from the drawer, the action penalty, and the degree to which the drawer is open.
- Episode Termination: The is_done method checks if the episode should be terminated based on whether the drawer is fully open or if the maximum episode length has been reached.
Helper Functions: The code includes several helper functions for computing grasp transforms, transformations between coordinate systems, and clamping tensor values.

The code is designed to be used with the Isaac Gym simulation environment, which is a physics simulation platform for training and evaluating robotic tasks using reinforcement learning. The FrankaCabinetTask class can be integrated into the Isaac Gym environment to simulate and train a reinforcement learning agent to perform the task of opening a cabinet drawer using a Franka robot arm.

The get_observations method in the FrankaCabinetTask class is responsible for computing the observations that will be used by the reinforcement learning agent to make decisions. The observations represent the state of the environment, which includes the positions and orientations of various components, such as the Franka robot arm, the cabinet drawer, and the robot's fingers.
Here's a breakdown of what the get_observations method does:

- Get Poses: The method retrieves the world poses (positions and orientations) of the robot's hand, the cabinet drawer, and the robot's fingers using the FrankaView and CabinetView classes.
- Get Joint Positions and Velocities: It also retrieves the joint positions and velocities of the Franka robot arm and the cabinet drawer using the corresponding views.
- Compute Grasp Transforms: The method computes the grasp transforms for the robot's gripper and the drawer handle. These transforms represent the local position and orientation of the grasp point relative to the hand and drawer, respectively. The compute_grasp_transforms function is called to compute these transforms based on the retrieved poses and predefined local grasp poses.
- Scale Joint Positions: The joint positions of the Franka robot arm are scaled to a range of [-1, 1] using the defined lower and upper limits for each joint.
- Compute Additional Observations: Additional observations are computed, such as the vector pointing from the robot's gripper to the drawer handle, the joint position and velocity of the cabinet's top drawer joint, and the scaled joint velocities of the Franka robot arm.
- Construct Observation Buffer: All the computed observations are concatenated into a single tensor called obs_buf, which represents the complete observation for the current state of the environment.
- Return Observations: The obs_buf tensor is returned as part of a dictionary, where the key is the name of the robot view ("franka_view"), and the value is another dictionary containing the obs_buf tensor.

The observations computed in this method are essential for the reinforcement learning agent to perceive the current state of the environment and make informed decisions about the actions to take. These observations will be processed by the agent's neural network or other decision-making mechanism to determine the next action to perform in the task of opening the cabinet drawer.