---
layout: ../../layouts/MarkdownPostLayout.astro
title: Hightlight Nav Link
author: Leo Merkel
description: "Set class for active page"
image:
  url: ""
  alt: ""
pubDate: 2023-11-27
tags: ["astro", "navigation"]
---

# [Highlight Nav Link for Current Page in Astro](https://www.cyishere.dev/blog/astro-active-nav-item)

We take advantage of Astro's Runtime API and get the pathname in Astro components' component script.

`src/components/Navbar.astro`

~~~
---
const pathname = new URL(Astro.request.url).pathname;
const currentPath = pathname.slice(1); // remove the first "/"
---

<nav>
  <a class={currentPath === "" ? "active" : ""} href="/">Home</a>
  <a class={currentPath === "portfolio" ? "active" : ""} href="/portfolio">Portfolio</a>
  <a class={currentPath === "posts" ? "active" : ""} href="/posts">Article</a>
  <a class={currentPath === "about" ? "active" : ""} href="/about">About Me</a>
  <a class={currentPath === "contact" ? "active" : ""} href="/contact">Contact Me</a>
</nav>
~~~
