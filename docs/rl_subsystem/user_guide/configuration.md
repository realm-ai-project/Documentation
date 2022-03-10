In this section, we will be going through the two main ways to interact with the `realm-tune` tool.

## Configuration file
Below is an example config file that contains all possible configurations (don't worry, its not a lot!). 

```yaml
realm_ai:
  algorithm: bayes # or random
  total_trials: 3 # total number of trials (inclusive of warmup_trials)
```

To start, create a `.yaml` file with any name you would like, copy the following code block and paste it in the newly created `.yaml` file.

## Cli arguments
The purpose of having cli arguments in conjunction of the configuration file is mainly for convenience, especially when `realm-tune` is interacted with programatically from other tools. For instance, it can be a hassle to parse the config file, save the config file, and then point `realm-tune` to it. 

One important thing to note is that arguments passed through the cli args **always takes precedence** over those through the config files. In other words, arguments passed through the cli always overrides those in the config file. This allows a user to say, have a fixed config file that they are comfortable with, and override them through the cli everytime they have a different game etc.

To get the list of available cli arguments, do `realm-tune --help`, the output of which should look something like:
```
usage: realm-tune [-h] [--config-path CONFIG_PATH] [--output-path OUTPUT_PATH]
                  [--behavior-name BEHAVIOR_NAME] [--algorithm {bayes,random,grid}]
                  [--total-trials TOTAL_TRIALS] [--warmup-trials WARMUP_TRIALS]
                  [--eval-window-size EVAL_WINDOW_SIZE] [--env-path ENV_PATH] [--use-wandb]
                  [--wandb-project WANDB_PROJECT] [--wandb-entity WANDB_ENTITY] [--wandb-offline]
                  [--wandb-group WANDB_GROUP] [--wandb-jobtype WANDB_JOBTYPE] [--full-run]
                  [--full-run-max-steps FULL_RUN_MAX_STEPS]

Realm_AI hyperparameter optimization tool

optional arguments:
  -h, --help            show this help message and exit
  --config-path CONFIG_PATH
  --output-path OUTPUT_PATH
                        Specify path where data is stored
  --behavior-name BEHAVIOR_NAME
                        Name of behaviour. This can be found under the agent's "Behavior Parameters"
                        component in the inspector of Unity
  --algorithm {bayes,random,grid}
                        Algorithm for hyperparameter tuning
  --total-trials TOTAL_TRIALS
                        Number of trials
  --warmup-trials WARMUP_TRIALS
                        Number of warmup trials (only works for bayes algorithm)
  --eval-window-size EVAL_WINDOW_SIZE
                        Training run is evaluated by taking the average eps rew of past x episodes
  --env-path ENV_PATH   Path to environment. If specified, overrides env_path in the config file

Weights and Biases Configuration:
  --use-wandb
  --wandb-project WANDB_PROJECT
  --wandb-entity WANDB_ENTITY
  --wandb-offline
  --wandb-group WANDB_GROUP
  --wandb-jobtype WANDB_JOBTYPE

Full run configuration:
  --full-run
  --full-run-max-steps FULL_RUN_MAX_STEPS
```

All arguments should look pretty familiar as they are mostly identical to those from the config file. However, the only two noteworthy arguments to point out are:

- `--use-wandb` exists because it allows the user to use Weights and Biases without requiring passing in any other information, such as the entity name.

- `--full-run` exists for the exact same reason. It allows the user to do an automated full training run after hyperparameter tuning, without the need to configure the number of steps (the default value will be used instead).