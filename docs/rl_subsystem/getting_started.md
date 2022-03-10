**Note:** This quick start guide is only applicable for using this RL Subsystem as a standalone. If using in conjunction with the REALM_AI's game plugin, the below steps are already automated for you.

## Building the environment
The first step is to build a ML-Agents compatible Unity environment, and *build it into an executable*. [Here](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Learning-Environment-Create-New.md){:target="_blank"} is a tutorial of building a Unity ML-Agents compatible environment from the official ML-Agents documentation. 

Remember where the path of the executable is, because we will need to use it in the later steps!

## Installing REALM_AI's RL-Subsystem
In terminal, enter the following commands to pull and setup the python package (e.g., install the necessary dependencies).

1. `git clone git@github.com:realm-ai-project/RL-Subsystem.git`

2. `cd RL-Subsystem`

3. `pip install -e .`

## Training
While what makes `realm-tune` powerful is its configurability, to get started it is as simple as performing the following command in the terminal:

```realm-tune --env-path <env_path>```

where `<env_path>` is replaced with the path to the unity executable built above.

If you see a lot of output to the console, it means the program is working as expected! You may see a tiny game window show up from time to time, and that is to be expected!

If you wait for a while, the program will eventually be completed, and all training outputs will be stored at `runs/RealmTune_xx-xx-xxxx_xx-xx-xx`, where the `x` represents a datetime stamp so that your training outputs are always easily recognizable. Congrats, you have tuned your first agent!


## Learn More
There are much more that `realm-tune` can do that will be covered in the subsequent pages, such as 

- configuring hyperparameters to tune over 

- picking the hyperparameter tuning algorithms 

- integrate with Weights and Biases with `wandb-mlagents-learn`

- automatically initiate the full training run after the hyperparameter tuning stage, using the best set of hyperparameters

- many more