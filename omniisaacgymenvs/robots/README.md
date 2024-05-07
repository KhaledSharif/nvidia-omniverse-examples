## Reinforcement Learning Robots

The Robot class provides a common interface for creating and managing robot articulations in the Isaac Sim simulation environment. It allows for configuring various properties, such as position, orientation, scale, visibility, and articulation controller. It also provides methods for applying actions (joint positions, velocities, and efforts), applying visual materials, handling gravity, and retrieving information about the robot's state, articulation bodies, and applied actions.

### Constructor Parameters

prim_path: The path of the Prim (Primitive) to encapsulate or create.
name: A shortname to be used as a key by the Scene class. It needs to be unique if the object is added to the Scene.
position: The position in the world frame of the Prim. Shape is (3,).
translation: The translation in the local frame of the Prim (with respect to its parent Prim). Shape is (3,).
orientation: The quaternion orientation in the world/local frame of the Prim (depends on whether translation or position is specified). The quaternion is scalar-first (w, x, y, z). Shape is (4,).
scale: The local scale to be applied to the Prim's dimensions. Shape is (3,).
visible: A boolean indicating whether the Prim should be visible in the stage during rendering.
articulation_controller: A custom ArticulationController that inherits from the base ArticulationController class. If not provided, a basic ArticulationController is created.


### Properties

articulation_handle: A handler to the articulation, which is a unique identifier used by the Dynamic Control extension to manage the articulation.
dof_names: A list of Prim names for each degree of freedom (DoF).
dof_properties: A NumPy array containing the properties of the articulation DoFs, such as type, limits, drive mode, maximum velocity and effort, stiffness, and damping.


### Methods

apply_action: Applies joint positions, velocities, and/or efforts to control the articulation.
apply_visual_material: Applies a visual material (e.g., PreviewSurface, OmniPBR, OmniGlass) to the Prim and optionally its descendants.
disable_gravity: Keeps gravity from affecting the robot.
enable_gravity: Allows gravity to affect the robot.
get_angular_velocity: Gets the angular velocity of the root articulation Prim.
get_applied_action: Gets the last applied action (joint positions, velocities, and efforts).
get_applied_joint_efforts: Gets the efforts applied to the joints set by the set_joint_efforts method.
get_applied_visual_material: Returns the currently applied visual material, if supported.
get_articulation_body_count: Gets the number of bodies (links) that make up the articulation.
get_articulation_controller: Gets the articulation controller.
get_default_state: Gets the default Prim states (spatial position and orientation).
