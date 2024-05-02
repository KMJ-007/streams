---
title: serverlesss
date: 2024-05-01
tags:
  - seed
enableToc: false
---
Thoughts learnings while i was messing with serverless, despite i knew the hype, but i still wanted to get my hands burnt!

what do we even mean by serverless in first place ?
there is no server ? then where does our code runs ????

so let's try to understand where the problem lies which serverless computing is trying to solve,

imagine you are using normal server for serving your users, they normally use in day time, everything is going good, you are paying for rented server through xy service, and servers are running 24/7, but user don't use your software 24/7, they are also human, they also sleep, they also do other things, so we are paying for server rent when we are not using also!

here comes the serverless in the picture, we only pay for what we use, so when someone sends request to our backend server, it will wake up, process the request, and then go offline, and we only pay for what amount of time we used!

okay but math is not mathing, when we call request our backend  in serverless, it will take some time to wake up and in net net res time will increase right ?

##### cold start problem:

yes!, this problem is called cold start problem in world of serverless computing, what you think aws knows something black magic or other serverless providers, cold start problem occurs when it is first time someone is invoking(fancy word for calling or making request) your serverless function, service which you are using will spin up new container to execute the code, and spinning up new container will take some time, which we called as cold start time, but once container is up, if any new request comes then there will be no cold start time!

only one company has solved cold start problem, which is cloudflare, they have taken different [approach](https://blog.cloudflare.com/cloud-computing-without-containers/) for running serverless functions, most serverless computing providers runs serverless code in new containers, but cloudflare handles this differently:


Cloudflare Workers runtime uses the **Chrome** **V8 Engine** to run Javascript code. Each process is sandboxed using “**[isolates](https://v8docs.nodesource.com/node-0.8/d5/dda/classv8_1_1_isolate.html)**” so that the different users’ codes are run in a single process in an isolated and secure way. This reduces the overhead of processes.

interested more in isolates ? -> [HN](https://news.ycombinator.com/item?id=31740885)

![[isolates.png]]
