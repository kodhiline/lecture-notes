---
title: "svg <path> element - bezier"
date: 2023-10-29T03:59:00+07:00
authors: ['Sparisoma Viridi']
tags: ['sk6091']
draft: false
math: true
url: "0125"
---
{{< toc >}}


## refs
+ Basic shapes ([MDN, 2023](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Basic_Shapes)).
+ Paths ([MDN, 2023](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths)).
+ &lt;text&gt; ([MDN, 2023](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/text)).
+ Answer to "vertical alignment of text element in SVG" ([West & Currie, 2016](https://stackoverflow.com/a/12250444/9475509))


## circle
{{< html >}}
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <circle cx="100" cy="100" r="50"/>
</svg>
{{< /html >}}
```svg
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <circle cx="100" cy="100" r="50"/>
</svg>
```


## line
{{< html >}}
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <line x1="50" x2="150" y1="50" y2="150"
      stroke="black" stroke-width="5" />
</svg>
{{< /html >}}
```svg
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <line x1="50" x2="150" y1="50" y2="150"
      stroke="black" stroke-width="5" />
</svg>
```

## text
{{< html >}}
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <text x="100" y="100" text-anchor="middle" 
      alignment-baseline="middle">(100, 100)</text>
    <circle cx="100" cy="100" r="5" fill="red" />
</svg>
{{< /html >}}
```svg
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <text x="100" y="100" text-anchor="middle" 
      alignment-baseline="middle">(100, 100)</text>
    <circle cx="100" cy="100" r="5" fill="red" />
</svg>
```

## circle-line-circle
{{< html >}}
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <circle cx="150" cy="50" r="4"/>
    <line x1="150" y1="50" x2="50" y2="150"  
      stroke="black" stroke-width="2" />
    <circle cx="50" cy="150" r="4"/>
</svg>
{{< /html >}}
```svg
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <circle cx="150" cy="50" r="4"/>
    <line x1="150" y1="50" x2="50" y2="150"  
      stroke="black" stroke-width="2" />
    <circle cx="50" cy="150" r="4"/>
</svg>
```


## path bezier
{{< html >}}
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <path  d="M 20 150 Q 100 50 180 150"
      stroke="black" stroke-width="3" fill="none" />
    <circle cx="20" cy="150" r="4" />
    <circle cx="100" cy="50" r="4" fill="red" />
    <circle cx="180" cy="150" r="4" />
    <line x1="20" y1="150" x2="100" y2="50"  
      stroke="red" stroke-width="1" stroke-dasharray="5 5" />
    <line x1="100" y1="50" x2="180" y2="150"  
      stroke="red" stroke-width="1" stroke-dasharray="5 5" />
    <text x="20" y="150" text-anchor="start" alignment-baseline="before-edge">(20, 150)</text>
    <text x="180" y="150" text-anchor="end" alignment-baseline="before-edge">(180, 150)</text>
    <text x="100" y="50" text-anchor="middle" alignment-baseline="after-edge">(180, 150)</text>
</svg>
{{< /html >}}
```svg
<svg
  version="1.1" xmlns="http://www.w3.org/2000/svg"
  width="200" height="200"
  style="background: #eee;">
    <path  d="M 20 150 Q 100 50 180 150"
      stroke="black" stroke-width="3" fill="none" />
</svg>
```
