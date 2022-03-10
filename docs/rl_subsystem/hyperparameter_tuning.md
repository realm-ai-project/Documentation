## What Are Hyperparameters?
In machine learning, hyperparameters are parameters whose values are used to control the learning process. In other words, hyperparameters directly affect the result of the learned parameters. As a result, hyperparameters are not learned during the training process. Instead, hyperparameters are usually set before training, and the set of optimal hyperparameters are usually chosen empirically through a process of trial and error. This process is called *hyperparameter tuning/optimization*. 

### Examples of Hyperparameters for Reinforcement Learning
Some common hyperparameters include batch size, learning rate, exploration-related hyperparameters (e.g., epsilon), etc. For a more comprehensive list of hyperparameters available for various algorithms provided by Unity's ML-Agents package, please refer to [here](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Training-Configuration-File.md){:target="_blank"}.

## Why Automate the Hyperparameter Tuning Process?
While it is possible to manually tune hyperparameters through trial and error, this process is mundane and very expensive given the usually long training times. This process is worsen by the need for domain knowledge in order to know which hyperparameter to tune, and the scale to tune them by.

## Common Hyperparameter Optimization Algorithms 
There are a few dominant algorithms that are commonly used to automate the process of tuning the hyperparameters. This is namely Grid Search, Random/Uninformed Search, and Bayesian methods such as the Tree-structured Parzen Estimator (TPE) algorithm. Realm-tune currently supports all of them.

To get started on how to automatically tune hyperparameters with REALM_AI, head to the [user guide](user_guide.md).