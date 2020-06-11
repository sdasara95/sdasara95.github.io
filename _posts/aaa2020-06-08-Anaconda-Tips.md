---
layout: post
title: Anaconda Tips
subtitle: Some Useful Commands
tags: [anaconda, python, data science]
comments: true
---
Anaconda is a very popular Python package manager. It's used widely for data science.
I use it quite often because of the stable environment it creates and it's robust handling
of dependencies of packages. I always create virtual environments for my projects to ensure
that my environment dosen't break. I recommend using it over pip anyday. However, sometimes 
`conda install` may not work. In such cases only one should use `pip install`.

**Create a new environment** <br>
`conda create --name py35 python=3.5` <br>

**List all packages** <br>
`conda  list` <br>

**Update Conda** <br>
`conda update -n base -c defaults conda` <br>




