---
layout: page
title: "Job scripts"
short-title: "Mod. 4" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - Explain differences between shell scripts and job scripts
> - Create a simple job script
> - Submit a job script and monitor the progress of a running job
> - Identify when a job has completed successfully or with errors
> - Retrieve the output of the job
{: .objective}

# Our First Job

A job is simply a set of commands we want to run.  To run these commands on the HPC we put them into in a file called a *job script* instead of typing them directly into the command prompt. Job scripts are like normal Unix scripts, except that they contain special instructions for the scheduler. In the case of PBS Pro, commands for the scheduler are prefixed by `#PBS` keyword. HPC job scripts are also given a `.pbs` (rather than the usual `.sh`) extension to illustrate that they are intended to be given to the scheduling software to manage.

Let's create our first job script now.
```
$ nano run_sleep.pbs

#!/bin/bash

# * Specify your project code
#PBS -P do18

# Request resources
# * 1 processor
# * 100 megabytes physical memory allocated to job
# * 10 minutes wall time to run
#PBS -l ncpus=1
#PBS -l mem=100MB
#PBS -l walltime=00:10:00

# Specify the queue
#PBS -q express

# Specify the work to be done
date
sleep 60
date

exit 0
```
{: .source}

Let's break this script down into separate components.

Firstly, the `#!` symbol at the very start of the script is called a [hashbang](https://en.wikipedia.org/wiki/hashbang). By including this line, we can tell the operating system which program we want it to use to to execute our script. In this case, we tell it to use the program located at `/bin/bash` (the BASH shell) to execute our script.

It's not compulsory to include a hashbang in our scripts, but it is good practice!
{: .note}

Next, many HPC clusters work on a project basis, meaning that each project has an allocation of resources measured in hours assigned to it. In order for the scheduler to accept our job, we need to tell it which project to use by including `#PBS -P <project code>`. Note that you will only be able to use projects that you have access to!

> ## Projects and Allocations
>Each project on Raijin is given an allocation of resources that can be thought of like a savings bank. Every time you run a job, you spend a number of *core hours* (also called *Service Units or SUs*) from the project's resource allocation. For example, if your job uses 10 CPUs (or *cores*) for 10 hours each, it will use 100 hours from your project allocation.
{: .inset}

In the next section we send more instructions to the scheduler that tell it what resources we need to run our job using `#PBS -l <resource type>=<amount>`. This includes the number of nodes (`select`) and CPUs (`ncpus`) we need, the amount of memory (`mem` in megabytes `MB` or gigabyes `GB`), and the maximum time (hh:mm:ss) the job can run for before it will be terminated (`walltime`).

Wondering how to calculate the resource limit values? Don't worry, we've got you covered in an upcoming module!
{: .note}
TODO: Delete if we don't cover resource allocation...

Next, we also need to tell Raijin which *queue* we want to send our job to. There are a large number of [queues](https://opus.nci.org.au/display/Help/Raijin+User+Guide#RaijinUserGuide-QueueStructure) to choose from. For testing of small jobs we can use the `express` queue so that our jobs run quickly. When it comes time to run a proper job we should use the `normal` queue, or one of the other hardware specific queues.

Finally, we have to specify the actual work we want to complete. In this case we are running some simple BASH commands. Try running `date` and `sleep 10` at the command prompt to see what they do. The `exit 0` command is a polite way of telling the shell (and other users) that if the program reaches this point it has completed successfully. By convention, [exit codes](https://www.gnu.org/software/bash/manual/html_node/Exit-Status.html#Exit-Status) other than zero indicate some sort of error has occurred.

> ## Wait, isn't `#` a comment?
> Looking at the script above you may have wondered why all our instructions to the scheduler start with a hash (`#`) sign, which is a comment in a BASH script. In fact, it is for precisely that reason that `#` is used! This means when we submit our job to the scheduler, PBS can look for instructions by looking through our script for lines that start with `#PBS`. However, when our script is executed (in this case by BASH) the shell will safely ignore all lines beginning with `#`, so we can be sure they will not affect our script.
{: .inset}

# Submitting and Monitoring Your Job
To submit a job we can use `qsub` command.

```shell
qsub run_sleep.pbs
```
{: .source}

```shell
7070971.r-man2
```
{: .output}

The scheduler gives us a unique number back that we can use to track and change our job. To see where our job is up to we can use `qstat -x <job number>`. The `-x` option let's us see the status of the job after it has finished running.

```shell
qstat -x 7070971
```
{: .source}

```
Job id            Name                  User              Time Use S Queue
----------------  --------------------- ----------------  -------- - -----
7070971.r-man2    run_sleep.pbs         abc1123            0       Q express-def
```
{: .output}

If you run this command several times you may see the status of your job move from queued (`Q`), to running (`R`), exiting (`E`) and finished (`F`).

Want to watch a job closely? Try using `watch qstat -x <job number` or `watch qstat -u <your username>` to get updates every 2 seconds. Use `ctrl-c` to exit watch.
{: .note}

> # Stop that job!
> Made a mistake and need to remove a running job from the queue? No problem, use `qdel <job number>` to remove a job from the queue.
> ```shell
> $ qdel 7070971
> ```
>{: .source}
{: .inset}


# Getting the Output
Once your first job finishes you will probably be wondering how do I see the output? The output (o) and errors (e) of our job are stored in separate files. Let's take a look.

```shell
$ ls
my_first_script_01.pbs    run_sleep.pbs.e7070971    run_sleep.pbs.o7070971
```
{: .source}

```
$ cat run_sleep.pbs.o7070971
```
{: .source}

```shell
Tue May 22 10:42:16 AEST 2018
Tue May 22 10:43:16 AEST 2018

======================================================================================
                  Resource Usage on 2018-05-22 10:43:26:
   Job Id:             7070971.r-man2
   Project:            do18
   Exit Status:        0
   Service Units:      0.06
   NCPUs Requested:    1                      NCPUs Used: 1               
                                           CPU Time Used: 00:00:00                                   
   Memory Requested:   100.0MB               Memory Used: 0B              
   Walltime requested: 00:10:00            Walltime Used: 00:01:08        
   JobFS requested:    100.0MB                JobFS used: 0B              
======================================================================================
```
{: .output}

The output from the `date` command is at the top of the file. The scheduler has then added appended some more on the resources requested and used to the end of our job.

If your output file is empty, check the error file to see if anything went wrong!
{: .note}

# Improving our Script
What we have above is a basic template for a job script, that we can easily adapt to running our own jobs on HPC. However, there are a few improvements that we could make:
1. The output from our `date` commands is being sent to the standard output (`stdout`), which the scheduler sends to the job output (o) file along with the resource utilisation information. It would be better to save that output somewhere that we choose.
2. We don't want to have to continually monitor our job to see whether it is in the queue, running or finished. It would be better to be automatically alerted when this happens.

## Redirecting the Output
Saving the output of our job in a separate script is easy enough using the [redirect](http://swcarpentry.github.io/shell-novice/04-pipefilter/index.html) (`>`) symbol. For example, we save our output in a file called `sleep_out.txt` like this:

```shell
$ nano run_sleep.pbs

...
# Specify the work to be done
date > sleep_out.txt
sleep 60
date >> sleep_out.txt
...

$ qsub run_sleep.pbs
```
{: .source}

Now the output of the `date` commands will be sent to the file `sleep_out.txt` (replacing it using `>` the first time, appending to it using `>>` the second time). The only problem with this is that every time we run the job our data files will be overwritten! Another way we could do this is to the use special *environment variable* in PBS called `PBS_JOBID`. When our job script is run, this variable will is replaced with the job number.

>## Enviro-whatties?
> Every time we start an `SSH` session on a remote computer the shell sets up a lot information that can be used by other programs to set different configuration settings. One way the shell does this is to setup an *environment*, which contains many variables describing different properties of the system you are using. These work just like other variables you might have used already (for example in a [for loop](http://swcarpentry.github.io/shell-novice/05-loop/index.html)), except that they set system properties. One commonly used environment variable is `PATH`, which determines where the shell looks for programs to run every time we type a command. You can look at this variable using `echo $PATH`, or you can use `printenv` to look at all the environment variables currently set.
{: .inset}

Let's make some changes to our script to use the `PBS_JOBID` environment variable. As our home directory is also starting to get a bit cluttered, we will also make a new subdirectory to store our script and results.

```shell
$ mkdir sleep
$ mv run_sleep.pbs sleep/
$ cd sleep/
$ nano run_sleep.pbs

...
# Specify the work to be done
date > sleep_out_$PBS_JOBID.txt
sleep 60
date >> sleep_out_$PBS_JOBID.txt
...

$ qsub run_sleep.pbs
```
{: .source}

Now when we run `run_sleep.pbs` job we should end up with three files: An output (`o`) file generated by the scheduler containing details about our job, an error file (`e`) containing any error messages if something went wrong, and an `out` file containing the actual data.

```shell
$ ls
```
{: .source}

```shell
run_sleep.pbs  run_sleep.pbs.e7126737  run_sleep.pbs.o7126737
```
{: .output}

But wait, we have the output and error files, but where is our data file? By default, the scheduler will put any files created by our job in our home directory.

```shell
$ ls ~
```
{: .source}

```shell
sleep  sleep_out_7126737.r-man2.txt
```
{: .output}

To stop this happening we can use the PBS work directory environment variable `$PBS_O_WORKDIR`. Let's modify our script again.

```
$ nano run_sleep.pbs

...
# Move to directory job was submitted in
cd $PBS_O_WORKDIR

# Specify the queue
#PBS -q express
...

$ qsub run_sleep.pbs
```
{: .source}

Now we can keep our output, error and data files in one place.

## Staying Up-to-Date With Alerts
Another improvement we can make to our script is to tell the scheduler to email us at certain times. This is quite easy to setup using two more PBS commands in our job script.

```
# Setup email notifications when the job is aborted(a), begins (b) or ends (e)
#PBS -M user@example.com
#PBS -m abe
```
{: .source}
TODO: Check why email notifications are not working

# Our Final Script
With the additional improvements we made above our final job script becomes:

```shell
$ cat run_sleep.pbs
```
{: .source}

```
#!/bin/bash

# * Specify your project code
#PBS -P dw1

# Request resources
# * 1 node, 1 processor
# * 100 megabytes physical memory allocated to job
# * 10 minutes wall time to run
#PBS -l ncpus=1
#PBS -l mem=100MB
#PBS -l walltime=00:10:00

# Specify the queue
#PBS -q express

# Setup email notifications when the job is aborted(a), begins (b) or ends (e)
#PBS -M abc123@example.com
#PBS -m abe

# Move to directory job was submitted in
cd $PBS_O_WORKDIR

# Specify the work to be done
date > sleep_out_$PBS_JOBID.txt
sleep 60
date >> sleep_out_$PBS_JOBID.txt

exit 0
```
{: .output}

We can use this script as a template for running our own jobs on Raijin. All we need to do is change the resources we need to request to match our requirements, and specify the work that needs to be done.


# Exercises
## Challenge 1
**Question**
Reorganise your job script and directory structure by moving the actual work commands from the job script int shell script called `sleep.sh` under a `src` subdirectory. Change your pbs job script to run this script, and save the output of this script into a file in the `data` subdirectory.



**Answer**
```shell
$ mkdir src data
$ nano src/sleep
```
{: .source}

```shell
#!/bin/sh
date
sleep 60
date
exit 0
```
{: .output}

```shell
$ nano run_run_sleep.pbs
```
{: .source}
```
...
# Specify the work to be done
bash $PBS_O_WORKDIR/src/sleep.sh > $PBS_O_WORKDIR/data/sleep_out_$PBS_JOB_ID.txt
...
```
{:. output}
