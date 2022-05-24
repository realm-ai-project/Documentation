## Using it as a standalone wrapper for ML-Agents
In this mode, users should interact with `wandb-mlagents-learn`, which acts as a wrapper passthrough for `mlagents-learn`.

To use WandB with ML-Agents, simply add an extra "wandb" field in a config file that is otherwise completely compatible with ML-Agents Python package. To run, enter `wandb-mlagents-learn` in the terminal. This wrapper accepts the same cli arguments as `mlagents-learn`. 

**Note**: In this use case, `wandb-mlagents-learn` does not support cli arguments. In other words, to use this wrapper, WandB's configurations must be present in a `mlagents-learn` compatible config file. The syntax for the various configs can be found [below](#wandb-mlagents-learn-configs).

## Using it with `realm-tune`
In this mode, users interact solely through `realm-tune`, as they have been tightly integrated.  

To use WandB with `realm-tune`, similar to previously, simply add an extra "wandb" field to the `realm-tune` config file. An example of which can be found [here](../realm-tune/configuration.md#configuration-file).

Comparing to using `wandb-mlagents-learn` as a standalone, using it within `realm-tune` allows cli arguments to be passed (more information can be found in [`realm-tune`'s config docs](../realm-tune/configuration.md#cli-arguments)).

## `wandb-mlagents-learn` configs
In the `realm-tune` or `mlagents-learn` config file (it should be a `*.yaml` file), add the following:  

```yaml
wandb:
    project: <default: realm_ai>
    entity: <default: None>
    offline: <default: False>
    group: <default: None>
    jobtype: <default: None> # "job_type" is accepted too! 
```
 
## Notes
- Resuming a run on wandb does not work (yet). Since we use the run_id as the name of the wandb run, we will see multiple runs with the same name when resuming a run
- If we intend to use mlagents default parameters, it is okay to pass in a config file that solely contains wandb config (as shown above)
- If "wandb" is not defined in the config file, wandb will not be used, and functionality will then be identical to mlagents!
- When resuming runs, multiple tensorboard files may be present. Currently, this wrapper uses the latest tensorboard file, based on time of creation (Windows)/last modification (Unix)