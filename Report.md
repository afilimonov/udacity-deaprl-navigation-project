### Approach

These are main steps for developing an agent to solve Banana collection environment:

* Install the environment and equired dependencies.
* Denfine the environment and examine state and action space.
* Take random action in the environmenbt and collect the feedback. This establishes the baseline.
* Implement learning algorithm(s)
* Define basic Deep Q-Network (DQN) and Double Deep Q-Network (DDQN) agents.
* Train DQN and DDQN agents and save trained models for each agent.
* Plot the training results.
* Test DQN and DDQN agents.
* Plot the testing resutls.

### Learning Algorithm

Learning algorithm is used to find an optimal policy that maximizes the reward for the agent. The optimal policy is discovered discovered by interacting with the environment and receiving environment feedback. Through interactions the agent learngs the optimal policy policy by mapping environment states to best actions i.e. actions the yield the highest reward. This process is know as Q-Lenaring. Q-Learning algorithm consists of multiple components described in the sections below.

#### Deep Q-Network

Deep Q-Network (DQN) uses Q-Function that estimates expected reward for all actions for all environment states. In DQN a neural network (NN) is used to approximate Q-Fuction. In this project I constructed a fully connected NN with 3 layers with 64, 64 and 4 (size of the action space) nodes. I used RELU activation function for the first two layers. The NN implementation can be found [here](dqn/model.py).

#### DQN Agent

Basic DQN Agent used in this project implments all required log for interacting with the environment and learning the optimal policy. It also provides train() and test() methods for training and testing the agent. The DQN source code can be found [here](dqn/agent.py)

#### Double Deep Q-Network Agen

In this project I also used Double Deep Q-Network (DDQN) agent. DDQN was introduced to overcome a problem of [overestimating Q-values](https://www.ri.cmu.edu/pub_files/pub1/thrun_sebastian_1993_1/thrun_sebastian_1993_1.pdf). DDQN addresses this issue by having two sets of NN parameters one used to select action and another to evaluate it. The DDQN agent is a subclass of DQN agent it reuses all logic and underlying neural networks. It overrites learn() method to implement the logic of using diferent sets of parameters to select and evalutation action. DDQN agent source code can found [here](dqn/doubleagent.py).

#### Experience Replay

Both DQN and DDQN agents use Experience Replay. Experience Replay logic inlcudes replay buffer that storegs history of agent interactions with the environment also known as experiences. The agent then can sample stored experiences during learning process thus breaking correlation between consequtive experiences. This imporvoes learning process by preventing Q-Larning algorithm becoming biased towards sequential experiences. The implementation of the replay buffer can be found
[here](dqn/replaybuffer.py).

#### Epsilong Greedy

Both DQN and DDQN agents in this project employ epsilong greedy action selection during traing process. This enables the algorithm to balance exploring and exploiting during the learing by randomly picking actions instead of policy action based on probability defined by epsilon hyperparameter. DQN and DDQN agents train() method accepts paremeters to set starting and endiing epsilon values as well as epsilon decay. The best (fastest to solve the environment) epsilon parameters discovered through experimentation: eps_start=1.0, eps_end=0.02, eps_decay=0.98

### Training Performance Reports

The graphs below depict DQN and DDQN training scores
![plot of rewards](./dqn-replay-graph.jpg)


