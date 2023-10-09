---
description: I cannot be contained because I am the container! --Jim Carrey
cover: >-
  https://images.unsplash.com/photo-1595587637401-83ff822bd63e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw0fHxjb250YWluZXJ8ZW58MHx8fHwxNjkyOTkxNDgwfDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# 🎁 Lab4 - Docker

In the previous Lab, you learned how to install Docker and also you have started working with Linux Comand Line within Docker which I believe feels awesome to have such flexibility and freedom!&#x20;

{% hint style="info" %}
In software engineering, containerization is operating system-level virtualization or application-level virtualization over multiple network resources so that software applications can run in isolated user spaces called containers in any cloud or non-cloud environment, regardless of type or vendor. [Wikipedia](https://en.wikipedia.org/wiki/Containerization\_\(computing\))
{% endhint %}

&#x20;

## Let’s _Dockerize_ the react-app

&#x20;

Let's start by adding a dockerfile to the main directory of your project. But what needs to be added to this file?!

As you have seen in the lecture this file contains several parts that need to be defined carefully (_otherwise it won’t work!_). Instead of jumping into a super-advanced fancy dockerfile, we adopt an incremental approach and add more fancy items as needed!

First, we need to pull the official base image. Since we use the node module, we need to make sure the base image contains a node and make sure the node version in our local machine is identical to the node version on the image.

&#x20;

<figure><img src="../.gitbook/assets/image (19) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The node version in my machine is 18.14.2.

To find out what base image is compatible with this version login to your account: [https://hub.docker.com/](https://hub.docker.com/)

Then search for “node” and inside the sort by box type the version of your node module plus the name of the (minimal) OS, in this case, it is going to be: `18.14-apline`

<figure><img src="../.gitbook/assets/image (20) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

What we need from this page is the complete name (tag name) of this image to refer to it in our `dockerfile: 18.14-alpine3.17`

Okay add this line to the dockerfile and then run the following command in the command prompt:

<figure><img src="../.gitbook/assets/image (21) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

```
docker build -t portfolio-app .
```

&#x20;

If everything goes well you should be able to see this image in our docker desktop app:

<figure><img src="../.gitbook/assets/image (22) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

As you have seen in t the lecture you can interact with this image using the shell:

<figure><img src="../.gitbook/assets/image (23) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

It is a good time to brush up your memory about [linux file system](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-the-linux-filesystem-explained)! You can also verify the version of the node running on this machine.

&#x20;

Now that we have the base image, the next step is to copy the application files into the image. Before that let’s define the working directory, i.e., _app_.

&#x20;

<figure><img src="../.gitbook/assets/image (24) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

If you have noticed this process takes a lot of time! Essentially because it copies all the files in `node_modules` directory into the image! We should do something about it!

If the process is still ongoing, just stop it (_ctrl + c_) we don’t want a large image!

Let’s add the ._dockerignore_ file beside our _dockerfile_ and add node\_modules to it.

<figure><img src="../.gitbook/assets/image (25) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

It is better now! Everything is done in less than 3 seconds!

&#x20;

Verify the results again by running the image:

<figure><img src="../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Next, we install the dependencies on the image every time it is started and expose the port we would like to use to communicate with the image.



It is easy! The only thing we need to add to the dockerfile is:

```
RUN npm install
EXPOSE 8000
```

&#x20;

If you do that you will run into an error like this:

<figure><img src="../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

To understand what is going wrong on your image when you run npm install you should comment out these two lines and rebuild your image and then go to that and manually run the command:

<figure><img src="../.gitbook/assets/image (28) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

You will need more options here!

Let’s go back to the dockerfile and fix the issue. If you open the README file you will get the additional arguments that need to be added.

```
RUN npm install --save react-tinder-card --legacy-peer-deps
```

<figure><img src="../.gitbook/assets/image (29) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Yes! It takes more time now. We will get back to this issue later!

&#x20;

We can verify that the _node\_modules_ directory is generated in the image:

<figure><img src="../.gitbook/assets/image (30) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Since we would like to start the app once the container starts running, we need to add this command to the dockerfile: `CMD [“npm”, “run”, “start”]`

&#x20;

<figure><img src="../.gitbook/assets/image (31) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

From the lectures, we have seen that the container is listening to port 8000 and it needs to be mapped to any port in the host, so we can get access to the ports on the container from the host. For that, we need to run the following script:

&#x20;

```
docker run -d -p 80:8000 portfolio-app
```

&#x20;

But when you try to see the portfolio from the host you will see the page like this:

<figure><img src="../.gitbook/assets/image (32) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

That means it is not accessible from the host (YET)

&#x20;

To debug the issue first we need to make sure the port on the container is listening. For that, we need to install the `nload` package on the container and then run `nload -m` that to show us the incoming and outgoing data from our network. (_Try this and see the result_, also _check out_ [_this link_](https://alpine.pkgs.org/3.15/alpine-main-aarch64/nload-0.7.4-r3.apk.html) _and_ [_this link_](https://linux-tips.us/monitor-bandwidth-with-nload/) _for more information_)

&#x20;

According to [this link](https://www.parinda.dev/blog/gatsbyjs-with-headless-cms-part-1-04122020/) (_and many other resources!_), it seems since we use Gatsby in this project we need to some adjustments in the docker file to be able to see the result:

* We should use _yarn_ instead of _npm_
* We need to explicitly mention the IP address of the host (i.e., 0.0.0.0)

Apply the modification in the dockerfile and then run:

```
docker build -t portfolio-app .
```

&#x20;

<figure><img src="../.gitbook/assets/image (33) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Finally, run the container with port mapping and check the result in your browser:

```
docker run -d -p 80:8000 portfolio-app
```

&#x20;

<figure><img src="../.gitbook/assets/image (34) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Everything works fine!

&#x20;

## Build and push Docker images to Azure Container Registry

&#x20;

First go to this address: [https://portal.azure.com/#home](https://portal.azure.com/#home)

<figure><img src="../.gitbook/assets/image (35) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Then use the plus sign to create a resource and search for Azure Container Registry

&#x20;

<figure><img src="../.gitbook/assets/image (36) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Pick a name for the registry name, in this case, I use the registry name: `teamportfolio`

<figure><img src="../.gitbook/assets/image (37) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Use the default values for the rest and create the container registry.

<figure><img src="../.gitbook/assets/image (38) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Then click on “go to resource” and then use “Access Keys” to log in to the registry:

<figure><img src="../.gitbook/assets/image (39) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

To log into the registry, you can use the script below:

&#x20;

<figure><img src="../.gitbook/assets/image (40) (1) (1).png" alt=""><figcaption></figcaption></figure>

Then get the list of all images and create an alias for the image with the proper name as below:

&#x20;

<figure><img src="../.gitbook/assets/image (41) (1) (1).png" alt=""><figcaption></figcaption></figure>



## Deploy the App

To deploy our app, we need to create a Web App using the production dockerfile.

First go to this address: [https://portal.azure.com/#home](https://portal.azure.com/#home)

<figure><img src="../.gitbook/assets/image (42) (1) (1).png" alt=""><figcaption></figcaption></figure>

Then use the plus sign to create a resource and search for: Web App

<figure><img src="../.gitbook/assets/image (43) (1) (1).png" alt=""><figcaption></figcaption></figure>

Use the option “Web App for Containers” and create one.

<figure><img src="../.gitbook/assets/image (46) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

<figure><img src="../.gitbook/assets/image (47) (1) (1).png" alt=""><figcaption></figcaption></figure>



## Oops, it doesn’t work!

So far everything has worked smoothly but now just in the very last step, it seems the web app we just created won’t work! Now it is your turn to put what you have learned as a software engineer into practice and try to fix the issue.

&#x20;

If you log into your portal, you can check the log files:

&#x20;

<figure><img src="../.gitbook/assets/image (48) (1) (1).png" alt=""><figcaption></figcaption></figure>



Please explain your solution and how did you find it in the learning journal!

Here are some hits that might come in handy as you try to debug the issue:

* Check the `portfolio-app` on your local machine and make sure it works OK. If it doesn't work maybe it is a good point to start!
* Check dockerfile and make sure its configuration is to be used in the web application.
* Check the platform we are using, in this case, Gatsby, do we need to do special treatment to support this platform in the web app.
* &#x20;Check our web app configuration again, did we miss anything?!



