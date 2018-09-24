# Deep Reinforcement Learning - Chasing Bananas

## Overview
Using the Unity agent/environment "Banana", the task is to train an AI agent to eat as many yellow bananas as possible in a 300 step episode run. The matrix for evaluation is how many episodes it takes for the agent to achieve an average reward of 13 over 100 consecutive runs.

The agent receives feedback in the form of a reward after taking each action (left, right, forward or backwards on the game board.) A +1 reward if it ate a yellow banana and a -1 reward if it ate a blue banana. The environment also conveys to the agent the state of the agent and area around it, including the agent's velocity along with information on objects in front of it.

At first the agent randomly takes actions and records the feedback, but eventually begins to take those experiences and learn from them using a deep neural network called a Deep-Q Network.

The attached code written in Python, using PyTorch and presented in a Jupyter Notebook, demonstrates how the agent learns and eventually achieves an average score of 13 over 71 consecutive episodes.

## Methodology

### Model Overview
As seen in the code, the Deep Q-Network includes a simple two hidden layer, 64-64 node neural network with ReLU activation functions. Traditional deep learning hyperparamters such as learning rate and batch size have been optimized for this particular environment and goal. In addition, the deep reinforcement learning model includes specialized hyperparamters that specifically control how and when the agent learns, which are discussed below.

### Exploitation vs. Exploration

Initially the agent knows nothing about the environment it is in. It has to try random actions to determine which are optimal to achieve its goal. However, over time, as it develops a repository of past actions, it has to transition from trying new things to doing what it has already learned are high quality actions. This exploration vs. exploitation balance, over the life of hundreds of episodes, is very impactful on the final result. 

<strong>I found in this environment that, relative to other DRL agents I have trained, the agent does not need to try nearly as many random actions to gather the necessary experience to act efficiently. Therefore, I have weighted exploitation heavily from an early stage while keeping a minimal amount of exploration.</strong>

### Learning From Experience

The agent stores all of its past experiences, which includes 1) what action it took that resulted in 2) what reward/penalty and 3) what next state of the environment did the action place the agent in. The question when training the agent is, when and how to use this experience to learn more optimal actions going forward. Hyperparameters include the number of experiences to keep in a rolling history, how often to pull a new batch of experiences to update the learning model, how much to weight what's learned, etc. 

<strong>In optimizing this agent, I found that the agent learns optimal actions fairly quickly, as described above, and therefore, I had the agent do a soft update of the network after every agent action. This approach, as opposed to only updating the network after every few actions, was far superior, cutting the training time by more than half.</strong>

## Results and Future Work

The above approach produced an average reward of 13+ over 100 consecutive episodes within 71 episodes, as shown in the jupyter notebook. Much of the improvement and variation in results centers around how much, how fast and how often to use the agent's past experiences to train the network and improve the action policy. Future work focused on this area could yild improved results, namely Prioritized Experience Replay or other methods of selecting/optimizing which experiences to utilize for training purposes.

## Setup Instructions

To reproduce this model on a Mac, clone the <a href="https://github.com/udacity/deep-reinforcement-learning">Udacity DRLND repo</a>, then place the banana.app.zip file in the p1_navigation folder and uncompress it. Also place the Juputer notebook there and run it.
