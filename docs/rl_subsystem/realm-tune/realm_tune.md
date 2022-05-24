<!-- This section describes the steps required to get up and running with the hyperparameter optimization tool. The following subsections go according to the sequence of steps. -->
REALM_AI's RL hyperparameter optimization tool focuses on configurability and simplicity to use. There are 3 main steps required to use the tool: [build the environment](#building-the-environment), [edit the configuration file](#edit-the-configuration-file), and finally [run the training procedure](#starting-the-training-procedure).

## Building the Environment
The first step is to build the Unity ML-Agents compatible environment into an executable. ML-Agents' documentation contains a [comprehensive guide](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Learning-Environment-Executable.md){:target="_blank"} that details a step-by-step guide to export the environment as an executable. 
<!-- Todo: add hyperlink to game plugin for automatic building -->

## Editing the Configuration File
In order to make the tool as simple to use as possible, all settings reside within a single `.yaml` file. There are 2 main components in the configuration file -- configurations for the REALM_AI RL_Subsystem's hyperparameter optimizer, and configurations for ML-Agents.

### REALM_AI Configuration
There are two main ways to interact with 

### ML-Agents Configuration
Note that we aren't doing any checking for the mlagents config portion

Also note that log_unif and unif exclude upper bound

#### Training configuration

#### Hyperparameters

##### Why the unconventional syntax for the hyperparameters?
(To keep the yaml file concise, reduce verbosity that comes from yaml's syntax) Since 

##### Syntax

### Sample Configuration File

## Starting the Training Procedure

## Caveats
### Single behavior only
The current setup assumes single-player game that contains a single behavior. Games with multiple behaviours would not work with the current script. However, due to the simplistic nature of the script, adding support for multi-agent environments is not difficult.