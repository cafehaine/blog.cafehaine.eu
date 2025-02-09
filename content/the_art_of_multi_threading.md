title: The art of multi-threading
date: 2017-03-16
tags: Programming
lang: en
---
<!-- Licensed under the CC BY-NC-SA 4.0 -->
<section markdown="1">
# Introduction

If you've ever wondered how to get more performance out of your programs,
without using some specific language tricks, you've probably heard of
multithreading.

I'll try and explain in a really basic way how it works, and then show you when
it can apply, how NOT to do it, and some final tips on how to use it.

# What is multithreading

As you might know, your CPU has multiple cores. You can consider that a CPU core
can run an application on its own. The goal of multithreading is to use multiple
cores at the same time, in order to run faster.

An application (process) can use multiple threads. A thread is where the code of
your program is ran. It's the role of the OS to manage threads and split them
amongst all of the availble cores.

In order to use multiple cores to run faster, an application must use multiple
threads, hence the name multi-threading.

Now that you understand a little bit more about multithreading, let's talk about
what you should NOT do. (If you still have some problems understanding this,
please go check wikipedia.)

</section><section markdown="1">

# What not to do

As with any other kind of optimisation, you should consider a few things first.

Is my application already functional? If you really think that your application
can work on it's own, then you can consider adding multithreading as a feature.
IT IS NOT A CORE FUNCTIONALITY.

Another guestion you can ask yourself is: Will my application really benefit
from multithreading? Most basic applications don't, and it will just be a
painful task to try and add multithreading to it.

You've decided to add multithreading to your application. Great, but if you usea
language, like C#, which asks you to lock resources accessed by multiple
threads, DO NOT OUTPUT YOUR RESULTS IN A SHARED VARIABLE. This will cause each
thread to wait for all others to stop saving the result. Instead, just return
multiple results that you can combine afterwards.

</section><section markdown="1">

# Some tips

Think about how to divide your workload before starting to code: Think about how
cinebench r15, or my program Mass Resizer are doing it.

Cinebench has a huge number of computations to do, so the total workload is
divided in about 200 "tasks" to do, and each thread will work on a new task as
their is finished.

MassResizer is supposed to handle about 200 files, so I simply divided the
number of files by the number of threads, which is much more simpler to do than
Cinebench's way, but it also means that when approaching the end, fewer threads
are working, as some may have finished their part faster.

Anyway, I hope this helped you in some way, and I hope you will have less
troubles realising your next multithreaded application.

<section markdown="1">
