---
layout: post
title: Updating the blog posting
category: markdown
tags: [jekyll, bash]
--- 

# Updating the blog posting

## A Running list of blogs 

I updated the `README.md` to include the HTML necessary for creating a running
list of the blog posts available for browsing

## A Script to Create New Posts 

I created a script to create new posts that generates a generic template and
names each new file appropriately for the jekyll standard. As well as creates
the necessary metadata fields for a more robust website. 

## Categories and Tags 

[Jekyll can accomodate categories and
tags](https://codinfox.github.io/dev/2015/03/06/use-tags-and-categories-in-your-jekyll-based-github-pages/).
This is something I should be looking into for the website.


## Zotero Bibliography integration

Zotero has an api that can be applied to other sites. [The documentation is
here](https://www.zotero.org/support/dev/web_api/v3/basics). 

I have created a start of an open group for a [Mesopotamian Knowledge
Graph](https://www.zotero.org/groups/2356093/messoptamianknowledgegraph). 

The bibliography from this library can be retrieved on the command line with: 

``` curl -X GET https://api.zotero.org/groups/2356093/items ``` 

The main problem with the API is going to be creating the Liquid Templates to
take all of the records and make sense of them in a Jekyll page. This will be
a major initial problem for this project. 

