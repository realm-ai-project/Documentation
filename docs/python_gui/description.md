The Python GUI acts as a bridge to connect the Game Plugin Subsystem with the RL Subsystem. It provides an interface for the user to accomplish 2 tasks:

- Start barebones Ml-Agents Training
- Start Hyperparameter Tuning and use the new tuned values to start Ml-Agents Training

![screenshot](images/home_screen.png)

## Basic Ml-Agents Training
![screenshot](images/ml_agents.png)
The first use case of the Python GUI is to start basic Ml-Agents Training. Users will have the option to configure different settings to suit their training requirements. There are 3 buttons at the bottom that can be clicked. They can:

- Restore Default Values
- Save the Ml-Agents Configuration file
- Start Ml-Agents training and select which configuration file they would like to use

Please refer to the user guide for a step by step workflow.

## Hyperparameter Tuning and Effective Ml-Agents Training
![screenshot](images/hyperparameter_tuning.png)
The second use case of the Python GUI is to start hyperparameter tuning and then Ml-Agents training. The result of the hyperparameter tuning is an optimized Ml-Agents configuration file. Once the hyperparameter tuning is done, Ml-Agents training is automatically ran with the optimized configuration file. 

There is a difference between the two options. Simply put, the first option is to just train. The basic Ml-Agents training runs the configuration file supplied by the user. The second option is to find the best parameters for training (this process is known as tuning) and then train. The Hyperparameter Tuning and Effective Ml-Agents Training will find the optimized values for Ml-Agents training to produce the best results. Note that this option will take significantly longer. 

There are 3 buttons at the bottom that can be clicked. They can:

- Restore Default Values
- Save the Hyperparameter Configuration file
- Start Hyperparameter Tuning and Training

Please refer to the user guide for a step by step workflow.