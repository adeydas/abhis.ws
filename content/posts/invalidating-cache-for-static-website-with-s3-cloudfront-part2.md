---
title: "Invalidating Cache for Static Website With S3 and Cloudfront - Part 2"
date: 2018-05-26T09:16:41-07:00
draft: false
tags: [aws, hugo, s3, cloudfront, route53]
layout: "post"
---
In an [earlier post](https://aniotaofthought.com/posts/invalidating-cache-static-website-s3-cloudfront/), I talked about a python based lambda to invalidate the static website cache. In this post I am going to talk about a JAVA based lambda. The underlying logic remains the same, so I am going to concentrate more on the code.

The handler
===========
The lambda handler is the ingress point for the S3 event. When it receives an event, it parses through the list of updated/added objects, prepends '/' to it and calls CloudFront for invalidation. If the object is named 'index.html', it invalidates the whole subfolder. 

<script src="https://gist.github.com/adeydas/71f251fc810e0ef3e2612431876afe45.js"></script>

The Cloudfront code
===================
The Cloudfront DAO batches the list of items to invalidate and calls Cloudfront to start the invalidation process. This works fine for a small number of files, but once your website becomes somewhat big, this call can result in throttling exceptions. A cheap way to get around it could be sleep and then retry. A better way would be to backoff exponentially and retry. This piece of code employs the cheap way.

<script src="https://gist.github.com/adeydas/3217afbb31fe132e7cebab83ec6e9863.js"></script>

Conclusion
==========
Cloudfront invalidation is pretty straight forward but one gaping hole with this solution is the number of invalidation requests it creates. While that is fine for smaller websites, bigger websites with thousands of pages would probably be hit with a high Cloudfront bill without support for batching requests.