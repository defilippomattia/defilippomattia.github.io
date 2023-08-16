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
`git clone defilippomattia.github.io`

2. `cd ./defilippomattia.github.io`

3. Run Hugo command to create a new site.  
`hugo new site .`

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


# Heading 1 {#custom-id}

But what if you want to add another entry to the dictionary without going back to the dictionary to put it there? That's what we are going to look at in this article. And I'm going to show you how to do it in 3 different ways. Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

{{< img src="cat.jpg" alt="how are u" size-method="Fit" size-format="600x400 webp" position="center" >}}


> For 50 years, WWF has been protecting the future of nature. The world's leading conservation organization, WWF works in 100 countries and is supported by 1.2 million members in the United States and close to 5 million globally.  Here's a sentence with a footnote. [^2]

[^2]: Here We Go

## And I'm going to show you how to do it in 3 different ways.
These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

1. Get One
2. Get Two
3. Get three


### Heading 3
These elements extend the basic `syntax` by adding additional features. Not all Markdown applications support these elements.

---

Control the position of [title](https://www.example.com) the markers and text indentation in a list using the list-inside and list-outside utilities.

- List One
- List Two
- List Three

#### Heading 4
Unlike other blockquote techniques, this style does not require a nested block-level element (like p). As such, it turns a paragraph into an inline-styled element to keep the content from dropping below the quote.

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

##### Heading 5

In the separated borders model, the border makes the entire box look as though it were embedded in the canvas. In the collapsing border model, drawn the same as 'ridge'.

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Tailwind lets you conditionally apply utility classes in different states using variant modifiers. For example, use hover:scroll-auto to only ~~The world is flat.~~
 apply the scroll-auto utility on hover.

term
: definition

###### Heading 6


That is so funny! :joy:
Ini adalah contoh lain dari subscript: x_{2}_.


{{< begin-task-list >}}
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media