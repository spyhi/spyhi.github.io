---
layout: essay
type: essay
title: The Way We Code
date: 2016-09-22
labels:
  - Coding Standards
  - JavaScript
---

<img class="ui fluid image" src="../images/the-way-we-code.jpg">

They say "hell is other people," but in the world of software engineering, the phrase is probably closer to "hell is other people's code." Spaghetti code is probably among the number one complaints of engineers inheriting legacy code, so much that many prefer doing work over instead of untangling twin Gordian knots of logic and unreadable syntax. These hours of lost engineering time is why coding standards are important.

The most basic reason for coding standards is readability. The human brain doesn't really recognize words so much as the shapes of words, which is why unusual fonts, bad layouts impact, or unfamiliar words will have an outsize impact on reading speed. The same is true of code. With code blocks alone, glanceability is hugely important and poor standardization can make parsing logic into an ordeal, but there are smaller things, too, such as creating breaks in logical places, which makes reading something like

```
const flat = {};
[[0, 1],[2, 3],[4, 5]].reduce((memo,item,index)=>{
const flatten=memo.concat(item);
flat[index]=flatten; return flatten;});
```

much harder than (with only minor modifications) reading something like

```
const flat = {};
[[0, 1], [2, 3], [4, 5]].reduce((memo, item, index) => {
  const flatten = memo.concat(item);
  flat[index] = flatten;
  return flatten;
});
```

(Source: [AirBnB JS Style Guide](https://github.com/airbnb/javascript#arrays--callback-return))

There are other, more important, reasons for coding standards, too. In a previous essay, I referenced how JavaScript's determination to run no matter what can [lead to as many problems](https://spyhi.github.io/essays/reflecting-on-learning-javascript.html) as it does creative solutions. JS is open and willing to take nearly any style of programming, from the top-down models of yore, to object orientation, to functional programming, which means that the logical constructs used to solve a problem may be opaque to team members, especially without documentation, making it a particularly risky language to use in a scenario with large teams and loose standards.

For example, if a coder uses `var` in a shop that uses `let` to control scoping, it risks creating a confusing bug due to the global nature of `var`, which doesn't stay confined to its code block and can creep into other namespaces, and since it's a bug that the `let` coder didn't introduce and isn't aware of where it came from, it could be extremely difficult to diagnose, costing heaps of engineering time that would be better spent on other more pressing problems.

One tool to deal with this is ESlint, which does code inspections in real time, ensuring that coding standards are enforced and throwing errors and red squigglies (that's a technical term) when those standards are not being met. This sort of automation allows me to skip memorizing all the rules and get to coding sooner, and correcting my style as the rules are broken, which is a great way of learning, too. Over time, I've produced less and less angry squgglies, so ESlint does a good job of training users to the style, too.

The result of coding standards and access automated tools has been that my code has been easier to parse at a glance, and it's been easier to collaborate with others, since I can read their code more easily, and I can expect their code to play with mine in a certain, amicable way. And in the end, that's made working with a team a lot less infernal.
