## Review (francesco Liaci - s349552)

The code works properly and these are the results:
- problem 1 (Best fitness: 917)
- problem 2 (Best fitness: 33650)
- problem 3 (Best fitness: 1035764) in 1m 36s

The solution implements a two-phase guided hill climbing algorithm. It starts by generating a random clean solution (each item can belong to at most one knapsack) then gradually improves it through a combination of repair and optimization
- In the repair phase, the algorithm checks if any knapsack exceeds the capacity constraints. If it happens, one of the exceeding items is removed at random until all constraints are satisfied. This approach works but since it’s random it might also remove items with a high value unnecessarily. A small improvement could be to remove the least valuable item first (for example choosing the one with the lowest value/weight ratio). that change might improve convergence speed
- Once the solution is valid, the optimization phase starts where the algorithm tweaks the solution to produce a neighbor, then evaluates its fitness and if it’s higher the solution is replaced. This is the standard hill climbing approach and the code correctly checks all constraints using matrix operations. However, since only better solutions are accepted the search might get stuck in local optima. Accepting slightly worse solutions or restarting from new random points after some iterations without improvements could also help the algorithm 
- Regarding performance the algorithm is already efficient for small and medium sized instances. As the problem size grows, computing all those full-matrix multiplications (solution @ weights) in loops might become costly. These could be slightly optimized with an incremental weights vector, but problem 3 is still solvable in reasonable time
