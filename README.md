# Iterated Prisoner's Dilemma

##About

This genetic algorithm simulation of the iterated prisoner dilemma (IPD) 
demonstrates Robert Axelrod's theory of the evolution of cooperation and 
confirms his assertions about the characteristics of successful strategies 
in prisoner's dilemma tournaments. 

We developed this as an experiment for our final project in an introduction to artificial 
intelligence class.  The project features contributions from:

* Nik Steel
* Eric Smith
* Christopher Zygowski 
* and Dwayne Alleyne.

In Axelrod's experiments with the IPD, he determined that successful strategies demonstrate the
following characteristics:

1. Niceness
2. Forgiveness
3. Retaliation
4. Non Enviousness

Thus, to assess this claim, we defined a set of predicate logic functions to be used as a heuristic
in our genetic algorithm's fitness function.  We also wanted to consider how these traits influenced 
the player's score and test whether or not diversity could also be a useful performance measure.
Our fitness function was then defined as a weighted average of the player's score, the four heuristics,
and diversity. 

The simulation assumes a 3 move memory and 64 bit string strategy genome.

##Usage

The simulation takes in a series of population parameters with which the simulation is to be run.
You may specify multiple sets of parameters at the command line or in a file via input redirection
to run the simulation multiple times and compare the results.  The simulation will output a CSV file
with population demographics, a list of all fitness strategy pairs for all players in all generations, 
and the demographics of the final population.

The simulation's input parameters are as follows:

1. Population size - the number of prisoners to play the prisoner's dilemma game during a single genetic algorithm iteration
2. Number of genetic algorithm iterations - the number of times to run the genetic algorithm. A single iteration consists of 
the following cycle:

   (evaluate -> select -> crossover -> mutate -> evaluate -> select -> merge)

3. Number of prisoner's dilemma iterations - during each of genetic algorithm iteration, the prisoners in the population with 
play the prisoner's dilemma this specified number of times in order to asses their score and fitness.
4. Selection rate - the proportion of the population to be selected for crossover and then survival during a given genetic algorithm iteration.
this value is actually the proportion of a random variable of a binomial distribution, so the exact number selected will vary slightly from turn 
to turn.  For example, a selection rate of 15% with a population size of 100 might result in 13 players one turn, 16 players another, 14 another, etc.
5. Mutation rate - the percentage of the population to apply a mutation to during a single genetic algorithm iteration.

Further, the five weighting factors to be used in the calcualtion of fitness are also specified, and the sum of these factors should add to 1.0

6. Score weight
7. Diversity weight
8. Niceness weight
9. Forgiveness weight
10. Retaliation weight
11. Non Enviousness weight

##Output

It is helpful to open the output demographics CSV files in excel where may be compared and analysed. 