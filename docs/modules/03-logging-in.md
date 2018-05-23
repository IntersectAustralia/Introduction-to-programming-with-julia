---
layout: page
title: "Logging in to the cluster"
short-title: "Mod. 3" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - Be able to log in to a remote cluster
> - List currently running jobs and their attributes
{: .objective}

That's enough of the theory, let's get started working on the HPC! We'll be following the exploits of Adamantium Beryllium Chloride (ABC), a theoretical chemist and avid Marvel fan as he learns to use the HPC for his research.
TODO: Update the backstory.

# Getting Connected

In order to start running our jobs on the HPC we will need to interact with a shell, which is a piece of software that provides a command line interface to the Unix operating system used by most High Performance Computing systems. Logging in to the HPC from your own computer is usually done through a tool known as SSH (for Secure SHell). As the name suggests, this gives us a secure connection to the HPC. To establish an SSH connection you will need your `username` and `password`, as well as the name of the computer to login to, which is referred to as the `hostname`. In our case the hostname is `raijin.nci.org.au`).

The method of using SSH depends on the operating system you are using:

**Mac and Linux Users:**
Open a terminal from the application launcher (on macOS Press Command + Space bar, then type “Terminal” and press Enter).

Type the following command and press Return/Enter (replace abc123 with your username).

```shell
ssh abc123@raijin.org.au
```
{: .source}

**Windows Users:**
On Windows computers with Git for Windows installed open *Git Bash* from the start menu and type the same SSH command as above.

On Windows computers with PuTTy installed open PuTTy from the start menu and set Host Name (or IP address) as `abc123@raijin.nci.org.au` (replace abc123 with your username). Select `Open`.


The first time we connect to the HPC you should get a security warning to let us know that we have not connected this machine before. Type or click `yes` to continue.

```
The authenticity of host 'raijin.nci.org.au (192.43.239.26)' cannot be established.
RSA key fingerprint is SHA256:y7+6bP/MzYyKao72kexbG+kpk0m/yxTL/q7udmZXb20.
Are you sure you want to continue connecting (yes/no)?
```
{: .output}

You will then be prompted for your password. Type or paste this into the terminal and press enter. Note that some software (like PuTTy) provides no visual feedback that you’re entering a password. If you type in a password, just trust that the system is receiving it, and make sure you type it carefully, or use copy and paste, but Windows users note the below!

**Important:** Putty does not support CTRL-C and CTRL-V for Copy/Paste respectively. These are reserved special commands on Unix systems and so cannot be used for Copy or Paste. To paste whatever is on your clipboard into Putty, just right-click into the Putty window. To copy from within Putty, simply select the text and it will automatically be saved to the clipboard.
{: .inset}

# Signs of success
When you are successfully connected to the HPC the command prompt will look something like this (where abc123 is replaced by your username):

[abc123@raijin1 ~]$
{: .output}

This gives us a good visual indication that this terminal is connected to Raijin and not our local computer. If you are ever not sure which computer the terminal is on, try running the `hostname` command. The command prompted also gives us a helpful prompt to show us where we are in the filesystem structure. By default we will start out in our home directory, which is represented by the tilde (`~`) character.

Note that there is a `1` after `raijin` in our output above. This is actually the number of the login node we are logged into. Raijin is so large that there are several login nodes. You may connect to different node in which case you will see a different number here. Don't worry, everything below will work just fine!
{: .inset}


# What's running now?
## Getting job details
Now that we've logged in, let's have a look at what is currently running on the HPC. We can easily check this out using the `qstat` command.

```shell
$ qstat -a
```
{: .source}

Wow, that's a lot of data! Let's make this more manageable by [piping](http://swcarpentry.github.io/shell-novice/04-pipefilter/) the output of this command to `less`.

```shell
$ qstat -a | less
```
{: .source}

```
| Job ID       | Username | Queue  |  Jobname  |  SessID | NDS | TSK | Req'd Memory | Req'd Time | S | Elap Time |
| ------------ | -------- | ------ | --------- | ------  | --- | --- | ------       | -----      |---| ----------|
| 123456.r-man2| zyx123   | normal-d| run_program1 | --  |  1  | 16  |  32gb        | 26:00      | Q |  --       |
| 789101.r-man2| zyx123   | normal-d| run_program2 | --  |  1  | 16  |  32gb        | 26:00      | R |  14:17:46 |
```
{: .output}


From this output we can see a paginated view of summary information for all jobs currently running on Raijin. For each job we can a lot of useful information, like the unique ID given to the job, the username of the user that submitted the job, the number of nodes (NDS), CPUs (TSK) and memory required for the job, it's status (S) and - if it's started - the length of time the job has been running. To tell the `less` command to show the next page press `f`, to see the previous page press `b`, to quit press `q`.

If we want to get summary information on a single job we can use it in our `qstat` command, for example `$ qstat 123456`. If you want detailed information use the `-f` option, for example `$ qstat -f 123456`.
{: .note}

TODO: Describe what is 'r-man2' on the job id. Is this the name of the head node?


## Getting user details
We can also use the `qstat` command with the `-u` option to check out the jobs currently for a specified user. This is especially useful for checking where our own jobs are up to. The structure is `qstat -u <username>`. Try it with your username now:

$ qstat -u abc123
{: .source}

$
{: .output}

It makes sense that we don't see any output, because we haven't run any jobs yet.

TODO: Resolve where exercises and answers should reside.

# Exercises
1. Find an active user, then list their currently running jobs.
2. Using the `qstat` command you see several jobs with a satus of `H`. How could you find out what that status means? See if you can find a way to list the different queues on Raijin, and their status.

*Answers*
1. Use the `qstat` or `who` commands to get a list of recent or logged in users, then `qstat -u <username>` to list their currently running jobs.
2. Use `man qstat` or trusty google. `qstat -Q` will show current statistics by queue.
