---
description: Let's rewrite our development process using a pipeline!
cover: >-
  https://images.unsplash.com/photo-1559510981-10719ce4266a?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxwaXBlbGluZXxlbnwwfHx8fDE2OTI5OTE5MTR8MA&ixlib=rb-4.0.3&q=85
coverY: -107
---

# 🗞 Lab5 - Pipeline

So far we have learned how to plan a project and collaborate with others on a software development project. We also worked with version control systems such as `git` to keep track of the files. in the previous Lab we explored Docker and deployed our team portfolio project on a cloud provider.

{% hint style="info" %}
A pipeline is a set of automated processes that allow developers and DevOps professionals to reliably and efficiently compile, build, and deploy their code to their production compute platforms.
{% endhint %}

&#x20;

## Create your first CI Pipeline

Let's log in to [https://dev.azure.com/](https://dev.azure.com/) and then head over to “Pipelines” where you can create your CI and CD pipelines.

<figure><img src="../.gitbook/assets/image (39) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Click on “Create Pipeline” and then use the classic editor to create a pipeline without YAML. Select your repository. In this case, it is Azure Repos Git and then the branch “main”.

&#x20;

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt="" width="336"><figcaption></figcaption></figure>

In the next step, we can choose a template or create an Empty pipeline and then add our jobs to it. Here choose to start with an “empty job”.

&#x20;

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

Create Agent job 1 and let’s add two npm tasks and publish artifacts task.

&#x20;

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

We need to change `npm` install step according to the install command we use in the package.json. If you don’t remember it you can go back to the files in the repository and get the command from there.

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

For the second step let’s rename the task npm run build under command choose from the dropdown “custom” and for the “command and argument” enter “run build”.

&#x20;

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Since we use the Gatsby framework in this project we need to copy files from the public directory after building the project.

&#x20;

{% hint style="warning" %}
NOTE: In normal react projects, files will be stored in the _build_ directory, and you don’t need to add this step.
{% endhint %}



<figure><img src="../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The final step is to publish the build artifacts: Click on the plus sign look for “publish build artifacts” and set the “path to publish” to _build_, so that our release pipeline we will have access to the generated build.

&#x20;

<figure><img src="../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Head over to the Triggers tab and select Enable Continuous Integration. You can leave everything else at default.

&#x20;

<figure><img src="../.gitbook/assets/image (9) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

At the top select Pipeline and change the agent specification to ubuntu-last

&#x20;

<figure><img src="../.gitbook/assets/image (10) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Finally, click Save & Queue and again hit Save & Queue.

&#x20;

On the Run pipeline modal, leave everything at default and hit Save and run.

<figure><img src="../.gitbook/assets/image (11) (1) (1) (1) (1) (1).png" alt="" width="272"><figcaption></figcaption></figure>



After a few minutes, the pipeline will finish running successfully. You can check under the Pipelines tab to verify it.

<figure><img src="../.gitbook/assets/image (12) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

## Test the CI Pipeline



The only thing you need to do is change something in the code and commit to your master branch. But if you remember this is not how we do the changes!

First, you need to create a work item. For example, add the dockerfile to the project (if you have not done that otherwise do some random change in the read me file). Then create a branch for that and commit your changes in that branch. Finally, you can merge it to your master branch after getting approval from the reviewer!

<figure><img src="../.gitbook/assets/image (13) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
NOTE: Do not add _package-lock.json_ to your project. If you added this accidentally, go to the repository and remove it manually otherwise you will get some errors at `npm` build step.
{% endhint %}

<figure><img src="../.gitbook/assets/image (14) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

<figure><img src="../.gitbook/assets/image (15) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



Before doing the `git push -u origin` You will need to do `git pull`

<figure><img src="../.gitbook/assets/image (16) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Now you can go back to the Pipeline and see what is happening! Yes the CI pipeline is triggered itself and going into the steps one by one!

If you click on the link you can see the generated artifacts.

<figure><img src="../.gitbook/assets/image (17) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

<figure><img src="../.gitbook/assets/image (18) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;

