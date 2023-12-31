# Monte Carlo Markov Simulations
I developed this [Jupyter Notebook](Parallel%20Markov%20Monte%20Carlo.ipynb) to run parallel Monte Carlo Simulations of Markov Models for Health Economics.  The notebook sets up the required class and functions for the simulation and implements a parallel approach using concurent futures and also optimises efficiency by implementing chunks. i.e. instead of computing each simulation in its own thread we bundle simulations into chunks giving a substantial [performance bump](Performance.MD). 

<img width="1338" alt="Screenshot" src="https://github.com/chriswilson2020/MonteCarloMarkov/assets/73828727/07dd4ef2-b7c2-4514-b832-547469cde71c">


## Introduction
This notebook is a Python implementation of a simulation using a Markov Model to estimate costs for two different medical treatments with different associated adverse effects and benefits, Treatment A and Treatment B, over a 20-year period. The simulation is performed using Monte Carlo methods.

<img width="583" alt="Screenshot 2023-12-17 at 11 44 18" src="https://github.com/chriswilson2020/MonteCarloMarkov/assets/73828727/d0e979b8-c1ec-442c-b035-a090c96f44dd">

Here's a breakdown of what the Monte Carlo simulation and the Markov Model do and how it works in this context:
### Monte Carlo Simulation: 
Monte Carlo simulation is a statistical technique used to estimate outcomes of complex systems by generating random samples from known probability distributions. In this case, the simulation is used to estimate the total costs associated with medical treatments.

### Markov Model: 
The code defines a MarkovModel class that represents a Markov Model for a medical system with different transition states. In a Markov Model, transitions between states occur probabilistically. The simulation modifies the current state of the system based on transition probabilities and random events. This is done by implementing a transition matrix for each of the treatments that determines the probability of moving from one state to another (as well as the probability of moving back to the previous more healthy state).  In simple terms, the matrix represents the journey of a person's health, starting from a healthy state and possibly ending in death. Each row in the matrix represents the person's current health state, and each column represents the potential next health state. Some additional details can be found [here](MarkovNotes.md).


### Simulation Process:
The run_simulation method of the MarkovModel class performs a single simulation run for a specified number of cycles (20 years in this case).
In each cycle, it calculates the next state based on transition probabilities defined in the transition matrix. It uses random multinomial sampling (np.random.multinomial) to determine how many individuals move from one state to another.
It also simulates the occurrence of new cases or diagnoses (e.g., prevalence) by adding a Poisson-distributed random value to the initial state.
It calculates the total cost for the current state and accumulates it over time. This cost is adjusted for insurance premiums. The simulation also assumes an annual increase in insurance premiums. The results of each cycle are stored in costs_over_time.

### Custom Transition Matrices:
The code defines two custom transition matrices, one for Treatment A and one for Treatment B. These matrices specify the probabilities of transitioning between different health states for each treatment.
The probabilities for adverse events and transitions between states may vary for each treatment, and these probabilities are sampled from normal distributions to introduce randomness into the simulation.

### Parallel Simulation:
To speed up the simulation, the code uses concurrent processing with a ProcessPoolExecutor to run multiple simulations in parallel.
The simulate_treatment_A_chunk and simulate_treatment_B_chunk functions perform a batch of simulations for Treatment A and Treatment B, respectively.
Multiple simulations are run in parallel by creating a pool of worker processes, and the results are collected at the end.
