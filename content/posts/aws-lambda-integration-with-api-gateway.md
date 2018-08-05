---
title: "Aws Lambda Integration With Api Gateway Without Proxy Integration"
date: 2018-06-15T19:56:20-07:00
draft: false
tags: [aws, api gateway, lambda]
layout: "post"
---
I was looking into using AWS API Gateway with a AWS Lambda without proxy integration today and I couldn't find enough resources on how to configure the integration response for throwing non-200 status codes on failures. Turns out, its not that complicated. So here we go.

I had a simple JAVA based lambda that for our very limited purposes just throws an exception. I tried returning a well-formed JSON response but that doesn't seem to work. Seems like unless the lambda throws an exception, API Gateway doesn't intepret it as an error condition.

<script src="https://gist.github.com/adeydas/7550cd0230d47ef86091e269f82ecb61.js"></script>

Note that I have a prefix called 'Failed'. I am going to use that to configure my API Gateway Integration Response. 

To do that, I created a new integration response and set the Lambda Error Regex as `Failed: .*` with Content Handling set to `Passthrough`. So overall, my Integration Response looked like:

![Integration Response](https://aniotaofthought.com/images/integration_response_06-15.png)

and my overall method execution looked like:

![Overall GET method execution](https://aniotaofthought.com/images/get_method_resource_06-15.png)

And that was it, pretty simple, huh!