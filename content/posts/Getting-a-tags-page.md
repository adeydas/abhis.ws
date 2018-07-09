---
title: "Getting a Tags Page"
date: 2018-04-08T00:54:27-07:00
draft: false
tags: [hugo, frontmatter]
layout: "post"
---
I wanted to get a page with all the tags in it sorted by the number of posts referencing each. The goal was to provide visitors to pick a tag of choice and be able to read posts in it. As I have talked about in previous posts, I am using Hugo for my site, so this post will be focussed on how I got it done on Hugo.

# Get all tags
Since a tag is a recognized Hugo taxonomy, it provides a quick and nice way to get all tags:

<script src="https://gist.github.com/adeydas/6cd083d8f035954653d161d932296638.js"></script>

That *list* layout under tags is used by Hugo to create all list pages. With a tag in the URL, it shows all posts referencing that tag. Without one, however, it renders an empty page. The piece of code above, populates all pages with the *list* layout with a list of all tags.

# Show the list only where appropriate
For me, I wanted to show the list of tags only on */tags/index.html*. Any subsequent lists, like */tags/s3/index.html* should not have the list. Since they are both on the same template, I needed a way to conditionally punt of the list for all pages but one.

To do so, I reused the pagination code to tell me if there were any posts in that scope. Without a tag in the URL, there will never be any posts and with one, there will always be atleast one. Thus, the code:

<script src="https://gist.github.com/adeydas/a558f121521437bbf389d421a4aa638f.js"></script>

And that was it. You can see it working [here](https://aniotaofthought.com/tags/index.html).