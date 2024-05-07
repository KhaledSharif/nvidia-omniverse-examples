# nvidia-omniverse-examples
Examples of how to use NVIDIA Omniverse Isaac Sim for to solve Reinforcement Learning Games (RL-Games)

## Installation

Follow the Isaac Sim [documentation](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_workstation.html) to install the latest Isaac Sim release (2023.1.1)

To install `omniisaacgymenvs`, first clone this repository:

```bash
git clone https://github.com/KhaledSharif/nvidia-omniverse-examples.git
```

Once cloned, locate the [python executable in Isaac Sim](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_python.html). By default, this should be `python.sh`. We will refer to this path as `PYTHON_PATH`.

To set a `PYTHON_PATH` variable in the terminal that links to the python executable, we can run a command that resembles the following. Make sure to update the paths to your local path. For Linux: 

```bash
alias PYTHON_PATH=~/.local/share/ov/pkg/isaac_sim-2023.1.1/python.sh
```

Install the repository and its dependencies:

```bash
PYTHON_PATH -m pip install -e .
```

To run a simple form of PPO from `rl_games`, use the single-threaded training script:

```bash
PYTHON_PATH run.py task=Cartpole
```

The result is saved to the current working directory in a new directory called `runs`. For example, the saved pytorch checkpoint will be at:

```
runs/Cartpole/nn/last_Cartpole_ep_100_rew_491.48883.pth
```
