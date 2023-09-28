---
title: "svg element with js"
date: 2023-09-28T14:12:00+07:00
authors: ['Sparisoma Viridi']
tags: ['xx1000']
draft: false
math: true
url: "0073"
---
{{< toc >}}

# introduction
+ SVG element in a HTML page can be created dynamically using JavaScript and customized its sub-elements, which is a little bit different than in createing HTML element since SVG is described in XML ([Quante, 2021](https://blog.q-bit.me/how-to-create-svg-elements-with-javascript/)).
+ Using only pure JavaScript or known as Vanilla JavaScript, without help from any JS libraries or frameworks, SVG elements can be created and manipulated easily but with slightly different way than in handling HTML elemements, e.g. it is used `createElementNS` instead of just `createElement` ([Katz, 2021](https://javascript.plainenglish.io/how-to-create-an-svg-element-with-vanilla-javascript-a6b140745196)).
+ Pablo, as a lightweight, open source library, can be used for this purpose, since it is simplifying the construction and manipulation of SVGs in JavaScript, that enables developers to more easily work with dynamically generated vector graphics while avoiding the verbose workflow of vanilla JavaScript ([Omotayo, 2022](https://blog.logrocket.com/building-svgs-javascript-pablo/)).


##
+ ([Roblewsky, 2020](https://www.motiontricks.com/creating-dynamic-svg-elements-with-javascript/)).
+ ([Borb&eacute;ly, 2021](https://www.freecodecamp.org/news/svg-javascript-tutorial/)).