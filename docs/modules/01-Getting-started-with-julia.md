---
layout: page
title: "What is High Performance Computing?"
short-title: "Mod. 1" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - Be able to describe what an HPC cluster is
> - Explain when and why HPC can be helpful for computationally intensive research
> - Explain how using HPC differs from using a laptop or desktop computer
{: .objective}

HPC, or high-performance computing, refers to the application of supercomputers or compute clusters to computational problems. A compute cluster is the name given to a computer with capabilities well beyond the scope of standard desktop computers. The computers that qualify as HPC systems are much more powerful than other systems, and HPC systems are usually used when using desktops or laptops takes far too long or is simply.

HPC systems are also called *clusters* because they consist of a group of smaller computers (called *nodes*) clustered tightly together. In HPC clusters the connections between each node are extremely fast, which means that data and processing power can be shared very quickly between all of the nodes. This essentially turns the entire cluster of nodes into a single very powerful computer, which can be used to process and analyse massive data sets or run many smaller tasks at the same time.

![Nodes and interconnects](http://training.nectar.org.au/package04/sections/images/CloudVsHPC.png)
TODO: Update image of nodes & interconnects

Building an HPC cluster requires very expensive hardware. Firstly, each node is individually quite powerful with high processing power and large memory. Further, the HPC needs ultra fast connections between each of the nodes, as well as fast *filesystems* that can read data that needs to be processed, and store data that has already been processed very quickly. Because they are expensive to build and maintain, HPC systems are almost always shared between many users who use the cluster to process their data and run their jobs at the same time. Sharing a single cluster is a much easier and more cost-effective way for researchers to access powerful computing resources than dozens, hundreds or even thousands of researchers individually buying and managing their own hardware.


> ## Supercomputers and compute clusters: what's the difference?
> Generally, a supercomputer refers to the worlds fastest machines available irrespective of their design but with the limitations that they need to be general purpose. Smaller computers of similar design than the above are commonly referred to as High performance computing (HPC) farms, batch farms, HPC clusters etc. A list of the fastest super computers is available on [top500.org](https://www.top500.org/lists/).
{: .inset}


# Why use HPC?
Interacting with an HPC cluster is typically done by typing commands into the Unix **shell** (usually BASH or the Bourne Again Shell). Typing-based interfaces are often called a **Command-Line Interface**, or CLI, to distinguish it from a **Graphical User Interface**, or GUI, which most people now use.

> ## Unix? CLI? Shell? What is this nonsense!
> This course assumes basic familiarity using the Unix shell, like being able to change directories, read and create files and folders, and run programs. If you haven't used the Unix shell work through [these lessons](http://swcarpentry.github.io/shell-novice/) from the Software Carpentry Foundation first, or register for one of our [Unix Shell Workshops](http://intersect.org.au/training)
{: .inset}

Working with the Unix command line and HPC systems can be a steep learning curve. So what's the benefit? Here are the top five reasons to use HPC:


- **Convenience.** Maybe your calculations just take a long time or are otherwise inconvenient to run on your personal computer. There's no need to tie up your own computer for hours when you can use someone else's instead!
- **Large data sets.** Can't run that analysis on your computer? No problem, HPC systems have both the processing memory (RAM) and disk storage to handle very large amounts of data. Petabytes of RAM and storage are available for research projects.
- **Repeating yourself.** Conventional computer usually process one file after the other, which can take a very long time. HPC systems allow hundreds or thousands of files to processed at once in parallel. Exploiting this type of parallelism is one of the main advantages of HPC.
- **Speed.** In some cases, the software used for processing may run faster if more CPUs are used in the processing. This is another form of parallelism. We'll cover this in more detail later.
* **Cost.** Bulk purchasing and government funding mean that the cost to the research community for using these systems in significantly less than buying your own hardware. Some Universities have their own compute clusters, and researchers at [Intersect member universities](http://intersect.org.au/content/members) can access the [Raijin supercomputer](http://nci.org.au/systems-services/peak-system/raijin/) at no cost.


>## A brief interlude on parallelism
> HPC systems often derive their computational power by exploiting parallelism. They achieve their power by have thousands or even millions of processors, rather than having faster processors (in fact, the speed of processors on HPC system is usually similar to what you would find in a normal desktop or laptop computer).
>The basic principle is that on a normal computer you run one task after another until all the work is done. This is sequential processing and can be quite slow. However, if you can split the task so that many smaller tasks can be run simultaneously the total time to finish the job is much faster. > This is the principle of parallel processing.
{: .inset}



# When not to use HPC
If one CPU is good, thousands must be better, right?! Unfortunately it's not quite that easy. There are some cases where using HPC is not the right choice. Here are the most common ones:
- **GUIs or interactive use.** HPC systems generally don't allow programs that need a GUI, as these do not use resources efficiently.
- **Interactive use.** On HPC systems we tell the computer what to do and where the data is, then leave it to get on with the job. If you need to interact with your program (to give it instructions or data while it is running) then HPC is not the right choice.
- **Lots of data to transfer.** Transferring data takes time, especially over the internet. If you have a huge data set you may find that the time it takes to transfer the data outweighs any time saving you gain by using HPC.
- **Single threaded tasks.** To harness the power of HPC a task generally has to either be able to be split into smaller tasks that can be run separately (e.g. rerunning the same application with different parameters), or the software used for processing must be written to allow multiple processors to simultaneously solve the problem faster (it must be multi-threaded). Software that is not written this way will not run faster on a High Performance Computer.

