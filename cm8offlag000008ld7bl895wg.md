---
title: "Navigating Jira: A Practical Introduction"
seoTitle: "Beginner's Guide to Jira"
seoDescription: "Learn Jira for project management, Agile frameworks, issue tracking, and integrations with Slack and GitHub"
datePublished: Tue Mar 25 2025 11:42:58 GMT+0000 (Coordinated Universal Time)
cuid: cm8offlag000008ld7bl895wg
slug: a-simple-guide-to-atlansian-jira
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1742823623308/37f72496-dd4e-4aef-84e0-ab7b50225a2d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1742902767223/ba65f817-874b-4450-b00f-f1bc46d9b7c9.png
tags: developer, devops, devops-articles, jira-automation

---

Jira is a comprehensive project management tool that enables teams to create, track issues, manage sprints, and collaborate seamlessly. It offers a customizable workflow to accommodate different team structures and work processes. Jira is widely used in software development, IT service management, and business project tracking.

### Agile Project Management

It is an iterative and flexible approch to manage Projects, primaraly used in software development . It focuses on continuous improvemet, customer feedback, and adaptive planning of rigid, long-term plans.

Popular Agile Frame Works :

1. Scrum
    
2. Kanban
    
3. Lean
    
4. SAFe (Scaled Agile Framework)
    

## Epic, Story, Task

In simple terms :

* **Epic** → A big feature or goal that takes a long time to complete.
    
    Example: "Build a real estate platform."
    
* **Story** → A smaller part of an epic that delivers a specific function.
    
    Example: "Allow users to list properties."
    
* **Task** → A tiny piece of work needed to complete a story.
    
    Example: "Create the property listing form UI."
    

### **Epic :**

Learn Docker and Deploy a Containerized App

### **Stories :**

1. Understand Docker Basics.
    
2. Work with Docker Images & Containers.
    
3. Use Docker Compose for Multi-Container Apps.
    
4. Deploy a Dockerized App.
    

### **Tasks :**

🔹 ***For Story 1 (Understand Docker Basics):***

* Install Docker on your system
    
* Learn basic Docker commands (`docker run`, `docker ps`, `docker stop`)
    
* Understand Dockerfile and how to create an image
    

🔹 ***For Story 2 (Work with Docker Images & Containers):***

* Pull and run a pre-built Docker image
    
* Create your own Dockerfile and build a custom image
    
* Push your image to Docker Hub
    

🔹 ***For Story 3 (Use Docker Compose for Multi-Container Apps):***

* Write a `docker-compose.yml` file
    
* Connect a Node.js app with a database using Docker Compose
    
* Start and stop containers with `docker-compose up/down`
    

🔹 ***For Story 4 (Deploy a Dockerized App):***

* Set up a production-ready Dockerfile
    
* Deploy a containerized app to AWS/GCP/VPS
    
* Use Docker logs and debugging tools
    

Each **Epic** is a big goal, **Stories** are smaller steps, and Tasks are the actionable work items to achieve the goal.

### Story point :

To estimate the effort and complexity, time required to complete a task.  
In User story a small task get fewer points and a complex one get more.

### **Example:**

**"Add a login page"** → **2 Story Points** (Easy)  
**"Integrate third-party payment system"** → **8 Story Points** (Hard)  
**"Build a real-time chat system"** → **13 Story Points** (Very Hard)

### Scrum Board :

A **Scrum Board** is a visual tool that helps teams track work in a project. It has columns like:

**TO Do** → task that eed to be done.

**In progress** → task currently being working on.

**Done** → completed task

You can also add additional phases like Testing ( for code testing ) and so on.

### How to Manage project :

#### **Step 1: Create an Epic (Main Goal)**

1. In the navbar, click the **"Create"** button.
    
2. A dialog box will appear.
    
    * Choose **Issue Type** as **"Epic"**.
        
    * Add a **summary** (e.g., "Learn Docker").
        
    * Check the **status** and add a **description**.
        
3. **Add assignee** (select the team member responsible).
    
4. **Add label** and choose the **team** (create a new team if needed).
    
5. **Select the start date** and attach any files if required.
    

#### **Step 2: Create a Story**

* Follow the same steps as creating an Epic, but:
    
    * Change **Issue Type** to **"Story"**.
        
    * Two important options:
        
        1. **Select sprint** (choose the relevant sprint).
            
        2. **Set story point estimate** (assign effort points).
            

#### **Step 3: Create a Task**

* Same as Story, but:
    
    * Change **Issue Type** to **"Task"**.
        
    * Select the **sprint** you're working on.
        
    * Set a **story point estimate**.
        

#### **Workflow Management**

* After completing these steps, tasks will appear in the **"To Do"** section.
    
* To start work, **drag the task ticket** to the **"In Progress"** section.
    
* Move tasks to further stages (e.g., "Review," "Done") as they progress.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742898352484/9f6d70db-0526-477b-8a6c-02acdd3e63b8.png align="center")
    

### **Ticket in Jira?**

* A **ticket (or issue)** in Jira represents a single unit of work (task, bug, feature, etc.).
    
* Each ticket has:
    
    * **Unique Ticket ID** (e.g., `PROJ-123`) for tracking.
        
    * **Type** (Epic, Story, Task, Bug, etc.).
        
    * **Assignee** (person responsible).
        
    * **Status** (To Do, In Progress, Done, etc.).
        
    * **Priority** (High, Medium, Low).
        

In the left hand side you willl see lots of option click on the Backlog

### Backlog :

A **Backlog** is a to-do list for a project. It contains all the tasks (stories, bugs, features) that need to be done but haven't started yet.

I have a task to install Jenkins but I need to complete this task only after finishing my Docker task. This way, I can keep my task in the backlog as a reminder that it needs to be completed later.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742794988966/42d662d9-6ba9-4a45-b0d9-794babfdb3c5.png align="center")

---

## Jira + Slack Integration

### Follow these steps to integrate Jira with Slack and manage tasks efficiently:

#### **Step 1: Create a Slack Account**

* Sign up for a **Slack account** if you don’t have one.
    
* Inside Slack, go to your **workspace**. If you don’t have a workspace, create one and launch Slack.
    

#### **Step 2: Install the Jira Cloud App for Slack**

* In Jira, go to the **Navbar** and click on **Apps**.
    
* Select **Explore more apps** and search for **Jira Cloud for Slack** (choose the most downloaded version).
    
* Alternatively, you can navigate to:
    
    * **Project → Quick Start → Connect Your Tools → Choose Slack**.
        

#### **Step 3: Connect Jira to Slack**

* Click on **Get App** → **Learn More** → **Allow the integration** → **Go to Slack**.
    
* You will now see **Jira** inside the **Apps** section in Slack.
    

#### **Step 4: Create a Jira Task from Slack**

* Open **Slack** and go to the **Jira bot message**. (you can refer the Image below)
    
* Type `/jira create task` in the chat.
    
* Fill in the required details.
    
* Click **Submit**, and the task will be created in Jira.
    

A new task will get created and get saved in the backlog you can check it out there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742797523471/3fc5f2b7-ff14-4ace-a31b-cc3d60af5bb7.png align="center")

## **Why Integrate Jira and GitHub? (Simple Explanation)**

Integrating **Jira and GitHub** helps developers and project managers work together smoothly. Here’s why:

1. **Track Progress Easily** → When you push code or create a pull request in GitHub, Jira updates the related task automatically.
    
2. **Better Collaboration** → Developers can see which Jira issues are linked to their code changes.
    
3. **Faster Workflow** → No need to switch between Jira and GitHub to update task status manually.
    
4. **Automated Updates** → Jira can move tasks from **"In Progress"** to **"Done"** when the code is merged.
    

## **Jira + GitHub Integration**

**Go to Project → Quick Start → Connect Your Tools → Choose GitHub**

* Click **Continue → Next**
    
* Grant **repository access**
    
* Once completed, your GitHub account will be connected to Jira
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742900039046/98b4506a-f54d-41c7-ae3c-c8ab3cdd2b99.png align="center")
    

Now, go to your **Scrum Board** and click on any task ticket. Under the **Development** section, you will have the following options:

1. **Create Branch** – Create a new branch in the linked GitHub repository directly from Jira.
    
2. **Create Commit** – Commit changes to the repository from within Jira.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742900339996/fe3abb6f-06fd-4cfc-97c8-c9bc682ec314.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742900681619/8ef65331-02c9-4728-841f-c1f0850a5b81.png align="center")

We know that every Jira ticket has a unique ID, such as **SCRUM-1, SCRUM-2**, etc.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Here’s a cool trick: when you push your code to GitHub, it’s usually only visible in GitHub. But with Jira and GitHub integration, you can track your commits directly from Jira.</div>
</div>

```bash
git add .
git commit -m "added new feature - SCRUM -1" 
git push origin feature-branch
```

## How things Automation works in Jira :

Follow these steps to automate Slack notifications when an issue transitions in Jira:

#### **Step 1: Create an Automation Rule**

* Navigate to **Project Settings → Automation → Create Rule**.
    
* Jira provides various automation functions that you can use for Slack integration.
    

#### **Step 2: Set Up the Trigger**

* Choose the **Trigger**: **"When an issue is transitioned"**.
    
* Configure the transition details (e.g., from **Done** to **Progress**).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742799314925/cacf99c9-1725-4b9c-bd76-d4a01e640e52.png align="center")

### **Step 3: Choose an Action**

After setting the trigger **"When an issue is transitioned"**, follow these steps:

* Click on **Add Action**.
    
* Search for **"Send Slack message"** and select it.
    
* Configure the message format, such as:  
    **"Task *{{issue.key}} - {{issue.summary}}* has been transitioned from *{{fieldChange.fromString}}* to *{{fieldChange.toString}}*."**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742799448448/369419a3-cd18-4c49-bb8d-ca07c2c27aef.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742900746929/a29256b7-967f-44b1-b910-dc9e7083d41a.png align="center")

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742901122208/89083466-c1fe-4e5f-a627-752a1caa885a.png align="center")
    
    **Google "Slack Webhook"** and open the official Slack page.
    
* click on **"Create Your Slack App"**.
    
* A dialog box will appear – click on **"Create New App"**.
    
* Basic Information Page will get open.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825859251/81271e74-5164-4662-81ff-58165f1a5c24.png align="center")

* Navigate to **"Using Incoming Webhooks"**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825881120/8550ab44-59d6-45ef-828e-f0e6c9cdcf8e.png align="center")

* Click on **"Add new webhooks to workspace"**.
    
* This will ask for the Channel to send the Notification. If channel is alredy created paste it. Otherwise, create a new Channel. ( Go to slack app → Channel → Create new Channel. )
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825906600/6a73f23d-daa2-41be-b948-9a27b971443e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825923957/f5de6351-3301-4105-83b2-2995bfac72dd.png align="center")

* Copy this webhook Url and Paste it in the Jira Automation inside Send Slack message.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825953167/96567191-e7e9-4c7d-a18e-de18c6f7ce5d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742902167946/f3f75915-d930-47b9-aaf6-2c868a7ad541.png align="center")

* Click → Next and Add rule.
    
* **Move the 'Create Docker files' ticket from TODO to IN PROGRESS, then check the Slack channel.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1742825971431/903ed703-cdd9-413a-9afc-7df0e1298181.png align="center")

**Jira is a powerful tool that streamlines project management and enhances team collaboration. By integrating it with tools like Slack and GitHub, you can automate workflows and boost productivity. Start leveraging Jira today to optimize your development process and keep your projects on track!**

Let me know if you want any modifications! 🚀