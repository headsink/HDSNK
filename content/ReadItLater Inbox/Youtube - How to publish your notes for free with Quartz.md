---
title: Youtube - How to publish your notes for free with Quartz
description: 
aliases: 
tags:
  - youtube
draft: false
date: 2024-02-10
---
# [How to publish your notes for free with Quartz](https://www.youtube.com/watch?v=6s6DT1yN4dw)

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/6s6DT1yN4dw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

>Below are notes for the video above.
# Step 1- 5

We need the following installed before you continue:

- [NodeJS](https://notes.nicolevanderhoeven.com/NodeJS) v18.14+ (check your version using `node -v`)
- [NPM](https://notes.nicolevanderhoeven.com/Node+Package+Manager) v9.3.1+ (check your version using `npm -v`)
- [Git](https://notes.nicolevanderhoeven.com/Git) (check your version using `git --version`)
- [Obsidian](https://notes.nicolevanderhoeven.com/obsidian-playbook/Using+Obsidian/01+First+steps+with+Obsidian/Obsidian)
## Step 1 - Local Installation
### 1.1 Download and install Quartz
 Clone the repository with command prompt or any shells...
```shell
git clone https://github.com/jackyzha0/quartz.git
```

### 1.2 Rename Folder
Rename the `quartz` folder to something like `myFolder` or anything more descriptive.

### 1.2.1 Go to that Folder
```shell
cd myFolder
```
### 1.3 Install Dependencies
Before entering the command make sure you have compitable NodeJS and NPM version as mentioned before.
```shell
npm i
```

### 1.4 Initialize Quartz
```shell
npx quartz create
```

## Step 2 Setting-up Github Repository
### 2.1 Create github repo
Set up github repository refer to [Setting up your GitHub repository (jzhao.xyz)](https://quartz.jzhao.xyz/setting-up-your-GitHub-repository) for details...

### 2.2 Change remote origin

```shell
# list all the repositories that are trackedgit 
remote -v
# add origin
git remote add origin 
```

### 2.3 Sync Changes
## Step 3 - Create Obsidian Vault

## Step 4 - Link local file to Github
Sync to github

## Step 5 - Hosting Vault
Hosting on github Pages.