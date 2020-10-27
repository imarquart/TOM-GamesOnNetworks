# TOM Knowledge Repository: Games on Networks

In this repository, I would like to write down what I (think I) understand about the analysis of games with a network structure and the literature relating to it. I will also try to point out some papers on the empirical application of these issues. Please feel free to add corrections as you see fit.

## What are games on networks (for)?

Game Theory is fundamental for analyzing _strategic_ interactions of (possibly boundedly) rational agents. Interactions are strategic if agents anticipate the benefit of their choices conditional on what other agents might do now or in the future. Different from, say, models of mutual learning, agents in a game engage in acts of introspection about what other agents might do next.

Typically, each agent is afforded a reaction function: If a peer were to do action _a_, then our agent would want to do action _b_. If peer were to choose action _c_ instead, our agent would now want to choose _d_, and so on. An _equilibrium_ is a set of actions for each agent that is consistent with all these reaction functions: In an equilibrium, everyone is happy with their choice of action, given the choices of other agents. Game Theory typically doesn't specifiy _how_ we get to the equilibrium, it rather analyzes equilibriums directly. This makes these immensely complex behavioral problems amendable to formal analysis. On the other hand, it means that several equilibria may be viable in a given situation - 

Game theory becomes crucial in modeling when preferences (goals) of the agents diverge _and_ agents are interdependent. Examples may be hiring committees, market interactions between firms, R&D strategies, voting in teams, delegation of tasks, the provision of public goods, or social pressure.

Games on _networks_ are situations where the structure of interdependence can be represented by a network. This occurs when three or more agents interact, and not everyone is directly interpendent. Consider three actors _A_,_B_, and _C_ and assume _A_ is interdependent with _B_ but not with _C_:

  _A_<---> _B_ <---> _C_
  
 We may now analyze this situation with pairwise dependencies between _A_ and _B_, as well as _B_ and _C_. If, however, _B_ anticipates in some way the actions of _A_ and _C_ when making his choice, then agent _A_'s payoff is now also indirectly influenced by the choice of _C_. We thus have to analyze a game on a network structure.
 
 
 
 ## Groups as a precursor to networks
 
 The analysis of networks is a recent addition to Game Theory. Before the late 2000's, 
