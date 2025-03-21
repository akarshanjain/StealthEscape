---
layout: default
title:  Final Report
---

### [Welcome to Stealth Escape!]()
<iframe width="560" height="315" src="" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; 
clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Project Summary  
The StealthEscape project is focused on developing a reinforcement learning (RL) agent within the Minecraft environment using the Project Malmo platform. The agent is tasked with navigating 
a maze, avoiding hazards such as lava pits, and evading zombie guards. The core objective is to optimize the agent’s pathfinding strategy using RL, incorporating a combination of exploration and exploitation to efficiently navigate through the maze while avoiding detection. The agent is trained to make decisions based on its current state (position, light levels, and proximity to obstacles) and adapt its behavior to minimize the risk of falling into hazards or being caught by guards. By leveraging Q-learning and a reward-based system, the agent's actions are refined over time, improving its ability to achieve the mission's goal.   
  
## Approaches  
For our final model, we built it on an earlier Q learning network that trained the agent to move through the maze with zombies and lava (dangers). Previously the agent could only access its position, nearby zombies, and lava locations to choose from a few actions(forward, turn left, and right). Also, we used a fixed reward system, where the agent was awarded 100 points for reaching the goal, and -100 for hitting any dangers. We utilized experience replay and periodic network updates to help improve the Q-values.

One advantage of our baseline approach is that it is simple and efficient, it is easy to implement, and computationally light, so it trains faster and doesn't require large amounts of data. It is also stable since the Q-values are updated periodically and rewards are fixed. 
The disadvantages of our baseline approach included limited observational space and action space. Using only basic position tracking meant that the agent couldn't effectively assess cues in the environment and limited the ability to make nuanced decisions. Using a fixed reward system also doesn't encourage exploration or safer decision-making beyond simply reaching the goal. The agent relied too much on static environments, so it was hard to generalize. 

Initialize Q-network, target Q-network, replay buffer, optimizer
Set epsilon = EPSILON_START

```
For each cycle:
    Start mission
    prev_state = None
    total_reward = 0

    While mission is running:
        state = Get current state
        If state is valid:
            If random() < epsilon:
                action = Random action
            Else:
                action = Max Q-value action

            Perform action
            next_state = Get next state
            reward = Calculate reward

            Add experience to replay buffer

            If replay buffer size >= BATCH_SIZE:
                Sample batch from buffer
                For each experience in batch:
                    Compute Q-values
                    Compute target Q-values
                    Calculate loss
                    Update Q-network

            epsilon = epsilon * EPSILON_DECAY

            If cycle % TARGET_UPDATE_FREQ == 0:
                Update target Q-network

    Print total_reward
```

Now, we made the agent smarter and it makes better decisions, the code has more detail about the environment, not just the agent's position. The agent can now sense how close the walls are, which way the goal is, and know more about the dangers near it. This extra information allows the agent to understand the surroundings a lot better and make much better decisions. The agent can move sideways and turn more smoothly, which helps it move better in the maze and avoid dangers more easily. This new movement style is also closer to how things move in real life so it helps in Minecraft.

For training, we changed the network to a deeper model to improve the model's ability to predict Q-values more accurately. We added a prioritized experience replay, so the agent focuses on learning from the most important experiences rather than revisiting all the past experiences uniformly. We also refined the reward system, it now receives feedback for safer exploration, and this will encourage the agent to explore the maze more effectively. One of the key challenges with Q learning is finding a balance between exploration and exploitation, to address this, we fine-tuned the epsilon decay mechanism to allow the agent to explore in the early stages of training while gradually focusing more on exploiting the best-known action as it learns. We also improved the target network update frequency so make sure that the learning process remains stable

The advantages of our current approach are better sensory input and smoother movement, which allows the agent to make better decisions in complex environments.
The new reward system allows safer exploration, and the agent can handle dynamic changes and adapt to new hazards, so it can move better in unpredictable environemnts.

But this comes with a greater computational complexity due to a deeper model. It also can overfit the expanded state space, especially if the environment changes too quickly. The training time is also longer since the network is deeper and the agent is trying to learn in a larger environment.

```
Initialize Q-values Q(state, action) arbitrarily
Initialize deep neural network model for Q-value approximation
For each episode:
    Initialize state s
    Repeat until goal is reached or max steps:
        Choose action a using epsilon-greedy policy
        Take action a, observe reward r and next state s'
        Store experience (s, a, r, s') in prioritized replay buffer
        Sample a batch from buffer with prioritized sampling
        For each experience (s, a, r, s') in the batch:
            Predicted Q-value = Q-network(s, a)
            Target Q-value = r + gamma * max(Q-network(s', a'))
            Update Q-network parameters using loss function (Predicted Q - Target Q)^2
        If s' is terminal, break
```



    
## Evaluation  
  

## References  
- [Project Malmo Documentation](https://www.microsoft.com/en-us/research/project/project-malmo/)  
- [Project Malmo Github Repository](https://github.com/microsoft/malmo)  
- [Mission XML Documenation](https://microsoft.github.io/malmo/0.30.0/Schemas/MissionHandlers.html)  
- [The Malmo Platform for Artificial Intelligence Experimentation](https://www.ijcai.org/Proceedings/16/Papers/643.pdf)  
- [Enjoy AI in Minecraft](https://tsmatz.wordpress.com/2020/07/09/minerl-and-malmo-reinforcement-learning-in-minecraft/)  
- Libraries Used: Malmo, Torch, Numpy  

## AI Tool Usage  
AI tools such as ChatGPT and DeepSeek were used for simple code debugging purposes and to help understand the Malmo documentation. For example, understanding how to use XML to help design
the missions. 
