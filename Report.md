## Deep Reinforcement Learning - Chasing Bananas
### Report

### Model Architecture
The Udacity provided Deep Q-Network PyTorch code was used and adapted for this environment. It is a simple two hidden layer, 64-64 node neural network with ReLU activation functions. 

### Hyperparameters
A learning rate of 5e-5 and batch size of 128 were used along with default buffer size of 1e5, gamma .99 and Tau of 1e-3.

One significant area of change in hyperparameters compared to the default provided initially in the code was in the areas of exploration vs. exploitation (epsilon hyperparameters) and in the usage of the experience memory:

#### Exploitation vs. Exploration

I found in this environment that, relative to other DRL agents I have trained, the agent does not need to try nearly as many random actions to gather the necessary experience to act efficiently. Therefore, I have weighted exploitation heavily from an early stage while keeping a minimal amount of exploration. I start epsilon at just 0.25 and decay it at .995 until a minimum of 0.001 is reached. This is significantly less than the 1.0 starting epsilon in the default code and has the effect of following a trained policy more often in the early episodes.

#### Experience Memory

In optimizing this agent, I found that the agent learns optimal actions fairly quickly, as described above, and therefore, I had the agent do a soft update of the network after every agent action. This approach, as opposed to only updating the network after every 4 actions in the default code, was far superior, cutting the training time by more than half. This change, when combined with the epsilon changes above, have a dramatic effect on speed of learning.

## Results and Future Work

The above approach produced an average reward of 13+ over 100 consecutive episodes within 71 episodes.

Much of the improvement and variation in results centers around how much, how fast and how often to use the agent's past experiences to train the network and improve the action policy. Future work focused on this area could yield improved results, namely Prioritized Experience Replay or other methods of selecting/optimizing which experiences to utilize for training purposes.
