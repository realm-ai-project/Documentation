## Features

### Pause and resume 
`realm-tune` can be paused and resumed. To pause, an interrupt signal can be sent to the process (e.g., ctrl+c in the terminal). The key to enable `realm-tune` to properly resume is to ensure that the `output_path` is pointed to the directory where the previous runs were saved. By default, the output directory will have resemblance to the following: `<some_path>/runs/RealmTune_xx-xx-xxxx_xx-xx-xx`.

The `output_path` variable can be set through the cli args (i.e., `--output-path`) or through the config file (see [realm-tune's config documentation](configuration.md)) 

**Note**: This feature works on Linux and MacOS, but on Windows due to the way they handle interrupts, the process may not pause properly. Therefore, we recommend users to use `realm-tune` with WSL on Windows. 

### Automatically running full training with best hyperparameters

Due to the computational cost of performing hyperparameter tuning on non-trivial games, we recommend users to reduce the number of training steps per tuning trial, but instead increase the number of tuning trials so that chances of finding a good hyperparameter space is maximized as much as possible. 

As such, `realm-tune` has the ability to automatically initiate a larger run (i.e., more training steps) once all hyperparameter tuning runs have been completed. In this case, `realm-tune` will use the hyperparameters from the best tuning trial to perform the full training.  

This can be configured through the cli args (e.g., `--full-run --full-run-max-steps n` where `n` is the number of training steps for the full run) or through the config file. 

**Note**: The full training run can also be paused and resumed.

## Limitations
- Does not support multiplayer environments (i.e., environments with >1 behaviour(s)). `realm-tune` automatically checks for this in the [code](https://github.com/realm-ai-project/RL-Subsystem/blob/12e9d688fa1458521bdab95c8d3c9dcb29796662/realm_tune/settings.py#L295){:target="_blank"}, so the program will error out on multiplayer environments.

- Does not support in-editor training, must be trained on a build. 