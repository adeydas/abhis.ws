---
title: "Static Website With Hugo, S3, Cloudfront, and Route53 - Part 1"
date: 2018-03-04T17:24:44-08:00
draft: false
tags: [aws, hugo, s3, cloudfront, route53]
layout: "post"
---

I started playing with [Hugo](https://gohugo.io/) recently, a super fast static website generator written in Go. I had tried using Middleman and Jekyll earlier, but the constant issues with maintaining a consistent version set of ruby dependencies was getting on my nerves. For a short while I even moved back to Wordpress, not the proudest moment in my life, but necessary to avoid spending copious amounts of time on Ruby dependencies. However, when Hugo began to trend, I decided to give it a try and here we are. This post is about setting up this blog, created with Hugo, on a string of AWS technologies, in an entirely serverless manner.

# Starting with Hugo
Hugo has [extensive documentation](https://gohugo.io/getting-started) on setting up Hugo sites, deploying and customizing them to fit one's needs. As such I will not go into details on this blog post. 
Before moving on to the next section, I would recommend setting a Hugo site up. Having said that, subsequent parts are agnostic to the static site framework and hence applies to all such frameworks and even hand-crafted HTML sites.

# Setting up a S3 bucket
S3 is my hosting solution. First, I created a bucket in a region of my choice. The choice of the region doesn't matter if you plan to use CloudFront. However, if you choose not to use CloudFront, I would recommend selecting a region closest to your readers to reduce the number of hops from your reader to the bucket endpoint.

After creating a S3 bucket, I changed the "Static website hosting" property to "Use this bucket to host a website." I also added my index document and changed the bucket policy to make the contents of the bucket publicly viewable.

<script src="https://gist.github.com/adeydas/c5f8605eecbea40b324943cfc1bebd0e.js"></script>

With my bucket ready to serve content to the world, I uploaded my website content. With Hugo, I ran *hugo* to generate the public artifacts and uploaded them to my S3 bucket.

# Setting up CloudFront
CloudFront, for me, has two purposes: 

1. to serve content faster via its edge caches and 
2. let my site have an *https* end-point.

Setting up a CloudFront distribution is pretty straightforward, and there are hundreds of articles out there explaining the process. Hence, I will skip that bit. The only thing to keep in mind is to not choose the S3 bucket as the origin. Instead, put the S3 bucket URL as the origin. The bucket URL is at *Properties -> Static Website Hosting -> Endpoint*. The reason is to let CloudFront consider the S3 bucket a web server and not an object store.

# Wiring things up with Route53
Route53 is a necessary bit to keep the architecture a hundred percent serverless. I created a *Hosted Zone* and pointed my domain to Route53's name servers. Once the domain propagated, I created a couple of record sets:

1. An *A* record with an *alias* to my CloudFront distribution.
2. A *CNAME* record called *www* that pointed to (1).

Although its possible to create a *CNAME* record on any domain provider and point it to a CloudFront distribution the same cannot be said for an *A* record, and thus, I ended up using Route53.

# Setting up SSL
An optional but highly recommended step is to setup SSL. Since I used CloudFront to 'front' my website, I set up a custom certificate for my domain on my CloudFront distribution. AWS offers certificates via its Certificate Manager. One may also upload a custom one. 

# Conclusion
And that's all. Stay tuned for more posts on Hugo and AWS as I work towards creating a more streamlined static blogging experience.