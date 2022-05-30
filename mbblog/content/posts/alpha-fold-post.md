---
title: "AlphaFold 2 Interpretability"                                           
date: 2021-10-02T01:40:07+01:00                                                                                         
---  

I never completely understood why interpretability of artificial intelligence, 
or understanding the reasoning behind predictions made by a model,
was so important.

It didn't seem as though it would contribute very much to solving intelligence itself,
since our own brains creatively and intelligently produce great works, 
without anyone really knowing the work's exact inspiration, 
or how that inspiration set off the chain of calculations that produced the work.
Both poker and chess players often intuit their next move without having a concrete notion of how they came to it.

I also understood where people like Yann LeCun were coming from, 
when they said that if the interpretability of a model comes at a cost to it's prediction ability, 
then it's probably not worth bearing, since all we really want are models, 
which are better at their given job. 

I've rethought my position, since a conversation I heard about AlphaFold 2.

Some time ago, AlphaFold 2 had a remarkable result in the longstanding problem of protein folding, 
or understanding the process by which a protein chain converts into a three-dimensional structure.
This result was commented on by Bret Weinstein and Heather Heying, whose reaction was enlightening.

In biology, a story is told, in which genes undergo mutations, mostly neutral or harmful. 
However, every so often by random chance a mutation is beneficial and contributes to fitness.
Eventually, after many iterations, we would get the flora and fauna of today.
The question is: Is the mechanism of random chance really poweful enough to generate the complexity and diversity that we see in life forms?

![Darwin's Finches](/xkcd.AnoleTree.png)

Bret Weinstein's view is no, and in relation to protein folding, the process is too weak to create the marvelous, little machines of folded proteins, known as protein conformations.
Additionally, slight variations of protein conformations do not change one type of amphibian into another.
Weinstein proposes 'explorer modes' as a better explanation. 
This proposal suggests that selection will discover mechanisms to search design space more efficiently than pure random search.
In other words, selection itself will have heuristics.

With regards to AlphaFold 2's amazing result in the protein folding competition,
Weinstein's hypothesis is that the model latched onto the products of the selection heuristics and worked it's way back to the resulting fold.
To the extent that there are patterns or themes in the folded up proteins, these could be the result of a heuristic that only investigates certain parts of the search space, 
withgoing the intervening space.
The hope is that Alphafold 2 would pick up on these heuristics and could ultimately tell us how the design space is searched.

So I wanted to see if this question had been answered, or if it even could be answered.
