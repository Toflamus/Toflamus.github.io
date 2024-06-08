---
layout: distill
title:  Setting up python environment
date: 2024-06-07 9:00:00
description: How to set up VScode with git and build an envrionment with anoaconda
tags: setupenv
categories: setupenv

toc:
  - name: Installation and setup of VScode
  - name: Get your git
  - name: Conda & anaconda
  - name: Connect remotely to server
---

## Installation and setup of VScode

Visit the official website and download. Do not forget to add to path!.  
Click [here](https://code.visualstudio.com/)

### Setting launch.json
  
Here is an answer from [Zhihu](https://zhuanlan.zhihu.com/p/673525708)  

Anyway for basic configuration, the VScode will write the `lanuch.json` for you.  

### settings.json

`settings.json` is an important file where you can set the configurations of VS code by .json instead of click a lot of settings.  

## Get your git

From [zhihu](https://zhuanlan.zhihu.com/p/671365179)  
Official website: (Git)[https://git-scm.com/]  

Please choose the component:  
`(NEW!) Add a Git Bash Profile to Windows Terminal`  

Everything else is just default configuration.  

Note that you may need to restart your VS code for using git

### Initialize the git

Gets into Git CMD  

Add your user name and user email  
`git config --global user.name "<your user name>"`  
`git config --global user.email "<your email>"`  

### Generate ssh keys and add the keys to your github

Generate ssh keys(still in GitCMD)
`ssh-keygen -t -rsa`  

Login to your GitHub account and find the SSH and GPG keys in your settings :  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-06-07-settingupenv/sshandgpgkeys.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Copy the information in the file `id_rsa.pub` and paste it to your github.  

To test if it works:  

Go to gitbash and run  
`ssh -T git@github.com`

## Conda & anaconda

### Set up conda environment and how to use conda

#### Install

[Conda](https://link.zhihu.com/?target=https%3A//conda.io/docs/) Official web  

[Anaconda download](https://www.anaconda.com/download)  

Open **Anaconda Prompt**  

`conda --version`  

Update conda  
`conda update conda`  

#### Creating environments

Conda allows you to create separate environments, each containing their own files, packages, and package dependencies. The contents of each environment do not interact with each other.  

The most basic way to create a new environment is with the following command:  

`conda create -n <env-name> (<package_names>)`  

To add packages while creating an environment, specify them after the environment name:  

Ex: `conda create -n myenvironment python=3.12.3`  

For more information on working with environments, see [Managing environments](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).  

#### Listing environments

To see a list of all your environments:  

`conda info --envs`  

A list of environments appears, similar to the following:  

`conda environments:  

   base           /home/username/Anaconda3  
   myenvironment   * /home/username/Anaconda3/envs/myenvironment`  

**Tip**  

The active environment is the one with an asterisk (*).  

To change your current environment back to the default `base`:  

`conda activate`  

**Tip**  

When the environment is deactivated, its name is no longer shown in your prompt, and the asterisk (*) returns to `base`. To verify, you can repeat the `conda info --envs` command.  

#### Installing packages

You can also install packages into a previously created environment. To do this, you can either activate the environment you want to modify or specify the environment name on the command line:  

* via environment activation  
  * `conda activate myenvironment`  
  * `conda install matplotlib`  

* via command line option  
  `conda install --name myenvironment matplotlib`  

For more information on searching for and installing packages, see [Managing packages](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html).  

#### via command line option  

`conda install --name myenvironment matplotlib`  

For more information on searching for and installing packages, see [Managing packages](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html).  

#### Clone environment

`conda create --name <new_env_name> --clone <copied_env_name>`  

#### Remove environment

`conda remove --name <env_name> --all`  

### **Anaconda、conda、pip、virtualenv的区别**  

#### **① Anaconda**  

Anaconda是一个包含180+的科学包及其依赖项的发行版本。其包含的科学包包括：conda, numpy, scipy, ipython notebook等。 

#### **② Conda**  

conda是包及其依赖项和环境的管理工具。 

▪ 适用语言：Python, R, Ruby, Lua, Scala, Java, JavaScript, C/C++, FORTRAN。 

▪ 适用平台：Windows, macOS, Linux  

▪ 用途：  

① 快速安装、运行和升级包及其依赖项。  

② 在计算机中便捷地创建、保存、加载和切换环境。  

> 如果你需要的包要求不同版本的Python，你无需切换到不同的环境，因为conda同样是一个环境管理器。仅需要几条命令，你可以创建一个完全独立的环境来运行不同的Python版本，同时继续在你常规的环境中使用你常用的Python版本。——  

▪ conda为Python项目而创造，但可适用于上述的多种语言。  

▪ conda包和环境管理器包含于Anaconda的所有版本当中。  

## Additional extensions

* Python extensions
  * python
  * python debugger
  * pylance

* Jupyter extensions
  
* C/C++
  
* Ruby
  
* LaTeX extensions
  
* Github extensions
  * GitHub Pull Request extensions
  * Open in GitHub

* Markdown extensions
  * Markdown all in one
  * Markdown PDF
  * Markdown priview enhenced
  * Markdownlint

* SSH
  * Remote SSH
  * Remote SSH: Editing Configurations files
  * Remote explorer

* AI
  * Tabnine
  * GitHub copilot

* Other
  * Background
  * Paste image
  * Rainbow CSV
  * vscode-pdf

## Connect remotely to server

A good article in [zhihu](https://zhuanlan.zhihu.com/p/655276102)  

