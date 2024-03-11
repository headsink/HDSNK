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
# list all the repositories that are tracked by git 
remote -v
# add origin
git remote add origin 
```

### 2.3 Sync Changes

```shell
npx quartz sync --no-pull
```
## Step 3 - Create Obsidian Vault
### Open your Quartz repository in Obsidian
Open folder as vault. Edit your pages inside the content folder.

Personally I made the content vault separately and made it a symbolic link inside my Quartz repository. Check out [[Youtube - SymLinks The Hidden SUPER Shortcut Feature in Windows]] on how to create a symbolic link.

## Step 4 - Link local file to Github
### Build your site locally
Before publishing build the site to run it locally...

 run this command:
```shell
npx quartz build --serve
```

You should see a block of text like below:

```
Started a Quartz server listening at http://localhost:8080
```

Open up your web browser and type `http://localhost:8080`.

### Sync to GitHub

Run this command:

```shell
npx quartz sync
```

## Step 5 - Hosting Vault
### Create a `deploy.yml` file
In your local Quartz, create a new file `quartz/.github/workflows/deploy.yml`.

Copy the code below and paste it inside the new yml file:
```yaml
name: Deploy Quartz site to GitHub Pages
 
on:
  push:
    branches:
      - v4
 
permissions:
  contents: read
  pages: write
  id-token: write
 
concurrency:
  group: "pages"
  cancel-in-progress: false
 
jobs:
  build:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0 # Fetch all history for git info
      - uses: actions/setup-node@v3
        with:
          node-version: 18.14
      - name: Install Dependencies
        run: npm ci
      - name: Build Quartz
        run: npx quartz build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          path: public
 
  deploy:
    needs: build
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

Then:

1. Head to “Settings” tab of your forked repository and in the sidebar, click “Pages”. Under “Source”, select “GitHub Actions”.
2. Commit these changes by doing `npx quartz sync`. This should deploy your site to `<github-username>.github.io/<repository-name>`.