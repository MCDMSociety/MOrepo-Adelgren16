# Multiobjective Extensions of Classical Single-Objective Problems -- Originals Taken from [MIPlib](http://miplib.zib.de/) 2010

The instances here were generated for testing the utility of a general purpose branch-and-bound algorithm for biobjective mixed-integer linear programs.

## Format description

Each instance is given in a single LP file. In each file the objective function is the original objective for the corresponding single-objective problem taken from [MIPlib](http://miplib.zib.de/) 2010. For each file, if there are "n" additional objectives, they are stored as the first "n" constraints. As given here, all objectives are intended to be maximized. Note that files are stored based on the number of objectives -- subdirectory "LP_n" contains problems with "n+1" objectives (one from [MIPlib](http://miplib.zib.de/) 2010 and "n" others).

### Strategy for obtaining additional objectives

Assume that the original objective is of the form \sum{c^1_i * x_i}. New objectives were generated using the six strategies outlined below. I originally generated a second objective in which c^2_i was randomly generated from the interval [-|c^1_i|, |c^1_i|]. I found when studying these problems, though, that many of them suffered from one of the following problems: (i) no conflict between objectives, i.e., the Pareto set was only a singleton, (ii) the second objective was unbounded, or (iii) solving the single objective MIP using the second objective was significantly easier than the original objective. To attempt to deal with each of these issues I generated 5 additional second objectives. The strategies for these were:

(o) For each i, c^2_i is randomly generated from the interval [-|c^1_i|, |c^1_i|].
(a) Solve the LP relaxation using the original objective. Assume the solution is x*. For each variable that is not basic at optimality, set c^2_i = - c_i^1 if: (i) c^1_i is greater than 0 and x*_i is not at its lower bound, or (ii) c^1_i is less than 0 and x*_i is not at its upper bound.
(b) Set c^2_i to be the multiplicative inverse of c^1_i.
(c) Objective 2 is the sum of the continuous variables.
(d) Objective 2 is the sum of the integer variables, plus one continuous variable.
(e) Solve the LP relaxation using the original objective. Also solve the MIP using the original objective. Repeat strategy (a) for integer variables having the same value at the LP solution as at the MIP solution.

Note that in the provided LP files, the objectives are labeled with one of: 1, o, a, b, c, d, e. Here 1 indicates that it is the original objective as given in [MIPlib](http://miplib.zib.de/) 2010 and o-e indicate that the objective was created using the corresponding strategy listed above. Also note that any objective that was unbounded or was not conflicting with objective 1 was thrown away.
