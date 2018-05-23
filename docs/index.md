---
layout: page
title: Getting started with HPC
short-title: "Home" # This will appear in the Nav bar in the header
show-in-nav-bar: false
---

# Introduction

Welcome to Getting started with HPC - Intersect's introductory HPC course for researchers.

"High-performance computing" supercomputers have been around for longer than some of their users today. The first supercomputer, the [Cray-1](https://en.wikipedia.org/wiki/Cray-1), was setup in 1976 and was put in operation at Los Alamos National Laboratory. In the course of history, the design of supercomputers underwent several revolutions. Today, most universities and an increasing part of the industry in several domains exploit the computational power of clusters of interconnected servers.

High-performance Computing (HPC) clusters are used for large scale data processing and data analysis, fine grained parallel calculations and simulations of ever increasing fidelity. This course material is meant to introduce learners to the core principles behind using a HPC cluster, how to connect to it, and how to dispatch jobs and retrieve their results.

By the end of this workshop, attendees will know:

- How to use the UNIX command line to operate a remote computer, connect to a cluster, and write simple job scripts.
- How to submit and manage jobs on a cluster using a scheduler, transfer files, and use software through environment modules.
- How parallelisation can be exploited on a cluster to speed up data analysis.

# Prerequisites

This course assumes basic familiarity using the Unix shell, like being able to change directories, read and create files and folders, and run programs. If you haven't used the Unix shell work through [these lessons](http://swcarpentry.github.io/shell-novice/) from the Software Carpentry Foundation first, or register for one of our [Unix Shell Workshops](http://intersect.org.au/training).

If you are already comfortable with using systems like PBS, Slurm or LSF, and have already run applications on a super computer you probably won't learn much from this lesson.
{: .note}

# Outline

TODO: Move objectives to YML and auto-populate the table below

| Module Number |   Name        | Learning Objectives        |
|---------------|---------------|----------------------------|
|              |[Setup]({{ site.baseurl }}/modules/00-setup)| Download software and files required for the lesson |
|1              |[What is HPC?]({{ site.baseurl }}/modules/01-what-is-HPC) | Be able to describe what an HPC cluster is <br> Explain when and why HPC can be helpful for computationally intensive research <br> Explain how using HPC differs from using a laptop or desktop computer |
|2              | [Nodes and Schedulers 101]({{site.baseurl}}/modules/02-nodes-and-schedulers)| Explain the how the login, head and compute nodes are related <br> Explain the role of the scheduler <br> Explain how using HPC differs from using a laptop or desktop computer |
|3              |	[Logging In]({{ site.baseurl }}/modules/03-logging-in)	| Be able to log in to a remote cluster <br> List currently running jobs and their attributes |
|4	            | [Job Scripts]({{ site.baseurl }}/modules/04-job-scripts) | Explain differences between shell scripts and job scripts <br> Create a simple job script <br> Submit a job script and monitor the progress of a running job <br> Identify when a job has completed successfully or with errors <br> Retrieve the output of the job <br> |
|5              |All about modules | Explain what software modules are and why they are useful, List modules available on the system, Load a module and run the software, Explain the concent of environment variables, Examine the impact on the $PATH environment variable, Use the $PBSJOB_ID and $PBS_O_WORKDIR environment variables in a job script, Practical Exercise #2 - Run a more realistic job requiring software to be loaded and use PBS_JOBID and PBS_O_WORKDIR to direct input and output |
|6	           | Data Transfer	| Transfer files to the HPC via SFTP, Retrieve files from the HPC via SFTP, Demonstrate differences in line endings between Unix and Windows, Inspect text file types using the file command, Convert Windows files to Unix files using dos2unix, Download data directly to the HPC using WGET, Practical Exercise #3 - Utilise SFTP, WGET, modules and line ending conversion to run HPC jobs |
| 7            |	Parallelisation Power	| Explain the difference between serial and parallel jobs, Contrast parallel code with parallel tasks, Compare time taken to run non-parallel code with 1 core and 2 cores, Explain embarrassingly parallel problems, Demonstrate parallelisation using job arrays |
| 8	           | The final test	| Practical Exercise #4, Run another (possibly domain specific) using environment variables, SFTP, WGET, modules, line ending conversion and parallel tasks |
| 9	            | Wrapping up	 | Describe the different queues available, Describe the different filesystems available, Explain how to maximise efficient use of the queue, Do's and dont's of good citizenship, Explain how to apply for HPC |


# Attribution

We would like to give due attribution to the following sites, made available under a [Creative Commons Attribution lience (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/legalcode"). Material in this course has been adapted from these sites:
- HPC Carpentry: [Introduction to High-Performance Computing](https://hpc-carpentry.github.io/hpc-intro)
- Peter Steinbech: [HPC in a day](https://psteinb.github.io/hpc-in-a-day)
- NeCTAR: [nectarcloud Self-Paced Training](http://training.nectar.org.au/)

[Go to module 1 to get started]({{ site.baseurl }}/modules/01-what-is-hpc)
{: .next-link}
