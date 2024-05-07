## Reinforcement Learning Environments

```python
class VecEnvBase(
    headless: bool, 
    sim_device: int = 0, 
    enable_livestream: bool = False, 
    enable_viewport: bool = False, 
    launch_simulation_app: bool = True, 
    experience: Optional[str] = None
)
```

- VecEnvBase: A base class that provides an interface for connecting RL policies with task implementations, following the gym.Env interface. It handles simulation initialization, task registration, and basic environment interactions like reset, step, and render.
- TaskStopException: An exception class used to signal task termination.
- TrainerMT: An abstract base class for controlling the start and stop of an RL policy.
- VecEnvMT: A multi-threaded environment wrapper that separates the RL policy execution and simulation tasks into different threads, enabling interaction with the UI during RL training. It uses message queues for inter-thread communication, managing the flow of actions from the policy to the task, and data from the task to the policy.

The code provides methods for setting up the simulation environment, initializing tasks, stepping through the simulation, rendering, resetting the environment, and handling actions and observations. It supports both single-threaded and multi-threaded modes of operation, with the multi-threaded mode allowing for UI interaction during training.