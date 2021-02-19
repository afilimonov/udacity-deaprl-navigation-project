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

Deep Q-Network (DQN) uses Q-Function that estimates expected reward for all actions for all environment states. In DQN a neural network (NN) is used to approximate Q-Fuction. In this project I constructed a fully connected NN with 3 layers with 64, 64 and 4 (size of the action space) nodes. I used RELU activation function for the first two layers. The NN implementation can be found [here](dqn/model.py) 
