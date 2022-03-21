In this section, we will be going through the two main ways to interact with the `realm-tune` tool.

## Configuration file
Below is an example config file that contains all possible configurations, alongside comments that describe the fields. 

```yaml
realm_ai:
  behavior_name: 3DBallHard # optional
  algorithm: bayes # or random, optional, default: bayes
  total_trials: 3 # total number of trials (inclusive of warmup_trials), optional, default: 5
  warmup_trials: 5 # optional for bayes algorithm, number of "warmup" trials where random hyperparams are used. Ignored for other algorithms. Default val is 5
  eval_window_size: 1 # optional, training run is evaluated by taking the average eps rew of past x episodes. Default val is 1
  env_path: ../../../Unity/envs/my_game/env # mandotary! Either specify here, or under env_path settings below. Setting here takes precedence.
  output_path: ../../custom_output_path # optional, specify to manually specify folder name, or to continue running
  full_run_after_tuning: # optional, if specified, config in "best_trial" folder will be changed to reflect the following settings(i.e., max_steps). Leave it out if no training is to be done after tuning. 
    max_steps: 20000 # number of steps to run for the full training
  wandb: # optional, if specified, log training metrics to wandb. Leave it out if wandb is not to be used.
    project: realm_tune 
    entity: <username>
    offline: false 

mlagents: # Fully compatible with all single-agent mlagents config. Must use default_settings for hyperparameters!
  env_settings:
    # env_path: ../../../../../Unity/envs/3dball/3dball # precedence given to env_path above
    env_args: null
    num_envs: 1
    seed: 0

  engine_settings:
    no_graphics: true
  
  # checkpoint_settings: 
  #   run_id: anything # does not matter, will be generated automatically
  #   force: false # does not matter, overwritten as True through cli argument

  torch_settings:
    device: cpu

  default_settings:
    trainer_type: ppo
    hyperparameters:
      batch_size: [64, 128, 256] # Means categorical
      buffer_size: log_unif(2000, 12000) # Automatic detection as int
      learning_rate: log_unif(0.0003, 0.01) # Automatic detection as float
      beta: log_unif(0.001, 0.01) # unif and log_unif exclude upper bound - [0.001, 0.01)
      num_epoch: unif(1, 15)
    reward_signals:
      extrinsic:
        gamma: [0.99, 0.95]
    max_steps: 10000
    time_horizon: 1000
    summary_freq: 5000
```

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