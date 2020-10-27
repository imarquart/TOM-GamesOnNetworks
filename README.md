# TOM Knowledge Repository: Games on Networks

In this repository, I would like to write down what I (think I) understand about the analysis of games with a network structure and the literature relating to it. I will also try to point out some papers on the empirical application of these issues. Please feel free to add corrections as you see fit.

## What are games on networks (for)?

Game Theory is fundamental for analyzing _strategic_ interactions of (possibly boundedly) rational agents. Interactions are strategic if agents anticipate the benefit of their choices conditional on what other agents might do now or in the future. Different from, say, models of mutual learning, agents in a game engage in acts of introspection about what other agents might do next.

Typically, each agent is afforded a reaction function: If a peer were to do action _a_, then our agent would want to do action _b_. If peer were to choose action _c_ instead, our agent would now want to choose _d_, and so on. An _equilibrium_ is a set of actions for each agent that is consistent with all these reaction functions: In an equilibrium, everyone is happy with their choice of action, given the choices of other agents. Game Theory typically doesn't specify _how_ we get to the equilibrium, it rather analyzes equilibriums directly. This makes these immensely complex behavioral problems amendable to formal analysis. On the other hand, it means that several equilibria may be viable in a given situation, and our model would require additional assumptions to pick which one will occur.

Game theory becomes crucial in modeling when preferences (goals) of the agents diverge _and_ agents are interdependent. Examples may be hiring committees, market interactions between firms, R&D strategies, voting in teams, delegation of tasks, the provision of public goods, or social pressure.

Games on _networks_ are situations where the structure of interdependence can be represented by a network. This occurs when three or more agents interact, and not everyone is directly interdependent. Consider three actors _A_,_B_, and _C_ and assume _A_ is interdependent with _B_ but not with _C_:

  _A_<---> _B_ <---> _C_
  
We may now analyze this situation with pairwise dependencies between _A_ and _B_, as well as _B_ and _C_. If, however, _B_ anticipates in some way the actions of _A_ and _C_ when making his choice, then agent _A_'s payoff is now also indirectly influenced by the choice of _C_. We thus have to analyze a game on a network structure. Interdependencies can now be direct, indirect or entirely absent.

The main thing to keep in mind is that the structure of interdependencies - aka the network - is the main "parameter" of interest. Typically, the games we consider are already well understood. The fundamental question here is how the presence or absence of interdependency might change the conclusions.

An [adjacency matrix](https://en.wikipedia.org/wiki/Adjacency_matrix#Examples) represents these relationships succinctly.
These relationships can be fixed (or exogenous), or they could also depend on the agent's choices (and be endogenous). In the former case, we analyze a game on a network structure. In the latter case, we also analyze network formation (and the subsequent game). Naturally, there's also a large literature, predating the present topic, that focuses only on network formation without an attached game, however I will not get into these papers here.

Network theory is a huge subject in itself, spanning multiple fields and numerous applications. I will link where I can, but I have to assume some knowledge about networks.

## Implicit networks in the past literature

The analysis of networks as structural objects of interest is relatively new in Game Theory.
However, networks implicitly turned up in the analysis of informational dependence in Mechanism Design. If you don't know what that is, perhaps the following explanation suffices: If you are a designer, and you know that agents are going to be strategic, which game should you pick? For example, if you are Google, and you want to auction off ad-space, then which auction format is best? That's mechanism design (econ Nobel prize 2007). Auction design (econ Nobel prize 2020) and regulation (econ Nobel prize 2014) are prominent applications. Given that this affair is typically even more complex than the analysis of games, let me just give you two important references for completeness:

#### McAfee, R. P. and Reny, P. J. (1992) ‘Correlated Information and Mechanism Design’, Econometrica, 60, pp. 395–421. doi: 10.2307/2951601.

Private information (or types, or preferences) determine how much "power" an agent has in mechanism design. For example, a firm would like to know how much a customer is willing to spend. If however, two customers are known to have very similar tastes (their private information is correlated), then finding out about one tells me about the other. McAfee and Reny analyze the consequence of such correlations.

#### Jehiel, P. and Moldovanu, B. (2001) ‘Efficient Design with Interdependent Valuations’, Econometrica, 69(5), pp. 1237–1259. doi: 10.1111/1468-0262.00240.

This paper not only assumes that private information may be correlated, but that the types of other players may also influence the payoffs directly.

While a network of interdependence exists in this literature, it is typically assumed to be random. For that reason, said network is not the primary object of analysis.

## Groups as a precursor to networks



## Appendix: Equilibrium existence