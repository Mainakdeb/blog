+++
title =  "Diving into Cellular Automata"
tags = ["Emergent Systems", "Cellular Automata"]
date = "2022-06-03"
+++

I remember [Vsauce](https://twitter.com/tweetsauce)(Michael Stevens) tweeting out a link to one of [Alan Zucconi's videos](https://www.youtube.com/watch?v=Kk2MH9O4pXY) about John Conway's game of Life. This is what pulled me into the world of Cellular Automata. 

Wolfram's Rule-30 is something that had me scratching my head, but why? 🤔

## Elementary Cellular Automaton and Rule 30:
Consider a 1-D realm with alive or dead cells. As we iterate over generations, the new state of a cell will only depend on  its nearest neighbors and past state.  A set of rules for this 1-D world could be:

<center><img src="../images/Cellular-Automata/rule_30.svg" width=500 ></center>
<p align="center">
<a href="https://mathworld.wolfram.com/ElementaryCellularAutomaton.html"><i>Image Source</i></a>
</p>

Note: cells below represent new cell states. Rule outcomes encoded in binary -> 30 = 00011110<sub>2</sub>

Starting from one single black cell we get the following generations. 

<center><img src="../images/Cellular-Automata/rule_30_output.png" width=600></center>
<p align="center">
<a href="https://mathworld.wolfram.com/Rule30.html
"><i>Image Source</i></a>
</p>

The remarkable thing about this rule is its chaotic nature, notably the middle column. In fact, this rule is often employed to generate random integers. Generating _chaos_ from _rules_ 👀

In case you're up for a challenge, Wolfram poses 3 problems concerning random nature of the center column, $30,000 for 3 problems -> [www.rule30prize.org](https://www.rule30prize.org/)

## Conway's Game of Life
Named after its creator [John Horton Conway](https://en.wikipedia.org/wiki/John_Horton_Conway), it features an infinite 2D grid-world of cells, having 2 possible states, _live_ or _dead_.  Each cell can only perceive its 8 neighbors, with rules shown below:

<center><img src="../images/Cellular-Automata/GOL_rules.png" width=400 > </center>
<p align="center">
<a href="https://www.researchgate.net/figure/Rules-of-Conways-Game-of-Life_fig5_339605473"><i>Image Source</i></a>
</p>

 Rules for Game of Life:
 1. Any live cell with two or three live neighbours survives.
2.  Any dead cell with three live neighbours becomes a live cell.
3.  All other live cells die in the next generation. Similarly, all other dead cells stay dead.

<center><img src="../images/Cellular-Automata/GOL_iterations.gif" width=250 ></center>
<p align="center">
<a href="https://github.com/woodruffw/CGoL
"><i>Image Source</i></a>
</p>

Turns out, Game of Life is [Turing complete](https://en.wikipedia.org/wiki/Turing_completeness). Paul Rendell designed a [Turing Machine in Game of Life](http://rendell-attic.org/gol/tm.htm) back in 2000.

<center><img src="https://media.arxiv-vanity.com/render-output/5370836/x9.png" width=550 >
</center>
<p align="center">
<a href="https://media.arxiv-vanity.com/render-output/5370836/x9.png"><i>Image Source</i></a>
</p>

Later in the year 2016, Nicolas Loizeau designed a [programmable 8-bit computer in Game of Life](https://conwaylife.com/wiki/8-bit_programmable_computer) which too is a sight to behold. 

<center><img src="https://i.ytimg.com/vi/8unMqSp0bFY/maxresdefault.jpg" width=500 >
</center>
<p align="center">
<a href="https://www.youtube.com/watch?v=8unMqSp0bFY"><i>Screenshot from Nicolas Loizeau's Video</i></a>
</p>

## Simulating Life Within Life - Droste Effect in Conway's Game of Life
Droste effect is the effect of a picture recursively appearing within itself.  The game of life is turing complete, which enables one to  simulate Life within itself as demonstrated in [this video](https://www.youtube.com/watch?v=xP5-iIeKXE8)  by Philip Bradbury. Following is a screenshot from Bradbury's video.

<img src="../images/Cellular-Automata/droste_effect_in_GOL.png" width=800 >
<p align="center">
<a href="https://www.youtube.com/watch?v=xP5-iIeKXE8"><i>Screenshot from Philip Bradbury's Video</i></a>
</p>

Life is a game with no players, a game that never ends, a game that sometimes plays itself 🎮