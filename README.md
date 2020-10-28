# TOM Knowledge Repository: Games on Networks

In this repository, I would like to write down what I (think I) understand about the analysis of games with a network structure and the literature relating to it. I will also try to point out some papers on the empirical application of these issues. Please feel free to add corrections as you see fit.

## What are games on networks (for)?

Game Theory is fundamental for analyzing _strategic_ interactions of (possibly boundedly) rational agents. Interactions are strategic if agents anticipate the benefit of their choices conditional on what other agents might do now or in the future. Different from, say, models of mutual learning, agents in a game engage in acts of introspection about what other agents might do next.

Typically, each agent is afforded a reaction function: If a peer were to do action _a_, then our agent would want to do action _b_. If peer were to choose action _c_ instead, our agent would now want to choose _d_, and so on. An _equilibrium_ is a set of actions for each agent that is consistent with all these reaction functions: In an equilibrium, everyone is happy with their choice of action, given the choices of other agents. Game Theory typically doesn't specify _how_ we get to the equilibrium, it rather analyzes equilibriums directly. This makes these immensely complex behavioral problems amendable to formal analysis. On the other hand, it means that several equilibria may be viable in a given situation, and our model would require additional assumptions to pick which one will occur.

To formalize the above, let <img src="https://render.githubusercontent.com/render/math?math=a_i"> be the action of agent <img src="https://render.githubusercontent.com/render/math?math=i"> . Let <img src="https://render.githubusercontent.com/render/math?math=a_{-i}"> be the action (or actions) of other agent(s). <img src="https://render.githubusercontent.com/render/math?math=r_i(a_{-i})"> is the reaction function (also called best-reply function), and <img src="https://render.githubusercontent.com/render/math?math=(a_i^*,a_{-i}^*)"> is an equilibrium if

<img src="https://render.githubusercontent.com/render/math?math=a_i^* = r_i(a_{-i}^*) \forall i">

Game theory becomes crucial in modeling when preferences (goals) of the agents diverge _and_ agents are interdependent. Examples may be hiring committees, market interactions between firms, R&D strategies, voting in teams, delegation of tasks, the provision of public goods, or social pressure.

Games on _networks_ are situations where the structure of interdependence can be represented by a network. This occurs when three or more agents interact, and not everyone is directly interdependent. Consider three actors _A_,_B_, and _C_ and assume _A_ is interdependent with _B_ but not with _C_:

  _A_<---> _B_ <---> _C_
  
We may now analyze this situation with pairwise dependencies between _A_ and _B_, as well as _B_ and _C_. If, however, _B_ anticipates in some way the actions of _A_ and _C_ when making his choice, then agent _A_'s payoff is now also indirectly influenced by the choice of _C_. We thus have to analyze a game on a network structure. Interdependencies can thus be direct, indirect or entirely absent.

The main thing to keep in mind is that the structure of interdependencies - aka the network - is the "parameter" of interest. Typically, the games we consider are already well understood. The fundamental question is how the presence or absence of interdependency might change the conclusions.

An [adjacency matrix](https://en.wikipedia.org/wiki/Adjacency_matrix#Examples) represents these relationships succinctly.
These relationships can be fixed (or exogenous), or they could also depend on the agent's choices (and be endogenous). In the former case, we analyze a game on a network structure. In the latter case, we also analyze network formation (and the subsequent game). Naturally, there's also a large literature, predating the present topic, that focuses only on network formation without an attached game, however I will not get into these papers here.

The question of whether equilibria exist and whether they are stable, is crucial for analyzing Games. Once equilibria are defined, we are in a good position to analyze many aspects of the game. Further, whether we can order equilibria tells us a lot about the complexity of the game, and the multitude of empirical outcomes we may be able to observe.
Network effects, peer effects, externalities, interdependencies etc. are plenty in real life. It is crucial for us to understand what effects they may have!

Network theory is a huge subject in itself, spanning multiple fields and numerous applications. I will link where I can, but I have to assume some knowledge about networks.

Overall, the application of these models to organizational design, for example, seems valuable to me. It's clear that the structure of interdependence is crucial for OD. Strategic situations, those where incentives and preference diverge, have perhaps received less attention in our canonical models. For that reason, game theory and networks may be a worthwhile approach to think of some problems in the field.

## Implicit networks in the past literature

The analysis of networks as structural objects of interest is relatively new in Game Theory.
However, networks implicitly turned up in the analysis of informational dependence in Mechanism Design. If you don't know what that is, perhaps the following explanation suffices: If you are a designer, and you know that agents are going to be strategic, which game should you pick? For example, if you are Google, and you want to auction off ad-space, then which auction format is best? That's mechanism design (econ Nobel prize 2007). Auction design (econ Nobel prize 2020) and regulation (econ Nobel prize 2014) are prominent applications. Given that this affair is typically even more complex than the analysis of games, let me just give you two important references for completeness:

#### McAfee, R. P. and Reny, P. J. (1992) ‘Correlated Information and Mechanism Design’, Econometrica, 60, pp. 395–421. doi: 10.2307/2951601.

Private information (or types, or preferences) determine how much "power" an agent has in mechanism design. For example, a firm would like to know how much a customer is willing to spend. If however, two customers are known to have very similar tastes (their private information is correlated), then finding out about one tells me about the other. McAfee and Reny analyze the consequence of such correlations.

#### Jehiel, P. and Moldovanu, B. (2001) ‘Efficient Design with Interdependent Valuations’, Econometrica, 69(5), pp. 1237–1259. doi: 10.1111/1468-0262.00240.

This paper not only assumes that private information may be correlated, but that the types of other players may also influence the payoffs directly.

While a network of interdependence exists in this literature, it is typically assumed to be random. For that reason, said network is not the primary object of analysis.

## Groups as a precursor to networks

The current approach to the analysis of games on networks grows largely out of the analysis of peer groups. Indeed, networks are a generalization of peer groups. Furthermore, it draws from statistical physics, although later models tend to grow back into the economics and game theory canon.

In the group literature, it is assumed that an agent _A_ is part of one group and is subsequently affected (only) by the choices of all other agents in that group. It is easy to see that this corresponds to a block-diagonal adjacency matrix. It also means that everyone in a given group has the same "peers".
In contrast, the peer group in a general network is individual to each agent. _A_ and _B_ may be peers, but may have different peer groups nonetheless.

While the papers below tackle many important substantive issues, such as community effects, inequality, schooling, competition and team performance, I will focus on the technical aspects. This is in part because many results and modeling approaches for peer groups are valid for games on networks. It seems like a good idea to get a sense of these issues in this simpler framework.

### Interdependencies are different kinds of externalities

What I broadly called "interdependencies" in the above may be more accurately described as "externalities". The choice of our agent, be it _a_ or _d_, depends on the choice of his peer because this choice exerts some effect on the utility of our focal agent. Since the utility is then changed by this "externality", our focal agent now wants to do something different. Externalities thus capture many types of interdependencies - tasks, information, outputs, etc.

The peer group literature already illustrates that different kind of externalities exist. I will tentatively sort them along two dimensions.

First, the *strategic dimension*. This dimension is most relevant when choices have magnitudes (number of produced widgets, dollars spent) or are at least in some sense ordinal. If the externality always has the same directional impact, then the aforementioned _reaction function_ behaves in predictable ways and we can neatly decide between two situations. In addition to determining the main results, these distinctions will matter for finding the equilibria.

If the reaction of agent _A_ is _increasing_ in the actions of his or her peers, then we have *strategic complements*. For example, if my competitor starts to exert more effort, I need to increase my own effort levels to keep up. In math, <img src="https://render.githubusercontent.com/render/math?math=\frac{\partial r_i(a_j)}{\partial a_j}>0">

If the reaction of agent _A_ is instead _decreasing_ in the action of his or her peers, then we have *strategic substitutes*. For example, if my co-worker fills up the community coffee pot more often, I need to do it less often. In math, <img src="https://render.githubusercontent.com/render/math?math=\frac{\partial r_i(a_j)}{\partial a_j}<0">

The second *aggregation dimension* categorizes how the externalities of peers affect the focal agents utility. In peer groups, the focal agent is usually concerned with an aggregate such as the sum or average in the group. We can differentiate two cases:

First, the focal agent might _compare_ himself to the average action in the peer group. This is called the *local average model*. It often describes conformism or status.

Second, the focal agent's payoff might be multiplicatively influenced by the actions of the peer group. This is then called the *local aggregate model*. It often describes interdependent production or public goods.

All four combinations are possible, and furthermore, many games don't fall in any of these categories. As it turns out, however, most do.

#### Bénabou, R. (1996) ‘Equity and Efficiency in Human Capital Investment : The Local Connection’, The Review of Economic Studies, 63(2), pp. 237–264.

This model considers how parents might choose a community to live in. After moving, the community exerts a local effect on the children's quality of interaction and education. This local effect is determined by the average social capital in the community. For that reason, this paper is an early version of the local average model.

#### Akerlof, G. A. (1997) ‘Social Distance and Social Decisions’, Econometrica, 65(5), pp. 1005–1027.

This paper is very significant for laying the groundwork of conformism and status models of social interactions. It already includes the formulation of utility (or valuation) that will be common in the later literature. Furthermore, Akerlof recognizes that peer effects have a strong tendency to create multiple equilibria. 
He analyzes local average models, where agents either care about out-performing their peers (called status model), or seek to minimize deviation ('social distance') from the group average (called conformism model).

#### Clark, A. E. and Oswald, A. J. (1998) ‘Comparison-concave utility and following behaviour in social and economic settings’, Journal of Public Economics, 70(1), pp. 133–155. doi: 10.1016/S0047-2727(98)00064-4.

Where Akerlof presents the *aggregation dimension*, the paper by Clark and Oswald analyzes the *strategic dimension* in a peer group setting. The authors frame this as a game between leaders and followers.

#### Akerlof, G. A. and Kranton, R. E. (2000) ‘Economics and identity’, The quarterly journal of economics, 115(3), pp. 715–753.

In this work, agents belong to social categories that combine to form an individual identity. For example, one could be male or female, car mechanic or hairdresser. Akerlof and Kranton then assume that each social category comes with a prescription of what an agent _should_ do, and an agent may benefit from conforming or deviation from said prescription. This, again, is a variation of the local-average conformism model

#### Durlauf, S. N. and Brock, W. A. (2001) ‘Discrete choice with social interactions’, Review of Economic Studies, 68(2), pp. 235–260. doi: 10.1111/1467-937x.00168.

Brock and Durlauf present a more general model of binary choice and social interactions. They assume that the properties of peers may be unknown to the focal agent. Most importantly, this is the first model to consider both local-average and local-aggregate formulations. In addition to multiple equilibria, the authors also find that local-average and local-aggregate differ only in level: They lead to the same econometric model and are - at least in peer groups - not separately identified. This problem will keep the subsequent literature busy for many years to come.

#### Glaeser, E. L., Scheinkman, J. A. and Sacerdote, B. I. (2003) ‘The Social Multiplier’, Journal of the European Economic Association, 1(2). doi: 10.1108/ilds.2002.12230dab.004.

Like the above paper, this one has both a formal-theoretical and an econometric part. As example, they consider beer consumption in college for different peer groups (fraternities, non-fraternities and so on). This illustrates an all-important concept called the _social multiplier_: The aggregate action - the "sum of outputs" of a peer group is higher than the sum of outputs if the agents were isolated. The total is more than the sum of its parts. The interaction structure can have its own multiplicative effect on the aggregate result. Ultimately, this is the motivation to study games on networks.

Finally, I highly recommend this article. If you read only one paper from this section, I recommend:

#### Glaeser, E. L. and Scheinkman, J. (2000) Non-market interactions. National Bureau of Economic Research.

Here, we have peer or reference groups, but each agent can have multiple ones, bringing us close to a network situation. Furthermore, this paper tries to provide a more general framework to analyze social interactions and shows some of the key issues, such as multiple equilibria. It also shows that complements are not a necessary nor sufficient condition for multiple equilibria to occur. Instead, multiple equilibria are likely to occur when interdependencies are strong. It also gives an overview of mean-field analysis, which is often useful to simplify the issues under consideration.

## Early applications of games on networks

Here are some examples of early papers of games on networks. 

#### Bala, V. and Goyal, S. (1998) ‘Learning from Neighbours’, Review of Economic Studies, 65(3), pp. 595–621. doi: 10.1111/1467-937X.00059.

A bayesian learning model with a network structure, even though it is not yet called a network structure but rather a set of individual neighborhoods. Learning here has a "conformism" effect (see above) and the authors find that, in the long run, all actors will achieve the same payoff due to social learning. This equalization of outcomes in local-average models appears in many subsequent papers. But is it truly a general result?

#### Bala, V. and Goyal, S. (2001) ‘Conformism and diversity under social learning’, Economic Theory, 17(1), pp. 101–120. doi: 10.1007/PL00004094.

This follow-up paper shows that diverse outcomes (or opinions) can co-exist, if the intensity of interaction between groups differs from the intensity within group. As of yet unrecognized is the general insight: The _symmetry_ of social interacts is a crucial determinant of diversity or conformism.

#### Kranton, R. E. and Minehart, D. F. (2001) ‘A Theory of Buyer-Seller Networks’, THE AMERICAN ECONOMIC REVIEW, 91(3), p. 30.

One of the first economics papers that explicitly considers networks. For the most part, these are bi-partite networks of buyers and sellers which lend themselves to well-known graph theoretic results about matching. This work is less concerned with the competition on the network than with the fact that endogenously formed buyer-seller networks can indeed lead to the welfare maximal outcome for society.

#### Bramoullé, Y. (2007) ‘Anti-coordination and social interactions’, Games and Economic Behavior, 58(1), pp. 30–49. doi: 10.1016/j.geb.2005.12.006.

This is a different approach to games on networks that is less influenial. In this setup, players who are connected meet to play an anti-coordination game: A discrete version of strategic substitutes. A classic example is the game of chicken: Two cars race towards each other and neither wants to be the first to deviate. Both, however, do not want to crash. In this model, each player picks one strategy to play against all neighbors in the network. Thus, we have a direct and indirect network effects. The downside of this approach is visible in this work: While there are nice predictions on how specific networks affect play, it is difficult to find general results about how network structure affects the behavior.

#### Kearns, M., Littman, M. L. and Singh, S. (2013) ‘Graphical models for game theory’, arXiv preprint arXiv:1301.2281.

I felt it important to present at least one paper outside of economics. Game Theory in Computer Science deals primarily with the complexity of finding equilibria, so this paper is a good example of how that looks.

## The game changer(s): Outcome as explicit function of network structure

At this point in time, authors started to propose some general frameworks to analyze games on networks. One example is Galeotti, A. et al. (2009) ‘Network Games’, Review of Economic Studies, 77(1), pp. 218–244. doi: 10.1111/j.1467-937X.2009.00570.x.

However, the most influential works actually took a step back from generality. These sets of papers assumed quadratic utility functions, or any utility function that gives first-order conditions linear in the peer effects. Specific functional forms of utility are of course  a rather strong assumption. If networks are involved, however, it turns out to be extremely valuable: Quadratic utilities have linear best-reply functions. Actions can then be described as affine functions involving the adjacency matrix, which allows to leverage linear algebra to understand the impact of the network on the choices of agents. Furthermore, with this approach, the literature start to understand when and in what fashion multiple equilibria could occur.

The first paper I'd like to highlight is

#### Bramoullé, Y. and Kranton, R. (2007) ‘Public goods in networks’, Journal of Economic Theory, 135(1), pp. 478–494. doi: 10.1016/j.jet.2006.06.006.

This paper deals with strong substitutes in local-aggregates, which we can understand as public goods: Everyone wants something, but it's sufficient that one neighbor provides it. While it does not yet provide a neat solution, this paper with its strong substitutive peer effects represents one extreme.

The other extreme comes from a much more influential work

### Ballester, C., Calvó‐Armengol, A. and Zenou, Y. (2006) ‘Who’s Who in Networks. Wanted: The Key Player’, Econometrica, 74(5), pp. 1403–1417. doi: 10.1111/j.1468-0262.2006.00709.x.

This paper studies both substitutes and complements for small peer effects. What the authors manage to do, however, is to provide an explicit relationship of equilibrium actions and (any) network structure. They show, that choices in their game are proportional to the [(Bonacich) centralities](https://en.wikipedia.org/wiki/Eigenvector_centrality) of agents. That is, what agents do is determined by their structural position in the network. Centrality has long been ... central ... in empirical studies, in particular in sociology. Social status, for example, is most often defined as centrality in the social network. This paper shows fundamentally why this measure occurs time and time again in human interactions. Further, the authors show that the existence of an equilibrium hinges on the largest eigenvalue of the adjacency matrix - or more generally, its spectral radius. If peer effects, and thereby the spectral radius of the adjacency matrix, are small enough, then we get a unique equilibrium.

The paper doesn't do an excellent job of highlighting all the important results it contains. The same authors published a shorter version, focused on strategic complements, which provides a much easier description: Corbo J.a Calvó-Armengol, A. b P. D. a (2006) ‘A study of nash equilibrium in contribution games for peer-to-peer networks’, Operating Systems Review (ACM), 40(3), pp. 61–66. doi: 10.1145/1151374.1151388.

Finally, the general solution to quadratic utility games on network got worked out - including both substitutes and complements, large and small peer effects, as well as local-aggregates and local-averages.
I consider this the most important paper in this document, so it's the one you should read for sure:

### Bramoullé, Y., Kranton, R. and D’Amours, M. (2014) ‘Strategic Interaction and Networks’, American Economic Review, 104(3), pp. 898–930. doi: 10.1257/aer.104.3.898.

Using a streamlined version of the prior paper, the authors unify both extreme cases and show that the results obtained, such as a unique equilibrium with strategic complements, are not generic. Proportionality to centrality also only holds on subgraphs.
The paper focuses first on substitutes. In that case, equilibria are unique if and only if the magnitude of the lowest eigenvalue of the adjacency matrix is small. This is a more precise condition than the magnitude of the largest eigenvalue, which is for example used when obtaining the Bonacich centrality in a network. If the smallest eigenvalue has a large magnitude (positive or negative), there are multiple equilibria with inactive agents. If an equilibrium is unqiue, it is stable. If an equilibrium is stable, then there is no other stable equilibrium with more active agents.
The authors can then show comparative statics: If the network effects increase, then the actions of agents move into the same direction.

The approach in this paper is not fully general. While peer effects can be substitutes or complements, the authors require them to be symmetric. This is because they use _potential functions_ to find equilibria: They seek a global "potential" describing the actions in the network, which can be optimized instead of optimizing for each agent separately.

## Network structure and eigenvalues

Why do the eigenvalues of the adjacency matrix matter? Previous papers have shown that when the lowest eigenvalue has a high magnitude (or absolute value), then substitutive relationships lead to fluctuation in best responses that bounce through the network. With a high magnitude lowest eigenvalue, the network is more two-sided, thus solutions are more likely to fluctuate "globally". That is when we find multiple equilibria.
What about strategic complements? Since actions here "multiply" each other, multiple equilibria are not related to fluctuations in the best-reply dynamics. Instead, we care about the largest eigenvalue, the spectral radius, and multiple equilibria occur due to bounds or discontinuities in the action space.

In both cases, the spectra of the adjacency matrix determine whether agents take more or less extreme actions, depending on their position in the social network. Having found the connection between network games and adjacency matrices, allows to leverage spectral graph theory to understand how a complex concept like "changing the network" influences agents' decisions. See for example Harkins, A. (2020) ‘Network Comparative Statics’, p. 45.

## Recent developments

There are several additions I would like to highlight. There are, of course, a lot of applications of the above frameworks. As an example, here is a paper analyzing networked markets based on the above framework:

#### Bimpikis, K. and Ehsani, S. (2019) ‘Cournot Competition in Networked Markets’, Management Science, p. 42.

Using network games, the authors can show how the presence of firms in different markets leads to connections that impact pricing and output behavior and has consequences for regulation and competition policy.


However, two theoretical issues remain. First, what about the distinction between local-aggregate and local-average models? Where do these terms even come from?
The above papers nest both cases, however they do not analyze local-average models explicitly. The reason is that local-average models usually have a unique equilibrium. If an agent compares his action against that of his peers, then the adjacency matrix becomes stochastic - rows sum to unity. Then, the highest eigenvalue, say, is going to be one, and we have no issue with equilibria. However, local-average models are substantively interesting, such that they now receive more attention in the literature:

#### Ushchev, P. and Zenou, Y. (2019) ‘Social Norms in Networks’, p. 97.


Secondly, there is still some more work to do to achieve generality. Previous papers, in addition to having only linear reaction functions, required the network ties to be symmetric i.e. undirected. This does not reflect all organizational situations, for example when attention is involved: I can pay attention to someone without the reverse being true. As it turns out, potential function approaches to do not apply here. Instead, we again have to look at substitutes and complements separately. For substitutes, the difficulty of finding equilibria is well known in economics and there seems to be no general solution. We can relax at least the condition of linearity of best-replies by using variational inequalities:

#### Melo, E. (2018) A Variational Approach to Network Games. Working Paper 2018.05..


However, for complements, we can go further. The provably most general approach to find equilibria has been identified by:

#### Milgrom, P. and Shannon, C. (1994) ‘Monotone Comparative Statics’, Econometrica, 62(1), p. 157. doi: 10.2307/2951479.

This paper shows that we can actually do comparative statics - equilibrium analysis - for games in which decision variables are merely ordinal (precisely, when the action space is a lattice). If the utility function is _quasi-supermodular_, a generalization of complementarity, then equilibria can be analyzed for the impact of parameters quite generally. Indeed, this is the most general way one can analyze choice situations, as the authors show.

Using this approach for network games led to this paper

#### Belhaj, M., Bramoullé, Y. and Deroïan, F. (2014) ‘Network games under strategic complementarities’, Games and Economic Behavior, 88, pp. 310–319. doi: 10.1016/j.geb.2014.10.009.

As far as I know, this is the most general approach for analyzing network games with strategic complements.

## Empirical Applications

The empirical literature on networks is much larger. The analysis of network games has clarified some issues that crop up when using data. Multiple equilibria means that identification is a challenge. Outputs being related to the eigenvalue and centralities of a matrix implies that peer effects, if unobserved or not accounted for correctly, will bias traditional econometric approaches in almost every setting. Finally, if networks are endogenous, a strong selection effect is to be expected.

The issue of identification has been raised first by Manski for peer groups:

#### Manski, C. F. (1993) ‘Identification of Endogenous Social Effects: The Reflection Problem’, The Review of Economic Studies, 60(3), p. 531. doi: 10.2307/2298123.

Insights from network game models were then used to show how peer effects can be identified:

#### Bramoullé, Y., Djebbari, H. and Fortin, B. (2009) ‘Identification of peer effects through social networks’, Journal of Econometrics, 150, pp. 41–55.

The distinction of local-average and local-aggregate effects led us to understand how networks may or may not multiply behavior, shocks, policy interventions or organizational design factors:

#### Liu, X., Patacchini, E. and Zenou, Y. (2014) ‘Endogenous peer effects: local aggregate or local average?’, Journal of Economic Behavior & Organization, 103, pp. 39–59. doi: 10.1016/j.jebo.2014.03.025.

An approach to tackling endogenous networks has been raised by:

#### Boucher, V. (2016) ‘Conformism and self-selection in social networks’, Journal of Public Economics, 136(November), pp. 30–44. doi: 10.1016/j.jpubeco.2016.02.005.

Finally, the literature now turns to the identification of networks and network effects when the data are incomplete, or networks are not directly observable.

#### Battaglini, M. et al. (2020) A Graphical Lasso Approach to Estimating Network Connections: The Case of U.S. Lawmakers. w27557. Cambridge, MA: National Bureau of Economic Research, p. w27557. doi: 10.3386/w27557.
