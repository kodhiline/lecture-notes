---
title: "sd causal loop diagram"
date: 2023-09-25T04:19:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi8093']
draft: false
math: true
url: "0064"
---
{{< toc >}}


## introduction
CLD or causal loop diagram is used to conceptually model dynamic systems in a holistic manner ([Marketlinks, 2019](https://www.marketlinks.org/resources/what-causal-loop-diagram-and-what-it-good)), since
+ it is a snapshot of all relations that matter,
+ it is a visual representation of key variables (i.e. factors, issues, processes) and how they are interconnected,
+ it shows the direction of causality, the nature of relationships (i.e. proportional or inverse), and whether there is any delay in an expected effects' occurence.

In CLD variables are represented as texts and causal relationships between them are represented as arrows.


## example
+ One of the common causal loop diagram is that represents relation between population, birth rate and dead rate ([Singh & Frostell, 2016](https://www.researchgate.net/publication/303943753_Beyond_Waste_Management)), which can be modified and drawn as follow
{{< mermaid >}}
flowchart LR
  P1 -.- P2
  D --"&rang;&#x2795;&rang;"---> P1
  P1 --"|&#x2796;|"---> D
  P2 --"|&#x2795;|"---> B
  B --"&lang;&#x2795;&lang;"---> P2
  subgraph BL["Balancing loop"]
    direction LR
    D(("Death rate"))
    P1(("Population"))
  end
  subgraph RL["Reinforcing loop"]
    direction LR
    P2(("Population"))
    B(("Birth rate"))
  end
  style BL rx:40, ry:40
  style RL rx:40, ry:40
  linkStyle default color:magenta
{{< /mermaid >}}

+ Population element should be in the same shape, but it is drawn separately as in above due to limitation of Mermaid ([Baketarić & Vinod, 2023](https://github.com/orgs/mermaid-js/discussions/4308#discussion-5100526)), in order to stress the two loops, balancing and reinforcing loops.
+ Common symbol for time delay is `||` which is used as `|+|` and `|-|` here.
+ The symbol `>>` or `<<` is for no time delay.


## equation
+ Population is symbolized with $P$.
+ Birth rate is defined as
$$\tag{1}
B_t = c_B P.
$$
+ Date rate is defined as
$$\tag{1}
D_t = c_D P.
$$
+ Rate of change of the population
