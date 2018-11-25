# Method

## Algorithm
We use typical Deep Q-Learning with Experience Replay and Fixed Q-Targets to train our agent.
The algorithm is implemented in dqn_agent.py and the dqn function in Navigation.ipynb.

### Traditional Q-Learning
![alt text](https://github.com/tiantian20007/DRLND-Navigation/blob/master/res/Q-learning.png "Traditional Q-Learning")

### DNN
We use a deep neural networks as the proximation for the Q functions instead of the tradition Q table.

### Experience Replay
When the agent interacts with the environment, the sequence of experience tuples can be highly correlated. The naive Q-learning algorithm that learns from each of these experience tuples in sequential order runs the risk of getting swayed by the effects of this correlation. By instead keeping track of a replay buffer and using experience replay to sample from the buffer at random, we can prevent action values from oscillating or diverging catastrophically.

The replay buffer contains a collection of experience tuples (_S_, _A_, _R_, _S'_). The tuples are gradually added to the buffer as we are interacting with the environment.

The act of sampling a small batch of tuples from the replay buffer in order to learn is known as experience replay. In addition to breaking harmful correlations, experience replay allows us to learn more from individual tuples multiple times, recall rare occurrences, and in general make better use of our experience.

### Fixed Q-Targets
In Q-Learning, we update a guess with a guess, and this can potentially lead to harmful correlations. To avoid this, we can update the parameters w in the network q^ to better approximate the action value corresponding to state _S_ and action _A_ with the following update rule:
![alt text](https://github.com/tiantian20007/DRLND-Navigation/blob/master/res/fix-target.png "Fixed Q-Targets")

where w<sup>-</sup> are the weights of a separate target network that are not changed during the learning step, and (_S_, _A_, _R_, _S'_) is an experience tuple.
 

## Model architectures
First we tried a DNN contains 5 hidden layers, and each one of them has 128 neuron units. We choose relu as the activate function. The model trained long time, and yield a result satisfied our needs. Then we tried a simpler model with just only two hidden layers and also got satisfied result with much less time. 
The mode is implemented in model.py. 

## Hyperparameters

- max episode count=2000
- max step in ech episode =1000
- eps_start=1.0
- eps_end=0.01
- eps_decay=0.995

# Rewards

## 5 Hidden layers model

![alt text](https://github.com/tiantian20007/DRLND-Navigation/blob/master/res/result.png "5 Hidden layers model")

## 2 Hidden layers model

![alt text](https://github.com/tiantian20007/DRLND-Navigation/blob/master/res/result2.png "2 Hidden layers model")





# Future Work

- [Double DQN (DDQN)](https://arxiv.org/abs/1509.06461)
- [Prioritized Experience Replay](https://arxiv.org/abs/1511.05952)
- [Dueling DQN](https://arxiv.org/abs/1511.06581)

Researchers at Google DeepMind recently tested the performance of an agent that incorporated all six of these modifications. The corresponding algorithm was termed [Rainbow](https://arxiv.org/abs/1710.02298).
It outperforms each of the individual modifications and achieves state-of-the-art performance on Atari 2600 games!
