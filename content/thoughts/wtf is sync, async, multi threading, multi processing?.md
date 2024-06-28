---
title: wtf is sync, async, multi threading, multi processing?
date: 2024-06-26
tags:
  - seed
enableToc: false
---

You know what, anyone you will ask about this two concept in discussion, you will get very vague answers or some kind of round robin answer because they look similar or little confusing, so let's simplify this thing, as easy which we can understand, and i have also some knowledge gaps, so that will also get addressed.

 
let's start from synchronous:

## Synchronous:

It's basic term, doing things in sync as we say, or doing things one by one, until one job is finished you don't move to another job, if you are in sync communication with someone, you need to wait for the other person to finish their work or response.


# Asynchronous:

Async is opposite of Sync, we don't wait  or get freeze, we continue our life and work on other things, we msg someone, we start doing other work, don't wait for their msg, when we get the reply we look at the reply, and do necessary action.



![[sync vs async.png]]

## So where's the confusion lies?
As far i have seen main confusion for people begins when they do async programming, let's see what is the expectation and reality, where confusion lies.

let's take example and understand,
```javascript
const response = await fetch(…);
const json = await response.json();
const foo = JSON.parse(json); 
console.log(foo);
console.log("hello Karan");
```

above example is pretty famous and simple, it fetches some endpoint, parses it and then prints it, that's it!

What do you think which print statement will get printed first?
### Expectation:
>there is await before fetch so we this program will wait for it's completion and then continue the next line of execution, so first foo will get first printed then hello Karan will be printed.
### Reality:
> hello Karan will get printed first than foo will be printed

async await is just some syntactical sugar bullshit([[Promises in js|promise]]) over single threaded process, which works like non blocking!

above same code as simpler version:
```javascript
fetch(…)
  .then(response => response.json())
  .then(json => {
    const foo = JSON.parse(json);
    console.log(foo);
  });
console.log("hello Karan");
```


Nodejs is basically works on single threaded single process model, so it should execute things one by one, but it will block the things which is problem, so to address this and to achieve non blocking in single threaded single process model,
it uses concept of event loop!

Great talk on explaining event loop: [What the heck is the event loop anyway?](https://youtu.be/8aGhZQkoFbQ?si=D-5YW9C1wr78wN8u)

than it comes than how will we handle concurrent requests?

this guy also had same question 8 years ago
![[why the fuck is nodejs faster?.png]]
here is the [question](https://stackoverflow.com/questions/34855352/how-in-general-does-node-js-handle-10-000-concurrent-requests), and detailed answer explanation,

so tldr is, multi threaded web server can spawns lot of threads, but they wait while the operation is getting done, they do nothing and waste resources, where event loop based approach utilises that and make use of those resources,

event loop approach in general fails if you need to do lots of CPU calculations before returning the data. Now, I don't mean a for loop processing the database result. That's still mostly O(n). What I mean is things like doing Fourier transform (mp3 encoding for example), ray tracing (3D rendering) etc.

but still where is the magic?
>our single-threaded app is actually leveraging the multi-threaded behaviour of another process: the database.

good analogy found from net:
>think of NodeJS as a waiter taking the customer orders while the I/O chefs prepare them in the kitchen. Other systems have multiple chefs, who take a customers order, prepare the meal, clear the table and only then attend to the next customer.

So many people who uses python don't know this but python is also single threaded(because of [Global Interpreter Lock (GIL)](https://realpython.com/python-gil/)), there is event loop which runs and works same way like nodejs when it comes to async programming(whenever you use `asyncio` lib)

### what is thread?
found lot of definition to be not easy to understand or not that intuitive, so here is some stolen analogy of what is thread:
>A thread is an execution context, which is all the information a CPU needs to execute a stream of instructions.
>
>Suppose you're reading a book, and you want to take a break right now, but you want to be able to come back and resume reading from the exact point where you stopped. One way to achieve that is by jotting down the page number, line number, and word number. So your execution context for reading a book is these 3 numbers.
>
>If you have a roommate, and she's using the same technique, she can take the book while you're not using it, and resume reading from where she stopped. Then you can take it back, and resume it from where you were.
so cpu also does this illusion that it is working on multiple things at the same time, but it is just doing that by spending bit time on each task, and it is possible because it has execution context, same like same book can be shared by friends.
threads are different from processes. A thread is a context of execution, while a process is a bunch of resources associated with a computation. A process can have one or many threads.

It's important to note that threads are different from processes:
- A thread is a context of execution, while a process is a bunch of resources associated with a computation. 
- A process can have one or many threads.
- Processes do not share memory (by default), but threads share all of their memory with other threads in the same process.

now we know what is thread, let's now see 

### what is multi threading:

let's no go to direct jargons and other academic definitions, and understand this from analogy,

Imagine a single chef (the CPU) working on multiple dishes simultaneously:

- The chef starts boiling pasta (Thread 1)
- While the pasta is boiling, they begin chopping vegetables (Thread 2)
- As they're chopping, they stir a sauce that's simmering (Thread 3)

The chef is quickly switching between tasks, but they're limited by being just one person. They can juggle multiple tasks, but they're not truly doing them at the exact same time. This is similar to how a single CPU core handles multiple threads.

this is the best multi threading example which i found and can think of.

This is like using a web browser. You can have multiple tabs open (threads), and the browser switches between them quickly. But on a single-core CPU, it's still processing one tab at a time, just switching very fast.
### what is multi processing:

same analogy, 

Multiple Chefs in Separate Stations

Now imagine the same kitchen, but with multiple chefs, each at their own station:

- Chef 1 is dedicated to boiling pasta (Process 1)
- Chef 2 is solely responsible for chopping vegetables (Process 2)
- Chef 3 is focused on preparing sauces (Process 3)

Each chef works independently and simultaneously, much like separate CPU cores in multiprocessing. They don't interfere with each other's tasks and can truly work in parallel.

This is like running multiple applications on your computer simultaneously. Your music player, word processor, and web browser can all run independently on different CPU cores, truly operating in parallel.

which one to use when ?
- Multithreading is efficient for tasks with waiting periods (like I/O operations), just as a single chef can manage multiple dishes with different cooking times.
- Multiprocessing is better for tasks that require continuous computation, like having separate chefs for labor-intensive tasks.

i still wanted to go to much more in details, because they taught me all this in the clg, but didn't connect dots

next i want to understand how exactly SIMD works all under the hood, lol i literally wrote what is SIMD in 4 marks in clg exam :)

thanks to this random guys from the internet because of them i understood this things and cover my knowledge gaps:
- https://www.youtube.com/watch?v=0vFgKr5bjWI
- https://youtu.be/AZnGRKFUU0c?si=FzvY6jZQLdh7_NjC
- [threads are evil](https://web.stanford.edu/~ouster/cgi-bin/papers/threads.pdf)
- [Multithreading vs multiprocessing - what to use when?](https://www.reddit.com/r/embedded/comments/aezf7n/multithreading_vs_multiprocessing_what_to_use_when/)
