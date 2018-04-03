PyRL : Reinforcement Learning with Python 3
===================

## What is it ? ##

PyRL is a project about Reinforcement Learning (RL) released during "Projet Informatique" IN104 at ENSTA ParisTech. In this project we tried to work with different Environments ( 1D, 2D, 2D with walls,  simple Tetris ) and Agents, starting from a "stupid" Agent to a self-learning Agent using different algorithms like Monte-Carlo Methods or Temporal Differencing.


Features
-------------

In this project we work with different agents implemented with different algorithms and also we can choose the environment that we would work with.

> **Agents:**

> - **AgentRandom** is a basic agent that takes a random action (Left, Right, Up, Down) Those possible actions are in the environment and the agent sees only a number that refers to an action.
> - **AgentValue**  : There is two types of this basic agent implemented with Monte-carl estimation (Batch and Incremental ). This agent learns from the value function calculated in each state and it depends on the policy ( Left, Right, Up, Down).
> - **AgentQValue** :  In previous Agents the problem was the transition function, here in Q value learning we will work pairs state-value. We have an RL agents that learns from previous steps.
> - **AgentTD** :  We will make our agent more "smart" using Bellman equation and the main difference with Monet-Carlo is that we will make updates at each step.

If you want to change the rate of learning you have to modify those variables:
```python
    13	self.decay_rate = 0.9 #decay rate for the probability of making a random action(0.99 slow learning)
        self.alpha = 0.5 # rate of learning-value between 0 and 1 (high value = fast learning but can lead to oscillations)	
```

> **Environments :**

> - **Environment1D** the most simple environment, it a 1D environment (seen as a 1D table ).
> - **Environment2D** it's a 2D environment that can have a various number of rows and columns.
There's 3 **variations** of this environment : simple 2D, 2D with static walls and 2D with moving walls.
> - **Environment Tetris simple** it is a simple Tetris environment 

Requirements 
-------------

To use this project you will need **Python3**. In GUI mode we are using **tkinter GUI library** and for learning graphs we work with **matplotlib**, so make sure you have this library before trying to plot learning curves.

How to use  
-------------


#### Terminal Mode (NO-GUI)

To use this program in a no-gui mode, you need only to run the *main.py*, and to download Agents and Environment folders. If you want to change the number of cells or the number of cells per row in an environment, you just have to change the variables *num_cells_* and *cells_per_row* in the env files.

In the main.py you can choose any type of environments and agents as well as number of episodes and number of actions allowed in each episode :

```python
    100 #environment = EnvironmentGrid1D(arguments)
	    #environment  = EnvironmentGrid2D(arguments)
		#environment  = EnvironmentGrid2DStaticWalls(arguments)
	    #environment  = EnvironmentMovingWalls(arguments)
	    environment  = EnvironmentTetrisSimple(arguments)
    
	    # Get the number of possible states and actions for this environment  
	    num_states  = environment.numPossibleStates()
	    num_actions = environment.numPossibleActions()
    
	    # Create the agent
	    #agent = AgentRandom(num_states,num_actions)
	    #agent = AgentLeft(num_states,num_actions)
	    #agent = AgentValueMonteCarlo(num_states,num_actions)
	    #agent = AgentQValueBatch(num_states, num_actions)
	    #agent = AgentQValueIncremental(num_states, num_actions)
    	agent = AgentTD(num_states, num_actions)
    
	    num_episodes    = 150  # Number of episodes to execute
	119 max_num_actions = 1000 # Max number of actions; abort episode if it is more.
```
#### Learning Curves

![GUI](http://code2net.com/folder/screenshots/curves.png)

There is also at the end of the *main.py*, a piece of code to plot the learning curve. Make sure that you have **MatPlotLib** installed. If you want to use this program without this lib, you have to comment the importation line:

```python
import matplotlib.pyplot as pyplot
```

and the following lines:

```python
#Plot the learning curve
    axes = pyplot.gca()
    axes.set_xlim([0, num_episodes])
    axes.set_ylim([-100, max(y_rewards)])
    pyplot.plot(nb_episode, y_rewards)
    pyplot.show()
```

#### GUI Mode

![GUI](http://code2net.com/folder/screenshots/gui.png)

The usage of GUI mode is implemented separately for every environment. This was adapted from the project Tetris Tk - A tetris clone written in Python using the tkinter GUI library (see https://code.google.com/p/tetris-tk/source/browse/trunk/tetris_tk.py)
License: GNU GPL v3

At the end of every file named gui_***.py you can choose the agents to work with. 
```python

# Create the agent
#agent = AgentRandom(num_states,num_actions)
#agent = AgentLeft(num_states,num_actions)
#agent = AgentValueMonteCarlo(num_states,num_actions)
#agent = AgentQValueBatch(num_states, num_actions)
#agent = AgentQValueIncremental(num_states, num_actions)
agent = AgentTD(num_states, num_actions)

num_episodes    = 600  # Number of episodes to execute
max_num_actions = 1000 # Max number of actions; abort episode if it is more

```

To run a gui, you first have to enter the following command:
```bash
python3 gui_***.py
```
and then **press the "S" key to start** some episodes (600 by default). You can change the delay between two actions using the *slider*.


More Information about Reinforcement Learning
-------------

See the IN104 project page: 
http://perso.ensta-paristech.fr/~stulp/IN104/index.php?n=Site.ApprentissageRenforcement

License
-------------
### The Code is tempopray private - contact me for details

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

-----
Imad El Hanafi & Antonin Raffin 

