---
description: >-
  The Linux philosophy is 'Laugh in the face of danger'. Oops. Wrong One. 'Do it
  yourself'. Yes, that's it. --Linus Torvalds
cover: >-
  https://images.unsplash.com/photo-1690812336375-829488c85418?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTI5ODQwMDB8&ixlib=rb-4.0.3&q=85
coverY: -134
---

# ⚒ Lab3 - LCL

Open Source-based technologies reduce the prospect of a product suddenly becoming obsolete. It allows for more collaboration and better innovation between industries.

{% hint style="info" %}
Linux is one of the most popular operating systems among professionals. In this article, you'll learn the most-used Linux commands. Also, you will be introduced to Docker!
{% endhint %}

&#x20;

## Introduction

In this Lab, you will learn how to work with Docker. Before talking about Docker, let’s take a moment to highlight containers. A container packages code and all its dependencies into a single unit, thus letting an application run quickly and reliably from one computing environment to another. This makes such applications easily portable between machines and solves the “it works on my machine” problem. Though the technology behind containers has been around for a while, Docker made it easier to work with containers. Since its debut in 2013, Docker has become an industry standard. Currently, the core technology exists as a popular, open-source container runtime called Docker Engine.&#x20;



To create Docker containers, you’ll first need a Docker image. If you’re familiar with object-oriented programming concepts, think of images as classes and containers as objects.    Images include everything needed to run an application: code, runtime, system tools, system libraries, and settings.&#x20;



Docker is ideal for the following use cases, and many more:

* Software prototyping and packaging
* Microservice architecture implementation&#x20;
* Network modeling
* Continuous integration and delivery
* Reducing debugging overhead
* Running more workloads on the same hardware      &#x20;

&#x20;

## Docker Desktop App

One of the best ways to get started with Docker is by installing Docker Desktop—especially if you’re a developer using Mac or Windows. That said, you might be wondering, “What’s Docker Desktop, and how’s it different from the open-source Docker Engine?”&#x20;

While some developers envision Docker Desktop as just a GUI on top of Docker Engine, that characterization barely scratches the surface. Docker Desktop is an easy-to-install application and includes Docker Engine, Docker CLI client, Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. Docker Desktop still uses Docker Engine at its core. However, the seamless integration and interoperability of these tools make Docker Desktop user-friendly—regardless of your experience with Docker.

By installing and using Docker Desktop, you’ll enjoy the following features:

* Simple and easy-to-install environment to build, ship, and run your containers
* Easy way to create and manage using volumes
* Local and remote management of Docker images
* Better collaboration by sharing repeatable and reproducible development from your local machine to the container
* Simple, one-click Kubernetes setup for your local machine
* A dashboard for a quick overview of running containers, images, and volumes
* Support for building and using multi-architecture images

&#x20;

In the next section, we will see how to run Linux using the Docker Desktop App

## Running Linux

First head over to [https://hub.docker.com/](https://hub.docker.com/) and complete the registration process, then login to your account

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

&#x20;

Then install the Docker desktop app from [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/) and log in with the credential you just created.&#x20;

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

On the search bar, type Ubuntu and then Run its latest version:

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

When you Run the container, you will see this message in the terminal:

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

That means you need to run your container in interactive mode to be able to work with it. So let’s run the command prompt and then execute the following commands:

* Run the powershell
* Use: `docker ps` to see the running processes or containers
* Use: `docker ps -a` to see the stopped containers as well
* Finally, use: `docker -it ubuntu` to run the container in an interactive mode

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

What we have here is called The Shell, It is a program that takes our commands and passes them to the OS for the execution. In this line, `root@982250960ecd:/#`, the root is the current user, after `@` we have the name of the machine, i.e., `982250960ecd`, automatically generated by Docker, after ‘:’ you can see where we are in the file system, i.e., `/`, which represents the root directory, finally we have `#` which means we have the highest privileges. If I logged in as a normal user instead of # you would see a `$` sign.

Next, we will explore some Linux commands.

## Working with Linux Command Line

Let’s see the location of the shell program. You need to run `echo $0` as you can see it refers to `/bin/bash` , bash is the enhanced version of the original shell program. Also using the history command you can see all the commands you have executed lately.

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>



{% hint style="warning" %}
_Note #1: “shell” is a broad term that refers to any program that provides a command-line interface, "Bash" is a specific type of shell that is widely used in Unix/Linux systems._
{% endhint %}

{% hint style="warning" %}
_Note #2: if you have noticed in Windows, we use a forward slash but in Linux, we use a backslash to separate directories._
{% endhint %}

{% hint style="warning" %}
_Note #3: Linux is a case-sensitive operating system! There is no command “Echo” it is “echo”!_
{% endhint %}



## Working with Grep

Now we are going to learn about "grep" command. Grep stands for _Global regular expression print_. As the name implies, Grep is used to search text files with regular expressions (shortly regex). It prints the lines matching the given pattern in a text file. If no file is given, grep will recursively search the given pattern in the files in current directory. Grep has two variants, namely _egrep_ and _fgrep_. These variants are deprecated but are provided for backward compatibility. Instead of using "grep -E" and "grep -F", you can use "egrp" and "fgrep", respectively.

First, let’s create a file with some random worlds and show its content.

`cat file.txt`

| Here is the output:                                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------------------------------- |
| <p>ostechnix</p><p>Ostechnix</p><p>o$technix</p><p>linux</p><p>linus</p><p>unix</p><p>technology</p><p>hello world</p><p>HELLO world</p> |

&#x20;

To begin the search, just type grep followed by what it is you're looking for and where you are looking from. For example, I am going to look for the string "nix" in file.txt. To do so, I run:

`grep nix file.txt`

What did you get as the output?! (Include results in your learning journal)

{% hint style="warning" %}
_Note#4: You can also use -n flag to show the line numbers in the output. This can be useful when you're working with a really long code._
{% endhint %}



Please note that grep is case-sensitive. What you will get if you run these commands:

```
grep os file.txt
grep -i os file.txt
grep -i 'hello world' file.txt
```

(Include results in your learning journal)

We can also pipe an output of a command into grep. Have a look at the following example.

```
cat file.txt | grep os
```

(Include results in your learning journal)

Now see what we've got. The output of the file.txt is piped into grep and the words that contain the letters "os" in file.txt have been displayed.

We can also use some special characters or regular expressions in grep.

* ^ - search at the beginning of the line.
* $ - search at the end of the line.
* . - Search any character.



What you will get if you run the following commands:

```
grep tech file.txt
grep ^tech file.txt
grep x$ file.txt
grep .n file.txt
```

(Include results in your learning journal)



You should now have a basic understanding of grep usage.

## Managing Users in Linux

&#x20;

In Linux we have some commands to add, modify, and delete a user:

```
useradd, usermod, and userdel
```

If you run this `useradd --help` you will see a bunch of options, you can use with this command. Here we only need `-m` or `--create-home` and let’s create the user called _john_.

```
useradd -m john
```

where is this user?! And how can I verify it?!

The user’s info is stored in a configuration file in `etc` directory. Let’s check it:

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
_Note #5: the name passwd is a bit misleading! Only user’s info will be stored here not their password!_
{% endhint %}



```
john:x:1000:1000::/home/john:/bin/sh
```

In this line “x” means the password is stored somewhere else! “1000:1000” refers to the user’s and its group id. Then we have “/home/john”, the home directory of the user, finally, we have “/bin/sh” the shell program used when this user logs in to this system.

&#x20;

But what if we want to use bash instead of shell when this user logs in? we should modify this information using `usermod` the command. First, let’s see what options we have:

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

Here I am going to use -s to modify the shell program.

```
usermod -s /bin/bash john
```

Now we can verify it!

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

&#x20;

Where are the passwords?! There is another file called shadow where all password is stored in an encrypted format. This file is only accessible to the root user!

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

To learn more about how this file works take a look at [this link](https://www.techtarget.com/searchsecurity/definition/shadow-password-file).

Now that we have created the user, we can login to the container with this user. To do this, while your container is still running in a new tab in the command prompt run the following commands:

First, let’s check if your container is still running and get its id with `docker ps`

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

In my case, the id is: `217ef9e08bba`. You may get a different ID!

Then use the command exec to execute the bash program in this container with the user _john_

Then use the following command to log in with the new user:

```
docker exec -it -u john 217ef9e08bba bash
```

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

Let’s see what happens if I want to access the shadow file using john user!

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

This verifies that I am not a root user!

{% hint style="warning" %}
_Note #6: we also have an alternative command to create a user “adduser” it is more interactive than “useradd” and also allows you to set the password as well as additional information when you create a new user._
{% endhint %}

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

## Managing Groups

First, let’s answer this question why do we need groups? All users in the same group will have the same permission to the system.

Let’s create a group called developers:

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

We can get its information in a configuration file in etc dir.

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

Now we want to add _`john`_ to this group. Again we need to use `usermod` command but this time with different options.

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

As you can see we have two options: `-g` and `-G` what are the differences?

`-g` is used to modify a user’s primary group but `-G` is used to modify a user’s supplementary group.

* _Primary Group_: Used to decide which files are created by which users. One user must belong to only one group.
* _Supplementary Group_: Specifies one or more groups for users to share files between them. One user can belong to up to 15 secondary groups.



You can check out [this link](https://www.hostingadvice.com/how-to/linux-add-user-to-group/) to understand.

Here we want to modify john’s supplementary group:

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

We use the `groups` command to confirm this.

&#x20;

## File Permission

First, let’s go to the home directory and create a file called `deploy.sh` Files with this extension are called shell scripts. In these files, you can put your script and run it in one go!

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

To get permission for this file we should get a long listing:

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

* If the first letter is – it is a file. _d_ means it is a directory
* We have 9 letters divided into 3 groups, e.g,. we have rw-r--r-- for the deploy.sh file. The first group is the permission for the user who owns this file. The second group is for the group that owns this file. The third group is the permission for everyone else.
* In each group we have _read_, _write_, and _execute_ permissions. In john dire we have rwx that means we have full permission. We have _x_ because we want to go into this directory.



If we try to execute the deploy.sh file we will get a permission error!

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

Because the root user does not have the execute permission.

Let’s add and then remove execute permission for the user who own this file with the command `chmod`:

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

We can do the same for the group and also others:

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

With that even john can execute this file! Because others have the _x_ permission

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

We can also combine these in one command:

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

Here we removed x, r, and w from the group and the others.
