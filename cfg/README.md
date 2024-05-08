## Reinforcement Learning Configuration

### What is Hydra?

Hydra is an open-source Python framework that simplifies the development of research and other complex applications. The key feature is the ability to dynamically create a hierarchical configuration by composition and override it through config files and the command line.

### What is ./config.yaml?

- Task Configuration: This section specifies the task name, experiment name, the number of environments to use for training, the random seed, and whether to use deterministic PyTorch operations.
- Device Configuration: This section configures the physics engine (PhysX), the pipeline (CPU or GPU), the device to be used for simulation (CPU or GPU), the device for running the RL algorithm, and whether to enable multi-GPU training.
- PhysX Arguments: This section sets the number of worker threads and the solver type for the PhysX physics engine.
- RL Training Arguments: These arguments control various aspects of the RL training process, such as running in test mode, loading a checkpoint, evaluation mode, headless rendering, live streaming, timeout settings, recording settings (e.g., interval, length, FPS, directory), and wandb (Weights & Biases) integration for logging and monitoring.
- Default Settings: This section sets the default task and training configuration based on the specified task (in this case, Cartpole).
Hydra Configuration: This section configures the output directory for the training logs and results using the Hydra configuration management framework.

### What is ./task/*.yaml?

- Environment Settings: This section defines the number of parallel environments, episode length, observation and action clipping, control frequency, noise in initial conditions, number of props, aggregation mode, and reward scales for different objectives (e.g., distance, rotation, finger positions).
- Simulation Settings: This section configures the simulation parameters, such as time step, gravity, ground plane, lighting, fabric usage, and whether to use GPU acceleration. It also sets the default physics material properties (friction, restitution).
- Physics Engine Settings: These settings are specific to the PhysX physics engine, including worker thread count, solver type, GPU usage, solver iteration counts, contact offsets, bounce thresholds, friction parameters, sleeping and stabilization settings, and GPU buffer capacities.
- Object-Specific Settings: These sections override specific parameters for individual objects or actors within the environment, such as the robot arm (e.g., Franka), cabinets, and props. These settings include enabling self-collisions, gyroscopic forces, solver iteration counts, sleep and stabilization thresholds, density, maximum depenetration velocity, and shape-specific parameters like contact and rest offsets.

### What is ./train/*.yaml?

Params: This section contains the main parameters for the RL algorithm and neural network architecture.

- seed: Random seed value for reproducibility.
- algo: The algorithm to be used, in this case, a2c_continuous (Advantage Actor-Critic for continuous actions).
- model: The model type, typically continuous_a2c_logstd for continuous action spaces.
- network: Configuration for the neural network architecture, including the type (actor-critic), activation functions, initialization methods, and layer sizes.


Load Checkpoint: Parameters related to loading a pre-trained model checkpoint.

- load_checkpoint: A flag to determine whether to load a checkpoint or not.
- load_path: The path to the checkpoint file to be loaded.


Config: This section contains various configuration settings for the training process.

- name: The name of the experiment or environment.
- full_experiment_name: The full name of the experiment.
- env_name: The name of the environment to be used (in this case, rlgpu).
- device: The device to be used for training (e.g., CPU or GPU).
- multi_gpu: A flag to enable multi-GPU training.
- ppo: A flag to indicate that PPO is being used.
- mixed_precision: A flag to enable mixed-precision training (useful for GPU acceleration).
- normalize_input, normalize_value, normalize_advantage: Flags for normalizing input, value, and advantage estimates.
- num_actors: The number of parallel environments to run.
- reward_shaper: Configuration for reward scaling.
- gamma, tau: Discount factors for future rewards.
- learning_rate, lr_schedule: Learning rate and its scheduling strategy.
- kl_threshold: The KL divergence threshold for adaptive KL penalty in PPO.
- score_to_win: The target score to consider the task as solved.
- max_epochs, save_best_after, save_frequency: Parameters for training duration and checkpointing.
- grad_norm, entropy_coef, truncate_grads, e_clip: Gradient-related parameters and entropy regularization.
- horizon_length, minibatch_size, mini_epochs: Parameters for batching and optimization.
- critic_coef, clip_value, seq_length, bounds_loss_coef: Additional parameters for the critic and bounding loss.