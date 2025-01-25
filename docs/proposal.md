---
layout: default
title: Proposal
---

## Summary of the Project
The main idea of our project is to have a stealth based game for Minecraft. We plan to have our agent navigate through a generated maze with random mobs or guards, different light sources, and different sound levels with random spots for safe-zones. The agent must avoid detection by staying out of the line of sight of the mobs (or guards). This will vary on the amount of light which stated as before will be random. The details will be figured out later but more light is a direction relationship to more line of sight which in turn, makes our agent have to be more careful in their actions. The inputs are gonna be the current state, or what the agent can see, the light levels, the mob positions, the different patrol routes, and the agent current position. The output will most likely be the agent next move, wheter to wait, run, walk, turn back, go to a safe zone, and many others that we will incooperate later, to successfully return a won state, or whenever the agent finally reaches the goal. This system could have applications in game AI development, particularly for stealth-based gameplay mechanics. This idea is originally from a game I played a lot growing up, a quest in runescape (link below if you're curious.) https://www.youtube.com/watch?v=2inuz7OXmK0&t=245s


## AI/ML Algorithms
The project will use reinforcement learning, specifically methods like Deep Q-Learning or similar algorithms that rely solely on reinforcement learning. These were some things we saw at the start of lecture and in other classes like 171. The approach will focus on rewarding stealthy behavior and penalizing detection, with additional rewards for reaching the goal safely.

## Evaluation Plan
To start things off, on the quantitative evaluation side, the projects success rate will solely be the percentage of the mazes that we complete without getting caught, the average steps it took to reach the goal compared to the shortest path, and the number of detections before getting caught or per episode. We are gonna have a random agent and a simple heuristic that should learn with about a 60-80% success rate as opposed to a 10-15% for the random agent. (These are ballpark numbers, I am just guessing.) The evaluation will use mazes with different sizes, random mob placement, random patrol routes, and different light levels. 

For the qualitative analysis, we will most likely use toy examples like small mazes with static mob placements, and fixed light levels for each section. Sanity checks include observing whether the agent avoids well-lit areas and mobs' line of sight. We will need to implement some sort of system to be able to track the learning of the agent, to make sure it is making progress. The moonshot goal is an agent that reliably navigates large, complex mazes with dynamic mobs and random patrols. This would be amazing as there are lots of different aspects that will all be random, and if our agent is able to navigate through all of that then it will be very successful. 

## Meet the Instructor

We plan to meet with the instructor Tuesday January 28, 2025 at 10:30 a.m. to discuss our project.


## AI Tool Usage
No AI tools were used
