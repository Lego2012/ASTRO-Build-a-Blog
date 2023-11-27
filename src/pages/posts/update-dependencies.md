---
layout: ../../layouts/MarkdownPostLayout.astro
title: Upgrade Dependencies
author: Leo Merkel
description: "How to upgrade package.json dependencies"
image:
  url: ""
  alt: ""
pubDate: 2023-11-27
tags: ["astro", "dependencies"]
---

# Astro Starter Kit: Blog

## Updating Package Dependencies
There are several ways to update dependencies, and I’ve tried various methods to find the easiest path. One way to do it is by manually updating each package using npm install package-name@latest. This method is the most straightforward way of updating. However, it may not be the most efficient option.

My recommended way of updating dependencies is by using the npm-check-updates package. There’s a good article from freeCodeCamp about that, so I won’t be explaining the details of what it is and how to use that package. Instead, I’ll show you my typical approach.

First, install `npm-check-updates` package globally.

~~~bash
npm install -g npm-check-updates
~~~

Before making any updates, it’s a good idea to check all new dependencies that can be updated.

~~~bash
ncu
~~~

Most of the time, patch dependencies can be updated without affecting the project at all. So, I usually update patch dependencies by running either `ncu -i --target patch` or `ncu -u --target patch`. The difference is that `ncu -u --target patch` will update all the patches, while `ncu -i --target patch` will give an option to toggle which package to update. It’s up to you to decide which approach to take.

The next part involves updating minor dependencies. Minor package updates usually won’t break the project, but it is always good to check the release notes of the respective packages. These minor updates often include some cool features that can be applied to our projects.

~~~bash
ncu -i --target minor
~~~

Last but not least, there might be some major package updates in the dependencies. So, check the rest of the dependency updates by running

~~~bash
ncu -i
~~~

If there are any major updates (or some updates you still have to make), the above command will output those remaining packages. If the package is a major version update, you have to be very careful since this will likely break the whole project. Therefore, please read the respective release note (or) docs very carefully and make changes accordingly.

If you run `ncu -i` and found no more packages to be updated, Congrats!!! you have successfully updated all the dependencies in your project.
