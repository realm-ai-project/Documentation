# Quick Start Guide 
## Brief Overview of Installation

To have the entire pipeline working, there are 5 main components to install:

- Unity Game Plugin
- RL Subsystem (`realm-tune`)
- Python GUI (`realm-gui`)
- Report Subsystem (`realm-report`)

The installation process for each of them are very straightforward, and are to be individually installed to facilitate flexibility to a user's needs.

For a more formal description of each of these subsystems, please refer them to their individual sections in this documentation.

## Installation Steps
### Installing ML-Agents
The REALM-AI tools are tightly integrated with Unity ML-Agents. As a result, it would be advisable to have Unity ML-Agents installed first, to ensure that installation of the following REALM-AI packages go as smoothly as possible.

To install Unity ML-Agents, please refer to their excellent [installation guide](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Installation.md#installation){:target="_blank"}.

### Unity Game Plugin
Since the installation process for the Unity Game Plugin is slightly more involved, we refer users to the installation guide provided as part of its documentation, [here](/game_plugin_subsystem/installation_unity).

### RL Subsystem (`realm-tune`)
To install the various tools bundled with the RL Subsystem, perform the following steps in a terminal:
```
git clone https://github.com/realm-ai-project/RL-Subsystem.git
cd RL-Subsystem
pip install -e .
```

### Python GUI (`realm-gui`)
To install the Python GUI, which is a custom-built UI that is tightly knitted with the Unity Game Plugin, perform the following steps in a terminal:
``` 
git clone https://github.com/realm-ai-project/Python-GUI.git
cd Python-GUI
pip install -e .
```

### Report Subsystem (`realm-report`)
The Report Subsystem is composed of a React frontend, and a Flask backend. These two components work closely with each other in order to generate and display heatmaps to the user. To install the `realm-report` tool, perform the following steps:
```
git clone https://github.com/realm-ai-project/Reporting-Subsystem.git
cd Reporting-Subsystem/api
pip install -e .
```