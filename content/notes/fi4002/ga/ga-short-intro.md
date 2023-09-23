---
title: "ga short intro"
date: 2023-09-21T19:07:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi4002']
draft: false
math: true
url: "0062"
---
{{< toc >}}


## introduction
+ Genetic algorithm or GA is an algorithm for optimization, which can avoid to land on local optimum in while searching global otimum ([Binus, 2018](https://socs.binus.ac.id/2018/12/08/genetic-algorithm/)).
+ This heuristic search is inspired by Charles Darwin's theory of natural evolution, which reflects the process of natural selection where the fittest individuals are selected for reproduction in order to produce offspring of the next generation ([Mallawaarachchi, 2017](https://towardsdatascience.com/introduction-to-genetic-algorithms-including-example-code-e396e98d8bf3)).
+ It is intelligent exploitation of random search provided with historical data to direct the search into the region of better performance in solution space, where it commonly used to generate high-quality solutions for optimization problems and seach problems ([overide, 2023](https://www.geeksforgeeks.org/genetic-algorithms/)).


## applications
+ One of the major applicaton of GA is the travelling salesman problem and this algorithm is also widely used in the field of robotics ([Pedamkar, 2023](https://www.educba.com/what-is-genetic-algorithm/)).
+ At least there are 10 real-life applications of GA, which are traveling salesman problem, vehicle routing problem, financial markets, manufacturing system, mechanical engineering design, data clustering and mining, image processing, neural networks, wireless sensor networks, and medical science ([Verma, 2022](https://analyticsindiamag.com/10-real-life-applications-of-genetic-optimization/))
+ There is also a list of applications of GA categorized according to the fields, e.g. i) natural sciences, mathematics, and computer science, ii) earth sciences, finance and economics, iii) social sciences, iv) industry, management, and engineering, v) biological science and bioinformatics, vi) general applications, vii) physics, and viii) others ([Wikipedia, 2023](https://en.wikipedia.org/w/index.php?oldid=1173413907)).


## terminology
+ There are some terms used in GA ([Muthee, 2021](https://www.section.io/engineering-education/the-basics-of-genetic-algorithms-in-ml/)), which are
  - Population, which is a subset of all probable solutions that can solve the given problem,
  - Chromosome, which is one of the solution in the population,
  - Gene, which is an element in a chromosome,
  - Allele, which is the value give to a gene in a specific chromosome,
  - Fitness function, that maps the solution to its suitability in solving the problem,
  - Genetic operators, which are used to change the genetic composition of next generation from information of previous generation.
+ Other term is individual, which is encoded in a chromosome ([Ray, 2016](https://stackoverflow.com/a/39740926/9475509)).


## operators
There are four operators used in GA during the search process, which are ([Katoch et al., 2021](https://doi.org/10.1007/s11042-020-10139-6))
+ Encoding: binary, octal, hexadecimal, permutation, value, tree;
+ Selection: roulette wheel, rank, tournament, Boltzmann, stochastic unversal;
+ Crossover: single point, k-point, uniform, partially mapped, order, precedence preserving, shuffle, reduced surrogate, cycle;
+ Mutation: displacement, inversion, scramble, bit flipping, reversing.
