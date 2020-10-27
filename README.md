# TOM Knowledge Repository: Games on Networks

In this repository, I would like to write down what I (think I) understand about the analysis of games with a network structure and the literature relating to it. I will also try to point out some papers on the empirical application of these issues. Please feel free to add corrections as you see fit.

## What are games on networks (for)?

Game Theory is fundamental for analyzing _strategic_ interactions of (possibly boundedly) rational agents. Interactions are strategic if agents anticipate the benefit of their choices conditional on what other agents might do now or in the future. Different from, say, models of mutual learning, agents in a game engage in acts of introspection about what other agents might do next.

Typically, each agent is afforded a reaction function: If a peer were to do action _a_, then our agent would want to do action _b_. If peer were to choose action _c_ instead, our agent would now want to choose _d_, and so on. An _equilibrium_ is a set of actions for each agent that is consistent with all these reaction functions: In an equilibrium, everyone is happy with their choice of action, given the choices of other agents. Game Theory typically doesn't specify _how_ we get to the equilibrium, it rather analyzes equilibriums directly. This makes these immensely complex behavioral problems amendable to formal analysis. On the other hand, it means that several equilibria may be viable in a given situation, and our model would require additional assumptions to pick which one will occur.

In math, let <img src="https://render.githubusercontent.com/render/math?math=a_i">  be the action of agent <img src="https://render.githubusercontent.com/render/math?math=i"> . Let <img src="https://render.githubusercontent.com/render/math?math=a_{-i}"> be the action (or actions) of other agent(s). <img src="https://render.githubusercontent.com/render/math?math=r_i(a_{-i})"> is the reaction function, and <img src="https://render.githubusercontent.com/render/math?math=(a_i^*,a_{-i}^*)"> is an equilibrium if

<img src="https://render.githubusercontent.com/render/math?math=a_i^* = r_i(a_{-i}^*) \forall i">

Game theory becomes crucial in modeling when preferences (goals) of the agents diverge _and_ agents are interdependent. Examples may be hiring committees, market interactions between firms, R&D strategies, voting in teams, delegation of tasks, the provision of public goods, or social pressure.

Games on _networks_ are situations where the structure of interdependence can be represented by a network. This occurs when three or more agents interact, and not everyone is directly interdependent. Consider three actors _A_,_B_, and _C_ and assume _A_ is interdependent with _B_ but not with _C_:

  _A_<---> _B_ <---> _C_
  
We may now analyze this situation with pairwise dependencies between _A_ and _B_, as well as _B_ and _C_. If, however, _B_ anticipates in some way the actions of _A_ and _C_ when making his choice, then agent _A_'s payoff is now also indirectly influenced by the choice of _C_. We thus have to analyze a game on a network structure. Interdependencies can thus be direct, indirect or entirely absent.

The main thing to keep in mind is that the structure of interdependencies - aka the network - is the "parameter" of interest. Typically, the games we consider are already well understood. The fundamental question is how the presence or absence of interdependency might change the conclusions.

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

The current approach to the analysis of games on networks grows largely out of the analysis of peer groups. Indeed, networks are a generalization of peer groups.
In the group literature, it is assumed that an agent _A_ is part of one group and is subsequently affected (only) by the choices of all other agents in that group. It is easy to see that this corresponds to a block-diagonal adjacency matrix. It also means that everyone in a given group has the same "peers".
In contrast, the peer group in a general network is individual to each agent. _A_ and _B_ may be peers, but may have different peer groups nonetheless.

### Interdependencies are different kinds of externalities

What I broadly called "interdependencies" in the above may be more accurately described as "externalities". The choice of our agent, be it _a_ or _d_, depends on the choice of his peer because this choice exerts some effect on the utility of our focal agent. Since the utility is then changed by this "externality", our focal agent now wants to do something different. Externalities thus capture many types of interdependencies - tasks, information, outputs, etc.

The peer group literature already illustrates that different kind of externalities exist. I will tentatively sort them along two dimensions.

First, the *strategic dimension*. This dimension is most relevant when choices have magnitudes (number of produced widgets, dollars spent) or are at least in some sense ordinal. If the externality always has the same directional impact, then the aforementioned _reaction function_ behaves in predictable ways and we can neatly decide between two situations.

If the reaction of agent _A_ is _increasing_ in the actions of his or her peers, then we have *strategic complements*. For example, if my competitor starts to exert more effort, I need to increase my own effort levels to keep up. In math, <img src="https://render.githubusercontent.com/render/math?math=\frac{\partial r_i(a_j)}{\partial a_j}>0">

If the reaction of agent _A_ is instead _decreasing_ in the action of his or her peers, then we have *strategic substitutes*. For example, if my co-worker fills up the community coffee pot more often, I need to do it less often. In math, <img src="https://render.githubusercontent.com/render/math?math=\frac{\partial r_i(a_j)}{\partial a_j}<0">

The second *aggregation dimension* categorizes how the externalities of peers affect the focal agents utility. In peer groups, the focal agent is usually concerned with an aggregate such as the sum or average in the group. We can differentiate two cases:

First, 

#### Bénabou, R. (1996) ‘Equity and Efficiency in Human Capital Investment : The Local Connection’, The Review of Economic Studies, 63(2), pp. 237–264.

This model considers how parents might choose a community to live in. After moving, the community exerts a local effect on the children's quality of interaction and education. This local effect is determined by the average social capital in the community. For that reason, this paper is an early version of what will later be termed a "local average model".

#### Akerlof, G. A. (1997) ‘Social Distance and Social Decisions’, Econometrica, 65(5), pp. 1005–1027.

This paper is very significant for laying the groundwork of conformism and status models of social interactions. It already includes the formulation of utility (or valuation) that will be common in the later literature. Furthermore, Akerlof recognizes that peer effects have a strong tendency to create multiple equilibria. 

## Early applications of networks

## The game changer: Outcome as a function of network structure

## Quadratic games and recent developments

## Empirical issues

## Appendix: Equilibrium existence
