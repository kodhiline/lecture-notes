---
title: "svg g element"
date: 2023-09-30T12:50:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi4002']
draft: false
math: true
url: "0075"
---
{{< toc >}}


## introduction
+ The `<g>` element groups all of its decendants in one group, which makes it is easy to add styles, transformation, interactivity, and even animations to the entire group of objects ([Soueidan, 2014](https://www.sarasoueidan.com/blog/structuring-grouping-referencing-in-svg/)).
+ Transformation applied to the `<g>` element are also performed on its child elements, and its attributes are inherited by its children, including core, styling, conditional, and presentation attributes ([taran910, 2022](https://www.geeksforgeeks.org/svg-g-element/)).
+ With `<g>` element the grouped elements can be reused as if they were a single element, that is an advantage compared to a nested `<svg>` element which cannot be the target of transformation itself ([Jenkov, 2014](https://jenkov.com/tutorials/svg/g-element.html)).