# Iterated Prisoner's Dilemma

##About

We developed this code as an experiment for our final project in an introduction to artificial 
intelligence class.  The project features contributions from:

* Nik Steel
* Eric Smith
* Christopher Zygowski 
* and Dwayne Alleyne.

Our goal with this genetic algorithm simulation of the iterated prisoner dilemma (IPD) 
is to test Robert Axelrod's theory of the evolution of cooperation and 
his comments on the characteristics of successful strategies 
in prisoner's dilemma tournaments. Primarily, whether or not it is useful for a strategy to
have the following properties:

1. Niceness
2. Forgiveness
3. Retaliation
4. Non Enviousness

To test these ideas, we defined a set of predicate logic functions to be used as a heuristic
in our genetic algorithm's fitness function.  We also wanted to consider how these traits influenced 
the player's score and test whether or not diversity could also be a useful performance measure.
Our fitness function was then defined as a weighted average of the player's score, the four heuristics,
and diversity. 

Our simulation allows the player a move memory of the previous three turns, and thus, the player's strategy
genome consists of 64 binary bits which define whether the player should cooperate or defect given the results
of the previous three moves.  The strategies and move memories are randomly initialized.

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
to turn.  For example, a selection rate of 15% with a population size of 100 might result in 13 players one turn, 16 players another, 14 another, 
etc.
5. Mutation rate - the percentage of the population to apply a mutation to during a single genetic algorithm iteration.

Further, the five weighting factors to be used in the calculation of fitness are also specified, and the sum of these factors should add to 1.0

6. Score weight
7. Diversity weight
8. Niceness weight
9. Forgiveness weight
10. Retaliation weight
11. Non Enviousness weight

You may omit a parameter from the calculation entirely by setting its weight to 0. All parameters are logged regardless of whether they are factored 
into the fitness score.  For example, you might run the simulation with 100% score weight and notice whether or not a score driven player exhibits
the four traits, even when not actively pursuing them.  The proportion of all cooperate and all defect are also tracked, so you might also observe
that when players value traits like niceness and forgiveness the population prospers yet when pursuing score only or retaliation, the population as
a whole suffers because the players do not cooperate as often.

##Output

It is helpful to open the output demographics CSV files in excel where they may be compared and analysed. 