---
description: >-
  Expect the best, plan for the worst, and prepare to be surprised! -Denis
  Waitley
cover: >-
  https://images.unsplash.com/photo-1511497584788-876760111969?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=3432&q=80
coverY: 0
---

# 🌴 Lab1 - Planning

Are you ready to embark upon a wonderful learning journey?

{% hint style="info" %}
_Here you can find the description of Lab 1 which is about project planning using Microsoft Azure. Enjoy the learning journey and don't forget to explore beyond the rules and regulations that are laid out in this article!_
{% endhint %}

&#x20;

## Creating an AZURE DevOps Organization

In this section, we cover the steps required to manually create an Azure DevOps organization

First, Navigate to the Azure DevOps website (dev.azure.com). Then, log in with your Microsoft account credentials and select New Organization in the left sidebar.

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

In the pop-up window, name your organization and set the region where you'd like your projects to be hosted. The name of the organization is ECSE437, and the region is set to Central Canada

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

&#x20;

On successful creation of the organization, Azure DevOps routes you to a page where you can create projects in your new organization.



## Creating an Azure DevOps Project

After creating the Azure DevOps organization, the Create A Project To Get Started page appears on the screen. To create a project using this form, specify a project name and visibility and then click Create Project.

After creating a project, you will see a dashboard with all the possible actions you can perform in the project. Azure DevOps projects are the starting point for everything you do.

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

&#x20;

Here is the Azure DevOps project dashboard

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>



{% hint style="warning" %}
_NOTE: There is another way to create a new project. You can do this separately from creating an organization as well. There are many situations where you want to add a new project to an existing organization. Click your organization's name in the menu on the left. You will be redirected to the Organization Overview page. Click the New Project button in the upper-right corner._
{% endhint %}

&#x20;

## Invite people to your team

If you click the blue invite button on the dashboard's top left corner, you can invite people to your team. Invite all the people on your team as well as me (Majid Babaei) and the TA (Sarvin: sarvin.ghiasikhalehoghli@mail.mcgill.ca).

&#x20;

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

&#x20;

## Create a work Item

Now, enter the details for the task. The following are the fields and their meanings so that it is easy for you to know what to type: (_Note: At this point, you don’t need to set all of these fields but later when you add the source code to your project you can add more detailed work item_)



* Title: Here, you can write the name of the task. (For example, create add-to-bag functionality for guest users.)
* Assigned: Here, you can assign work items to specific people on your team. This person must be a member of the project.
* Add tag: You can also add tags to this work item. You can use these tags to group related work items and find them later.
* State: Because this work item is new, the state is automatically set to To Do.
* &#x20;Iteration: Here, you can define which sprint to add to this task. Setting the iteration can also happen later in the backlog.
* Description: Here, you can add more details about the task so that other people on your team have full context on the details of the work item.
* Discussion: Here, team members can post additional comments about the work item. You can have conversations here about tasks, pull requests, bugs, or any other thing relating to the work item.
* Priority: Here, you can set a number to indicate the priority of the work item.
* Activity: You can also classify this item. For this project, your work item can be classified as a deployment, design, development, documentation, requirements, or testing activity.
* Development: Here, you can link the item to a specific branch, build, commit, or Pull Request.
* Related Work: You can link the item to other items like GitHub issues and other work items. You can also create relationships between this task and others. Types of relationships include child, duplicate, duplicate of, parent, predecessor, related, successor, tested by, and tests.

&#x20;

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

&#x20;

Let’s create an issue and then some tasks based on this issue. The issue is called “learning the programming platform”. Then we can list all the items that we need to learn as tasks under this issue. Assign this issue to everybody on your team!

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

Now create a simple work item task called “Learning ReactJS” and assign it to all team members. Here is a sample description of the task and some tags, assign it to an iteration. (_You can give it a different priority point_)

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

If you go to the history option, you will see:

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

Now you can link this task to the issue we have already created. Click on the add link and the find the issue in the list. (Make sure the like type is _parent_)

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

Now you can see the link under the related work.

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

Now you can create a discussion on how to complete this task with your friends.

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
_<mark style="color:red;">Please do not mention me here!</mark>_
{% endhint %}

When you save this, you will see your work item like this:

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

&#x20;

{% hint style="warning" %}
_Note: You have successfully created a new work item. I recommend creating a variety of work items such as issues, epics, and tasks. This will help you become familiar with the different work items and how to navigate them._
{% endhint %}

&#x20;

## Managing Backlogs

Backlogs help you plan your project with issues or epics. Once you have a plan, you can start working on writing the code for the product.

The product backlog is a roadmap of what your team plans to deliver. Backlogs have features that make project planning hassle-free. The following are some of these features:

&#x20;

* Quickly define tasks assigned to your team by identifying epics, product backlog entries, or issues
* Reorder your backlog to make sure you're working on the most important work items first&#x20;
* Add details and estimates to your backlog items
* Quickly assign backlog items to team members and sprints
* Predict tasks to evaluate what can be delivered within a sprint
* The project dashboard gives you access to your backlogs. To visit the Backlogs page, select Boards ➪ Backlogs  &#x20;

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

Here, you can see all the other work items in the project. You can move work items into iterations (or sprints) from the backlog. (_It only shows you issues_)

<figure><img src="../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

In addition to moving backlog work items to iterations (or sprints), you can edit, reassign, copy, add relationships, or email work items. You can move work items between projects. This is especially useful when the organization is restructured, and projects are reassigned to various teams.

If you want to see the related work for this issue you need to click on it and check the list of the related work. (_You can add as much related work as you want here_)

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

If you click to view as a board, you will see the states that your issue can have (from to do to done).

When you start working on this issue you can drag and drop it to the “doing” state.

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

You can add several subtasks to this.

<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

When you complete all the tasks you can move the issue to the done state.

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

When you open the backlog, you will see something like this:

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

Here you can check the status of the issue and each task.

&#x20;

## Sprints

Sprints (or iterations) are used to divide the work into specific periods. Teams use two or three weeks for their sprints depending on what works for them. This is based on the momentum that a team can endure, that is the rate at which the team is finishing the tasks.

&#x20;

Let's look at the Sprints page view in Azure DevOps in more detail:

&#x20;

* Select Sprints from the left menu below the dashboard. By default, the Backlog view is displayed. You can get an overview of the issues again here, except this time for the current sprint.
* Click Taskboard in the top menu to see different views of the work items in the sprint similar to what's happening in the board. This time, the items in the current sprint are shown at the task level in the backlog.
* From here, you can create new tasks under specific issues or in the unparented column; you can also drag, edit, and interact with work items as described in the “Boards” section.  &#x20;

&#x20;

Sprint task boards are often used by teams in their daily standups. Items are moved to different columns based on the team's progress. The team will also briefly discuss these elements and, if necessary, ask for help when there's a blocker or an error. At the end of the sprint, most items are moved to the Done column.

&#x20;

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

&#x20;

Let’s create a query:

You can filter work items based on filter criteria specified by Azure DevOps. This makes it easy to get an overview of all work items of a certain type, status, or tag. This can be done both within a project and across multiple projects.

To create various queries for searching through work items, complete the following steps:

* Click Query in the left menu under Boards.
* Next, let's create a query that will be searching for an issue with the Doing state.
* Then, click Run query. The result will display all the issues that are currently active

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>
