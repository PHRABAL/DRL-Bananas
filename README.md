# Deep Reinforcement Learning - Chasing Bananas

## Overview
Using the Unity agent/environment "Banana", the task is to train an AI agent to eat as many yellow bananas as possible in a 300 step episode run. The matrix for evaluation is how many episodes it takes for the agent to achieve an average reward of 13 over 100 consecutive runs.

The agent receives feedback in the form of a reward after taking each action (left, right, forward or backwards on the game board.) A +1 reward if it ate a yellow banana and a -1 reward if it ate a blue banana. The environment also conveys to the agent the state of the agent and area around it, including the agent's velocity along with information on objects in front of it.

At first the agent randomly takes actions and records the feedback, but eventually begins to take those experiences and learn from them using a deep neural network called a Deep-Q Network.

The attached code written in Python, using PyTorch and presented in a Jupyter Notebook, demonstrates how the agent learns and eventually achieves an average score of 13 over 100 consecutive episodes.

## Methodology
