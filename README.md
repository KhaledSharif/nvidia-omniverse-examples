# nvidia-omniverse-examples
Examples of how to use NVIDIA Omniverse Isaac Sim for Robotic Synthetic Data Generation (SDG)

## System Requirements

It is recommended to have at least 32GB RAM and a GPU with at least 12GB VRAM. For detailed system requirements, please visit the [Isaac Sim System Requirements](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/requirements.html#system-requirements) page. Please refer to the [Troubleshooting](docs/troubleshoot.md#memory-consumption) page for a detailed breakdown of memory consumption.

## Installation

Follow the Isaac Sim [documentation](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_workstation.html) to install the latest Isaac Sim release. 

*Examples in this repository rely on features from the most recent Isaac Sim release. Please make sure to update any existing Isaac Sim build to the latest release version, 2023.1.1, to ensure examples work as expected.*

Once installed, this repository can be used as a python module, `omniisaacgymenvs`, with the python executable provided in Isaac Sim.

To install `omniisaacgymenvs`, first clone this repository:

```bash
git clone https://github.com/KhaledSharif/nvidia-omniverse-examples.git
```

Once cloned, locate the [python executable in Isaac Sim](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_python.html). By default, this should be `python.sh`. We will refer to this path as `PYTHON_PATH`.

To set a `PYTHON_PATH` variable in the terminal that links to the python executable, we can run a command that resembles the following. Make sure to update the paths to your local path. For Linux: 

```bash
alias PYTHON_PATH=~/.local/share/ov/pkg/isaac_sim-2023.1.1/python.sh
```

To run a simple form of PPO from `rl_games`, use the single-threaded training script:

```bash
PYTHON_PATH ./omniisaacgymenvs/scripts/rlgames_train.py task=Cartpole
```

This script creates an instance of the PPO runner in `rl_games` and automatically launches training and simulation. Once training completes (the total number of iterations have been reached), the script will exit. If running inference with `test=True checkpoint=<path/to/checkpoint>`, the script will run indefinitely until terminated. Note that this script will have limitations on interaction with the UI.
