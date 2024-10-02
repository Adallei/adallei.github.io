---
title: Building hugo with termux and deploying to Github
date: 2024-09-17
type: blog
authors:
  - name: Ljg
    link: https://github.com/adallei
    image: https://github.com/adallei.png
excludeSearch: true
---

 {{< callout >}}
This article is to use termux build hugo and deploy to github some basic tutorials, advanced tutorials will be written in the follow-up.
{{< /callout >}}
<!--more-->
## Foreword
Hugo is a static website generation engine written in the go language, known for its speed and claimed to be "The world's fastest framework for building websites"<br>
Termux is a terminal emulator on Android. It is very powerful and can run some linux applications. So you can use termux as a terminal to build hugo.<br>
{{< callout type="info" >}}
This post will be divided into two parts: Build and Deployment.
{{< /callout >}}
## Build

#### Preparations Work
>  Before you start, you need to download termux and install the relevant packages before you can start the build.

* ##### Download termux
*  Download and install open termux on [GitHub](https://github.com/termux/termux-app/releases) or [F-droid](https://f-droid.org/packages/com.termux/).<br>
 * Getting storage access<br>
 `termux-setup-storage`
 * update package<br>
 `pkg upgrade -y`
 * Installation of related tools (git and vim)<br>
 `pkg install git vim -y`
 
#### Installation & Use
* ##### Install hugo
 * Install<br>
 `pkg install hugo -y`
* ##### Create a web page
 * Create a new site<br>
 `hugo new site (Your site name)`
 * Download & Install Theme<br>
 `cd (Your site name)`<br>
 `cd themes`<br>
 `git clone (Theme Download Address)`
 > Hugo doesn't have a theme by default, so you need to install a theme before you can use hugo.<br>
Find a hugo theme online then replace (Theme Download address) with the theme you found.<br>
Or just download the theme's source code and extract it to the themes directory.<br>
Themes may be installed in slightly different ways, you need to find the official installation tutorial released by the theme and follow it.
 * Starting services<br>
 `hugo server`
 > Be careful to execute it in the root directory of the site, which is the (Your site name) directory.<br>
After successful startup, you can browse the site by typing localhost:1313 into your browser.<br>
The default configuration file when you enter this command is in toml format, if you are used to yaml format then enter<br>
`hugo convert toYAML [flags] [args]`<br>
Convert all front content in the content directory to front content using the yaml format

* ##### Write an article
 * New article<br>
 `hugo new content/(Article directory)…/Article name.md`
 > The front matter structure of the article is:<br>
title: Title of the article<br>
date: The date the article was published (usually in YYYY-MM-DD format)<br>
author: Author's name<br>
draft: Whether it is a draft (true or false)<br>
tags: List of tags for organizing articles<br>
categories: Category list for categorizing articles<br>
slug: Custom short paths in URLs<br>
summary: A summary of the article, usually used on listing pages<br>
keywords: Page keywords for SEO<br>
description: Page descriptions for SEO<br>
aliases: Redirect list for old URLs<br>
type: The content type, which determines the template used for that content.<br>
layout: Specify the template layout to be used<br>
The article adopts Markdown markup language, you can go to [Markdown Guide](https://www.markdownguide.org/) to see how to use it!

* ##### Summary
 Above is the basic construction of the page, if you want to customize your hugo or encountered any errors please refer to the[**Official Hugo Documentation**](https://gohugo.io/).
## Deployment

#### Preparations on github
* ##### Account&Repository
 * Register for a [**github**](github.com) account<br>
 * Establishment of remote repository
 > Create a new repository in github, and make sure the name of the repository is your github username.github.io.<br>
Others can be filled in or not.
 * Setting up therepository<br>
  Access to repository settings/Pages<br>
  Change the source option under build and dissolve to deploy from branch.
  
#### The use of git
* ##### Configuration
 * Go to the public directory in the site<br>
 `cd /…/(Your site's path)/public`
 > If you don't have a file under public you need to type in (your site path).<br>
`hugo -D`
<br>to generate static files
 * Configure user information<br>
  `git config --global user.name "(Your username)"`<br>
  `git config --global user.email "(Your email address)"`<br>
  >Note: (Your username) and (Your email address) need to be different from the ones on GitHub.
  * Initialize the directory as a git repository<br>
  `git init`
  > If you enter it once and it doesn't work, enter it twice.
  * Adding a remote repository<br>
  `git remote add (The alias, usually origin) "(SSH link to the repository)"`
  > To add an SSH link using git remote add, you first need to know the SSH link to the github repository first.<br>
    Click code on the repository home page and then click SSH to see the SSH link to the repository.
  * View repository Information<br>
  `git remote -vv`
  * SSH key generation key pairs<br>
  `ssh-keygen -t rsa -C “(Comment)”`
  > where (Comment) may be omitted.<br>
Getting the generated public key is usually in the .ssh file in Termux's home directory, which can be opened in the native files of the desktop, or authorized to be opened by other applications.<br>
Find the id.rea.pub file in the .ssh directory, open it as text and copy everything in it, then paste the copied content into GitHub.<br>
Click on your avatar on the GitHub website, then click on Settings and find SSH and GPG Keys.
Click New SSH Kays and paste what you just copied under the key and click Add SSH Key to add the key, and if you need to enter a password, enter your GitHub password.
 * Commit all files under public to the data staging area<br>
  `git add `
 * Submission of document changes<br>
 `git commit -m "(Push message)"`
 * Push<br>
 `git push -u origin main`
 > origin is the alias mentioned above.<br>
main stands for the master branch, if push to the main branch fails<br>
you can use the command:<br>
`git pull -f origin main`<br>
to force a push, using this command will force overwriting the remote repository code with local code.<br>
If the above doesn't work, type:<br>
`git push -u origin master`<br>
master is the default branch name.<br>
After pushing you need to go to Pages in the settings in your GitHub repository and change Branch to master.
* ##### Summary
Above is the deployment of hugo on GitHub.<br>
There's another way to deploy using GitHubActions check out [**Hugo Official Website**](https://gohugo.io/hosting-and-deployment/hosting-on-github/)<br>
Finally, thank you for watching and I hope this has been helpful!