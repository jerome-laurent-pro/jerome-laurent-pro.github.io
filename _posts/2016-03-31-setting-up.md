---
layout: post
title: Setting up a blog
subtitle: With Jekyll, Github, Vagrant and knitr
---

### After a few hours, it finally works seamlessly.

I had this idea for several months since I randomly stumbled upon Github Pages. The first step was finding a Jekyll layout I liked.
Thankfully, **Dean Attali** has done an amazing job with his repository [beautiful jekyll](https://github.com/daattali/beautiful-jekyll). Very nice, easy to use and with a comprehensive readme, perfect to get started with [Jekyll](https://jekyllrb.com/).

After that, the hosting : [Github Pages](https://pages.github.com/) automatically host a website from a specific repository,  http://*username*.github.io. Pushing a local directory to Github is all that is needed.

The two lasts steps presented the most difficulties.

I wanted to use [Vagrant](https://www.vagrantup.com/) to host locally the website on a virtual machine, in order to check my work without pushing to Github. I first tried to follow this [blogpost](http://www.jamessturtevant.com/posts/running-jekyll-in-windows/) by James Sturtevant but I was unable to serve the website because of several issues with Ruby gems. Finally, I used the `Vagrantfile` contained in the *beautiful jekyll* repository and spent some time editing the `Gemfile` and the `Gemfile.lock` and rebuilding the VM to make the syntax highlighting work.

Lastly, I like to use the literate programming package `knitr` in `R` and thought it would be great to automatically generate posts from Rmarkdown files. I found several methods on the Internet and had the most success with this [one](https://github.com/dgrtwo/dgrtwo.github.com/blob/master/_scripts/knitpages.R) by [David Robinson](http://varianceexplained.org/pages/workflow/). It is a `R` file that compiles all `.Rmd` files into suitable `.md` files. It works perfectly and any `.Rmd` file can be transformed into a blogpost.
