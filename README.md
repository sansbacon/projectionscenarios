# projectionscenarios
Python library for creating NFL and fantasy football projection scenarios.

Current optimizers, particularly those using mixed-integer programming, are rule-based. Players then try to capture a wide range of possible outcomes in an ever-increasing number of rules about who can and cannot be paired together and at what frequency. This is a classic "square peg, round hole" situation, where the rules are a proxy for a player's intiution about various scenarios that could unfold. The initial inspiration for this library is my sense that projection scenarios, not complex optimizer rules, are the best way to generate lineups from these intuitions or possibilities. 
 
This distinction is shown by the following example. Assume DET is at TEN (-4) with a game total of 53, and you are interested in players in this game because they have reasonable salaries for the expected boost from the game environment. If you are using a traditional optimizer, you might allocate a (somewhat arbitrary) percentage of ownership to the QBs in this game as well as the other skill players, create a stacking rule to include one or more pass catchers, and possibly bring it back with one or more players from the other team. Particularly if you are using mixed-integer programming to optimize, this ends up requiring a very complex set of linear constraints that are difficult to program and debug.

Under the "projectionscenarios" approach, you generate multiple sets of projections, and optimize on each set of projections. You can then filter the generated projections by a variety of criteria to obtain the desired number of lineups. There is some inefficiency in throwing away lineups, but there are also significant performance gains from simplifying the optimization criteria.

