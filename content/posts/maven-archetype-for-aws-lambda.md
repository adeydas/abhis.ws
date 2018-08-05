---
title: "Maven Archetype for Aws Lambda"
date: 2018-05-02T20:39:03-07:00
draft: false
tags: [aws, lambda, java, maven, archetype, open source]
layout: "post"
---
I recently started playing with AWS Lambda and migrated a couple of my projects that suited the model to it. While re-writing some of those things, the one thing I missed the most was an automatic way to generate all the boilerplate code I need for every Lambda. Thus, I ended up writing an archetype for creating AWS Lambdas in JAVA.

The [code](https://github.com/adeydas/aws-lambda-maven-archetype) for it is on [Github](https://github.com/adeydas/aws-lambda-maven-archetype) and it comes with a [README](https://github.com/adeydas/aws-lambda-maven-archetype/blob/master/README.md) on how to use it. Give it a try and let me know if it was of use.