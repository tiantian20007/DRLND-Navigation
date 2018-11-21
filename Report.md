# Method

## Algorithm
We use typical Deep Q-Learning with Experience Replay and Fixed Q-Targets to train our agent.
The algorithm is implemented in dqn_agent.py and the dqn function in Navigation.ipynb. 

## model architectures
We use a DNN contains 5 hidden layers, and each one of them has 128 neuron units. We choose relu as the activate function. The mode is implemented in model.py. 

## Hyperparameters

- max episode count=2000
- max step in ech episode =1000
- eps_start=1.0
- eps_end=0.01
- eps_decay=0.995

# Rewards

![alt text](https://github.com/tiantian20007/DRLND-Navigation/blob/master/res/result.png "Logo Title Text 1")





# Future Work

- [Double DQN (DDQN)](https://arxiv.org/abs/1509.06461)
- [Prioritized Experience Replay](https://arxiv.org/abs/1511.05952)
- [Dueling DQN](https://arxiv.org/abs/1511.06581)

Researchers at Google DeepMind recently tested the performance of an agent that incorporated all six of these modifications. The corresponding algorithm was termed [Rainbow](https://arxiv.org/abs/1710.02298).
It outperforms each of the individual modifications and achieves state-of-the-art performance on Atari 2600 games!
