# Project Computational Science
## Dynamic Modeling of Bed Bug Spreading: A Scale-Free Network Simulation for Community-Integrated Pest Management Strategies
### Contributors:
- Dita Arklina (University of Amsterdam)
- Maria Mshalwat (Vrije Universiteit)
- Xuening Tang (University of Amsterdam)
## Project Description
This project aims to study the impact of treatment costs, neighborhood density, and connectivity on the prevalence of bed bugs across economically 
diverse neighborhoods. We also examine the influence of initial site of infestations on the spread within and between such neighborhoods. Thus, 
our research question is: To what extent does the location of the initial outbreak influence the prevalence of bed bug infestations in economically 
diverse neighborhoods based on their connectivity and density? The results of this study give an insight into the dynamics of bed bug infestations 
in different neighborhoods, which is informative for future studies on determining appropriate measures for infestation control and spread.

## How the Code Operates:
Each node has a state, it can be either infected (state = 1) or susceptible (state = 0). Additionally, the simulation is set to run for 100 time steps, where each time step represents 2 days. To determine how the nodes are infected, there is 
a rule that states that the more infected neighbors one node has, the higher the probability of infection for this node will be. 
Each node can either be aware or unaware, all the newly infected nodes begin with an awareness probability of 0.05 assuming that the bed bugs are hard 
to detect in the earlier days of the infection. The longer the nodes are infected the higher the chance of detecting the infection will be, therefore, 
after each time step where the nodes are still found unaware, the awareness probability increases by 0.05 so that in the following time step the chance 
of detection is higher. 

To determine the treatment method that each node will end up choosing, we make use of different probabilities based on the financial status of the nodes. 
We base our probabilities mostly on educated guesses and assumptions in this case, since there is no real-life data to support these assumptions. 
For the below-average, we assume that the majority of the nodes will go for the DIY treatment as they most likely will not be able to afford the professional treatment, 
while the majority of the above-average nodes will choose to do the professional treatment. Based on these probabilities, we assign each newly infected node a treatment method for its infection
period. Furthermore, the node is allowed to test the effectiveness of the method at every time step until the treatment works and the node is susceptible, but in a recovery/cool-down period for 7 time steps
until it becoms fully susceptible again. Once newly infected again, the node gets assigned a new treatment method, going through the probability test all over again.

To make the model more realistic we add some rules based on the financial status of the nodes:
- For below-average nodes that are assigned the professional treatment we introduce a cool-down period, where the nodes are only allowed to use the professional treatment every 15 time steps. During the cool-down period, they make use of the DIY treatment until they either manage to get rid of the infection or they can afford the professional treatment again.
- For the above-average nodes that are assigned the DIY treatment, they change to the professional treatment after the first failed treatment attempt. 

## How to Run the Code:
The code was created and edited on google colab, but it can also be ran in a jupyter kernel. There are two files, [bedbug_model](https://github.com/ditulis/project_team_3/blob/main/bedbug_model.ipynb) and [visualization_bedbug_model](https://github.com/ditulis/project_team_3/blob/main/visualization_bedbug_model.ipynb), bedbug_model is the main model, where the simulation is executed, and visualisation_bedbug_model is where the network was visualized on a smaller scale for the 
presentation poster of this project.
The output of the code was left in the notebook, but it can 
be cleared and ran again with different parameters if needed. The code is ran with different scenarios to which changes can be made. 

## License:
Released under [MIT License](https://github.com/ditulis/project_team_3/tree/main?tab=MIT-1-ov-file)
