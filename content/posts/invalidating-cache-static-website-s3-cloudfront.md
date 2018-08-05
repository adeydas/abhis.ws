---
title: "Invalidating Cache For a Static Website With S3 and Cloudfront"
date: 2018-03-05T19:54:23-08:00
draft: false
tags: [aws, hugo, s3, cloudfront, route53]
layout: "post"
---

I am using CloudFront to serve as an edge cache for my static blog, and an issue I faced with that approach is cache invalidation. Whenever I write a new blog post, my statically generated index and tag pages are updated as well, but since CloudFront had already cached them, the new content doesn't show up till the said cache has expired. This post is about invalidating the CloudFront cache automatically when I upload new content to my S3 bucket. Read my [first post](https://aniotaofthought.com/posts/static-website-with-hugo-s3-cloudfront-and-route53/) on how I set up my statically generated blog.

For my solution, I used AWS Lambdas. I [found](https://blog.miguelangelnieto.net/posts/Automatic_Cloudfront_invalidation_with_Amazon_Lambda.html) a python script to call Cloudfront and request invalidations for all the objects that were updated. 

<script src="https://gist.github.com/adeydas/31829ed89c9a20e609689f1e3865db35.js"></script>

With that, I created a new Lambda and added S3 as the trigger. Since I wanted it to trigger every time an object was created or updated in my S3 bucket, I chose *ObjectCreated* as the event.

![AWS Lambda configuration](/images/2018-03-05_20-06-41.png)

And this is how my Lambda interacts with my S3 bucket, CloudFront and CloudWatch.

![AWS Lambda, S3 interaction](/images/2018-03-05_20-16-59.png)

Now, whenever I upload new objects to my S3 bucket, this Lambda function fires and invalidates the cache of the changed objects. Please note that invalidating CloudFront caches cost money, so this solution might not be super scalable.