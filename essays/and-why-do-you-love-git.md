---
layout: essay
type: essay
title: ...And Why Do You Love Git?
date: 2016-09-15
labels:
  - Git
  - Configuration Management
  - Version Control
---

<img class="ui fluid image" src="../images/why-love-git.jpg">

There is a common quip among the developer community that goes "What is your favorite version control manager, and why do you love Git?" The effusiveness of the community starts to make sense when you realize that git is relatively new (circa 2005), and so revolutionary that it achieved ubiquity with breakneck speed.

What's magical about git is how easy it is to branch and merge--the operations are painless and nearly instant. Though it seems like an obvious approach today, it wasn't always that way, and collaborators used to dread the difficult, day-long process of merging work back into the master, which Linus Torvalds referred to in his talk about git at Google, receiving rueful chuckles from the assembled developers. I've even experienced some of this in my early days as a computer science student at the University of Hawaii, when I would have to email files back and forth with team members (that most primitive of version control versions) in my ICS101 class, manually having to figure out what changes collaborators had made and whether `project1-final-final-final.java` is really as final as it claims to be.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4XpnKHJAok8" frameborder="0" allowfullscreen></iframe>

And it's not just the process of merging and branching that's magical, it's also being able to see a history of everyone's changes going back to the origination of the document, and being able to easily resolve merge conflicts. This makes massive amounts of branching easy and, by extension, Git makes working on a team as easy as possible.

Another useful feature of git and configuration management is the ability to store configuration information to help maintain a consistent development environment across teams and even various computers for a single coder. For example, a meteor project keeps a list of the npm packages it uses in a `pakcage.json` file, which puts a new team member one `meteor npm install` from being productive, and it's easy to get spun up when a team member decides to add (or remove) another package.

Linus said that making version control into an O(1) operation alters the way developers collaborate and manage their code, and it's completely true. So, now you'll probably catch me quipping "...and why do you love git," too.
