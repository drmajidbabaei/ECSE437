---
description: >-
  Don't expect your life to be as perfect as the main branch of your git
  project!
cover: >-
  https://images.unsplash.com/photo-1681863177225-5fa13305ea95?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTI5ODQwMDB8&ixlib=rb-4.0.3&q=85
coverY: 48
---

# 🐊 Lab2 - Git

Doesn't feel marvelous to keep track of everything? getting back to history and only cherry-picking the best pieces of your past work and integrating them into the future?

{% hint style="info" %}
Git is a distributed version control system that tracks changes in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows. [Wikipedia](https://en.wikipedia.org/wiki/Git)
{% endhint %}



&#x20;

## Clone the repository in your local machine

First, we need to clone the repository and do some initial steps:

* Create a directory called “workspace” on your desktop and go to this directory
* Right-click and _open in_ _Terminal_.
* Clone the repo using this command: git clone [git@github.com:ecse437/portfolio.git](mailto:git@github.com:ecse437/portfolio.git)
* In the terminal go to the directory portfolio:&#x20;

{% code fullWidth="false" %}
```
cd .\portfolio\
```
{% endcode %}

* Check all the files here using:&#x20;

```
ls
```

* Check if you have a remote repository in git using:

```
git remote -v
```

* Yes, we have one called “_origin_”, which means we cannot add more with this name. If we want to add a new remote with the same name we need to remove this one.
* &#x20;Let’s remove it!

```
git remote remove origin
```

* Now everything is ready!

&#x20;

#### Push your code into your DevOps project

Login to your Azure DevOps account:  [_https://dev.azure.com/_](https://dev.azure.com/)

Then go to the _Repos_ where you can import your files from your local machine, or you can directory clone from a remote repository.

You need to use the code generated for you in this part (_Note: the code shown in this picture may not be identical to what you see in your system because simply we run different projects!_)

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

What you need to do here is to run these commands in your terminal where your code is located!

When you run that you will see such message that tells you everything is pushed to your remote repository successfully!

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

That is good news! You can confirm that if back to your account!

<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

Now you can get your code from your team repository in Azure DevOps Repos. If you click on the “Clone” icon, this window will pop up where you can get the address to clone the repo.

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

Everyone in your team can run this can clone the repo in their local machine:

* Copy the text in the box
* Open the terminal in the directory you want to place your code
* Run the _git clone_ command with the address here

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
_Note: “https://ECSE437@dev.azure.com/ECSE437/Portfolio/\_git/Portfolio” is the address on my project you need to use the address in your repo_
{% endhint %}



Open your code in VScode (you can download it from here: [https://code.visualstudio.com/download](https://code.visualstudio.com/download)) and run the code locally with the embedded terminal in vscode (ctrl + \~) and execute the _npm install_ command:

```
npm install --save react-tinder-card --legacy-peer-deps
```

<figure><img src="../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

## Check and update the gitigonre file

_Note: This can be done only by one person in your team (all the people don’t need to repeat the process, because they can simply pull the changes!_)

Open the _.gitignore_ file and check if all unnecessary files are already included in this file. It is important because when you run the code it will generate a lot of files and directories if you didn’t add these files, the generated files make your code messy. That reduces the maintainability of your code!

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

There question here is do we need to add “package-lock.json” to the .gitignore file or not?!

| According to the discussion in here:                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><em>Think about it, if you delete package-lock and re-install, you are forcing the latest versions of all packages in the dependency tree. Meaning, you are changing the behavior of (potentially) the entire application.</em></p><p> </p><p><em>What are you really trying to do? If you have some weird npm-related problem, simply remove node_modules and run npm install again. Removing package-lock.json is never the solution.</em></p> |

&#x20;

OK! Since we would want to force everyone to get the latest version of all packages, let’s add the “package-lock.json” file to this file and then update it!

&#x20;

Before committing the changes let’s get the _git status_ and make sure is this the change we really want to do or we should take some extra steps.

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

The list of the files is OK but we don’t what to do this in the main branch! (_Why_?!)

Let’s create a new branch!

From the lectures, we know to create a new branch for our recent changes we need to pick up a name. So the next question is what is going to be the meaningful name for the branch?! At the end of the day (or sprint) we should be able to discuss all the jobs we have done on the projects. So it is better to provide such a link between the worktime we work on and the changes we have made in the code.

Let’s create a proper work item that reflects our intention.

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
_Note: It is nice to have a short description of the expected behavior of the work item (issue) especially if it is meant to fix a bug!_
{% endhint %}

* Don’t forget to assign it to yourself or someone who is in charge of performing the update
* Adding proper tags always is a good practice
* You can change the status to Doing once you start working on it, then other people will know what you are currently working on.

<figure><img src="../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

&#x20;

Now you can create a good name for your branch based on the issue you just created! The name could be a combination of the \[short format of] project name “PRTFL” and the issue number “10” and the issue name “Update gitignore file”:

```
PRTFL10/update-gitignore-file
```



{% hint style="warning" %}
_Note: You might get a different number for the issue_
{% endhint %}

Back to the code!

Run this to create the new branch:

```
git checkout -b PRTFL10/update-gitignore-file
```



Let’s check if everything is OK:

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

Yes! We are on the right branch and the modified file is already there.

All you need to do is:

* &#x20;Add the file to your staging area
* Committing the changes to your local git repository
* Push the commit to the remote git repository

```
git add .gitignore
git commit -m "package-loc.json added to this file"
git push --set-upstream origin PRTFL10/update-gitignore-file
```

&#x20;

Nice! You have committed your first changes and let’s inform everyone that you have completed this task and celebrate!

<figure><img src="../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

But the question is: how can I inform everyone professionally about this small change? Do I need to reach out to them by email or phone or is there any systematic way to do that?

<figure><img src="../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

The short answer is Yes there is a better way to get your message across to your team!

Besides, you need to inform two groups of people:

* People who have access to the code and can verify your changes (Dev people)
* People who don’t have access to the code yet they eager to check and show off your achievement (Op people)



Create a Pull Request (PR) is a way to inform Dev people to let them know you are ready to get feedback on your changes.

Before creating a PR make sure you have done everything for this issue, if you want you can do more commits on the same issue before creating a PR.



{% hint style="warning" %}
_Note: Keep in mind that the size of your commit shouldn’t be very long, which means you should not modify multiple files in one commit because it makes it difficult for other people to understand the logic behind every commit and verify your changes_. _Do you wish to learn more? Checkout_ [_this link_](https://softwareengineering.stackexchange.com/questions/206979/how-big-should-a-single-commit-be)
{% endhint %}

For this change we are OK, so we should create a PR.

<figure><img src="../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

* If you want you are welcome to add a more detailed description
* Pick a reviewer from your team who is acting such a role or capable of giving you constructive feedback (YOU CAN NOT BE A REVIEWER OF YOUR OWN CODE)
* Add a related working item if it is linked to the previous issues you fixed. It helps the reviewer to go through the chain of changes and get a better big picture of your attitude.
* If you have made your changes based on some suggestions or scientific papers you can add a link or those papers here as attachments. Again, it helps other people to understand your work better (_of course there are chances to show off your theoretical mind here_).



## Check the PR and merge to the main branch

&#x20;

Now other people in your team (especially the reviewer) can go to the pull requests and see the changes you have made.

<figure><img src="../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

&#x20;

In the files you can see the list of the changes in this PR:

<figure><img src="../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

You can add your comment on every line of each file and start the communication with the developer.

<figure><img src="../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

You can approve/approve with suggestions/reject/ect. the PR.

<figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

If there are no merge conflicts and after getting all the approvals from reviewers now its time to merge the changes to the main branch.

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

Click the _complete_ and choose the best merging option. If you have made several commits to complete this issue (especially to address the feedback you have received), you’d better off squash the commits and don’t bring all of them to the history of the main branch! (_We will discuss the consequence of that during the lectures on VCS_)

<figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

For now, let’s stay with this option and do the merging!

<figure><img src="../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

If you are unhappy with the changes you can Revert it!

As you can see the associated work Items have changed to complete and this is how you can inform Ops people! (_But in this case, we didn’t add a link to this development work item so we should do it manually_)

&#x20;

<figure><img src="../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

&#x20;

## Update the other files using the same approach                                                              &#x20;

How can I get the list of the files that need to be updated with our team information:

Select the project directory “portfolio” and then click _ctrl_ and _h_ at the same time and search for _\[…]_ on the result you will see all the places you should update based on the information of your team.

<figure><img src="../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

For every file you should follow these steps:

* Create a work item
* Create a new branch
* Do the changes
* Commit to the remote repository
* Create a PR
* Link the work item to the PR
* Address the feedback from reviewers
* Merge the changes to the main branch

Make sure you include the description of the steps you have taken to complete this part in your learning journal.





