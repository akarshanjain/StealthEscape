---
layout: default
title: Status
---

## Project Summary  
The StealthEscape project is focused on developing a reinforcement learning (RL) agent within the Minecraft environment using the Project Malmo platform. The agent is tasked with navigating 
a maze, avoiding hazards such as lava pits, and evading zombie guards. The core objective is to optimize the agent’s pathfinding strategy using RL, incorporating a combination of exploration 
and exploitation to efficiently navigate through the maze while avoiding detection. The agent is trained to make decisions based on its current state (position, light levels, and proximity 
to obstacles) and adapt its behavior to minimize the risk of falling into hazards or being caught by guards. By leveraging Q-learning and a reward-based system, the agent's actions are 
refined over time, improving its ability to achieve the mission's goal. 

[Take a look at our status update!](https://www.youtube.com/watch?v=Ry0RnIFcsuc)
<iframe width="560" height="315" 
    src="https://www.youtube.com/waRy0RnIFcsuc" 
    frameborder="0" 
    allowfullscreen>
</iframe>

<iframe width="560" height="315" 
    src="https://youtu.be/Ry0RnIFcsuc" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
</iframe>

## Approach  
This project utilizes **Q-learning**, a reinforcement learning algorithm, to train an agent to navigate a maze filled with hazards like lava, gaps, and zombies. The agent receives 
observations about its position and surrounding entities, including nearby zombies and light levels, which influence its decision-making. The agent has three actions it can take: 
move forward, turn left, and turn right, with predefined weights to guide its exploration-exploitation balance. Rewards are given for reaching the goal (+100), while penalties are 
assigned for falling into lava (-100), being caught by zombies (-100), or falling into gaps (-100).

The agent's experience is stored in a replay buffer, from which random mini-batches of data are sampled for training. The Q-values are updated using the Bellman equation, and the model’s 
loss is minimized using Mean Squared Error (MSE). The agent's policy improves through repeated cycles, with the target model’s weights updated every 10 cycles to stabilize training. 
Hyperparameters like learning rate (0.001), discount factor (0.99), and epsilon decay rate (0.995) were chosen to balance exploration and exploitation and facilitate stable learning.

Training consists of 100 cycles, with the agent interacting with the environment in each cycle, collecting rewards, and updating its Q-values. As the agent learns, it progressively improves 
its navigation strategy, avoiding hazards and optimizing its path to the goal.

## Evaluation  
The initial maze-solving agent had significant limitations that affected its performance. The basic state space, consisting of just x, y, z coordinates, meant the agent often fell into gaps and struggled to navigate effectively. With only three possible actions: moving forward and making 45-degree turns. The agent's movement was rigid and unnatural, leading to inefficient pathfinding and frequent collisions.

The improved implementation transforms the agent's capabilities through several key enhancements. By expanding the state space to include comprehensive environmental awareness, including wall detection and goal orientation, the agent now makes more informed decisions. The addition of smoother turning angles and strafing movement allows for more precise navigation. A refined reward system encourages the agent to explore safely while making steady progress toward the goal.

The results speak for themselves (in the video: https://youtu.be/FyNuD8hs58c) the new agent explores the maze more thoroughly while avoiding hazards, demonstrates smoother navigation patterns, and shows higher success rates in exploring the maze completely. This improvement stems from the agent's enhanced ability to understand its surroundings and make intelligent pathfinding decisions, rather than the trial-and-error approach of the previous version.


## Remaining Goals and Challenges 
As we move forward, our primary goal is to refine the reinforcement learning agent's ability to navigate the maze more efficiently. While the agent is capable of completing the maze, its 
pathfinding remains inefficient, and we intend to improve the optimization of its movements. Specifically, we aim to integrate a more sophisticated learning algorithm that takes into 
account the surrounding environment, such as light levels and obstacles, as part of a more nuanced state space. Additionally, we plan to enhance the reward system to incentivize faster, 
safer, and more strategic navigation, rather than simply rewarding the agent for reaching the goal.

Another key goal is to evaluate the current agent's performance more rigorously. Our testing so far has been limited to basic functionality, and we have not yet conducted a comprehensive 
evaluation of the agent's ability to handle more complex mazes and interactions with environmental features such as lava or guards. We will be conducting a set of performance evaluations, 
both quantitative (e.g., average reward per episode, time to goal) and qualitative (e.g., visual demonstrations of agent behavior), to assess the current state of the system and determine 
areas for further improvement.

The challenges we foresee include fine-tuning the reward structure and ensuring the agent's learning process is stable despite the noisy environment in the maze. The complexity of 
integrating dynamic features, like light levels and variable guard positions, will also add to the difficulty of maintaining efficient learning. Additionally, performance issues, 
particularly with training time and convergence, may pose obstacles as we scale the number of episodes and complexity of the task. To overcome these challenges, we may explore using a 
more complex deep reinforcement learning architecture or experiment with alternative training strategies like experience replay or dueling networks.

## Resources Used 
- [Project Malmo Documentation](https://www.microsoft.com/en-us/research/project/project-malmo/)
- [Project Malmo Github Repository](https://github.com/microsoft/malmo)
- [Mission XML Documenation](https://microsoft.github.io/malmo/0.30.0/Schemas/MissionHandlers.html)
- Libraries Used: Malmo, Torch, Numpy
