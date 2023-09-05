---
title: "How to create and deploy a Hugo blog"
draft: false
date: 2022-08-27T09:16:45.000Z
description: "See how to create and deploy a Hugo blog with Github Actions and Github Pages."
---

## Introduction

I like the idea of having a personal website where I can write some stuff, so I created this one. Before I started, I had a few requirements:

1. It should be easy to create and deploy new content.
2. It should be easy to maintain.
3. It should be created using static site generator.

The requirements are met by using [Hugo](https://gohugo.io/) (static site generator) and [Github Actions](https://github.com/features/actions) (CI/CD).

## Steps

1. Create Github account and repository

2. Install Hugo
3. Create a new Hugo site
4. Setup CI/CD with Github Actions
5. Custom domain name (optional)

### 1. Create Github account and repository

Create Github account and repository. It's important to name the repository `username.github.io` where `username` is your Github username. My repository is named `defilippomattia.github.io`.

### 2. Install Hugo

Just follow the [official guide](https://gohugo.io/getting-started/quick-start/).

### 3. Create a new Hugo site

1. Clone previously created repository.  
   `git clone https://github.com/defilippomattia/defilippomattia.github.io.git`

2. `cd ./defilippomattia.github.io`

3. Run Hugo command to create a new site.  
   `hugo new site myblog`

4. Add a theme, I'm using [Lowkey](https://themes.gohugo.io/themes/lowkey-hugo-theme/). Follow the theme's instructions to install it.

For Lowkey theme I did this:

`git submodule add https://github.com/nixentric/Lowkey-Hugo-Theme.git themes/lowkey`

`cp -r themes/lowkey/ExampleSite/* .`

` rm -rf themes/lowkey/ExampleSite/config/_default/config.toml`

`npm install`

5. Start the Hugo server.

`hugo server -D`

Now you can see your website at `http://localhost:1313/`. Once you are happy with the result, you can stop the server and commit your changes.

### 4. Setup CI/CD with Github Actions

Next goal is to setup CI/CD with Github Actions, this will allow us to automatically build and deploy the website on every push (for eg. when a new post is created).
I was suprised how easy it was to setup this, literally in 5 minutes I had a working CI/CD pipeline.
I just followed the [official guide](https://gohugo.io/hosting-and-deployment/hosting-on-github/).

### 5. Custom domain name (optional)

You can host your website on Github Pages for free (on `username.github.io`), but you can also use a custom domain name. I bought my domain name on [Namecheap](https://www.namecheap.com/) and I configured it to point to Github Pages.

## Conclusion

With this setup, it's very easy to create and deploy new content. Just create a new post, commit and push it. Github Actions will automatically build and deploy the website.

GitHub repository is available here: https://github.com/defilippomattia/defilippomattia.github.io
