---
layout: default
sort: 1
title: Bento Quick Start
---

# Quick Start Tutorial

## Introduction
Bento follows the principal of “Configure Locally. Deploy Globally”. An end-user installs a local version of his/her application and configures it to its desired state. The updated application is then pushed to a cloud platform. 
<br>The purpose of this tutorial is to walk the end-user through process of installing a data sharing platform on AWS. 

## Prerequisites
Before you proceed any further please ensure the instructions in this section are completed.

1. Install Git: Bento uses GitHub to commit, store and share its code base. Instructions to install Git, on your local machine, are found [here](https://github.com/git-guides/install-git). 

2. Install Docker: All code in Bento is containerized. You will need to install the following Docker components on your local machine: (a) Docker Desktop (b) Docker Engine and (c) Docker Compose.
    * Instructions to install Docker Desktop are [here](https://www.docker.com/products/docker-desktop).
    * Instructions to install Docker Engine are [here](https://docs.docker.com/engine/install/).
    * Instructions to install Docker Compose are [here](https://docs.docker.com/compose/install/).

3. Install AWS Command Line Interface (AWS CLI). Instructions to install AWS CLI are [here](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).

4. Install Terraform; instructions to install are [here](https://learn.hashicorp.com/tutorials/terraform/install-cli).

5. Install Ansible; instructions to install are [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

6. Create an account on Amazon Web Services. You will need an administrator’s role on AWS, and the ability to create cloud resources. See here for instructions on creating an AWS account.

7. Configure AWS CLI credentials. See here for instructions on configuring AWS CLI


## Fork the Bento Repos
The Bento code-base is divided into three main components: (a) the front end (b) the back end and (c) the database. The code-base for all three are stored on GitHub. Here are the repos to fork:

1.  [Front End](https://github.com/CBIIT/bento-frontend.git)

2.  [Back End](https://github.com/CBIIT/bento-backend.git)

3.  [Data Model](https://github.com/CBIIT/BENTO-TAILORx-model)

Fork each of these to create your own remote repos. Instructions on forking a GitHub repo are [here](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/fork-a-repo).

For this tutorial we shall assume that you have named your repos:
<br>`https://github.com/CBIIT/bento-demo-frontend.git`
<br>`https://github.com/CBIIT/bento-demo-backend.git`
<br>`https://github.com/CBIIT/bento-demo-model.git` 


## Set up the Bento Local Environment on your machine.
The ‘Bento Local’ environment is designed to run within Docker, on a user's local machine, and can be set up within all types of operating systems- Windows, Mac and Unix flavors. This allows users to create and deploy their local copy of Bento, with minimal changes to their local environment.
The code-base to create the local environment is available at:  `https://github.com/CBIIT/bento-local`.
For this tutorial we shall consider `$src` to be the folder in which you will store all your local code for Bento.

1.  Clone the bento-local code-base in your local machine by running the following commands in `$src`. The first command initializes a git repository in `$src`; the second, clones the bento-local repo on your machine.

    ```
    git init
    
    git clone https://github.com/CBIIT/bento-local
    ```

    This creates a `bento-local` folder under `$src`.

2. Inspect the bento-local folder, by running the following commands. 

    ```
    cd bento-local/

    ls -lh
    ```
The list of files in your  `bento-local` folder should look like this:

```
drwxr-xr-x  10 <your user name>  <your group name>    320 Oct 24 08:23 .
drwxr-xr-x   7 <your user name>  <your group name>    224 Oct 24 08:23 ..
-rw-r--r--   1 <your user name>  <your group name>   2037 Oct 24 08:23 .env
drwxr-xr-x  12 <your user name>  <your group name>    384 Oct 24 08:23 .git
-rw-r--r--   1 <your user name>  <your group name>  12904 Oct 24 08:23 README.md
drwxr-xr-x   4 <your user name>  <your group name>    128 Oct 24 08:23 dataloader
-rw-r--r--   1 <your user name>  <your group name>    454 Oct 24 08:23 dataloader.yml
-rw-r--r--   1 <your user name>  <your group name>   1306 Oct 24 08:23 docker-compose.yml
drwxr-xr-x   6 <your user name>  <your group name>    192 Oct 24 08:23 dockerfiles
drwxr-xr-x   6 <your user name>  <your group name>    192 Oct 24 08:23 initialization
```

3. Open the `.env` file using a text editor of your choice. 
    * Set the following variables: `FRONTEND_REPO`, `BACKEND_REPO`, `MODEL_REPO` to the URLS of your forked repos for the front end, back end and data model respectively. 
    * Set the variable BUILD_MODE to `dev`. Note: see [here](https://cbiit.github.io/bento-docs/installation/installing-bento-on-your-local-machine.html#overview) for a discussion on the three modes for Bento local environment.
    * Save and exit the `.env` file.


Here is what your `.env` file should like after you are done with your updates:

```
########################################
#                                      #
#      INITIALIZATION PROPERTIES       #
#                                      #
########################################

USE_DEMO_DATA=yes
# Set to "yes" to seed the project with the provided demo data set

BACKEND_REPO=https://github.com/CBIIT/bento-demo-backend.git
BACKEND_BRANCH=master

FRONTEND_REPO=https://github.com/CBIIT/bento-demo-frontend.git
FRONTEND_BRANCH=master

MODEL_REPO=https://github.com/CBIIT/bento-demo-model.git
MODEL_BRANCH=master
# Set these variables to the desired branches to use when initializing the project with Bento source code

########################################
#                                      #
#          RUNTIME PROPERTIES          #
#                                      #
########################################

BUILD_MODE=dev
# Defines the build type used when building the project. Available options are:  demo, build, dev

```

4. The `initialization` folder in `bento-local` stores the intialization scripts for the Bento local enviroment. Move to the appropriate `initialization` sub-folder: 
	*  `initialization/mac_linux` for Mac and Linux users
	*  `initialization/windows` for Windows users. 

This sub-folder stores the initialization script(s) for the relevant operating system. For Mac and Linux users, make the script executable and the run it:
```
    chmod a+x init.sh
    ./init.sh
```

This script clones the code from your three repos: front-end, back-end, data model in the `bento-local`folder and also creates a `data` folder in `bento-local`.
The initialization script will query you `use demo data [default=yes]:`. Type `yes` to include demo data in the `data` folder.

*Note to advanced users: if you have your own bento-model compliant data set as a Neo4J dump file, then you can store the dump file in the `bento-local/data` folder and rename it `bento-data.dump`. Bento will then display your data on the UI* 

5. In the `bento-local` folder start the three docker containers with the following command:
    ```
    docker-compose up -d
    ```
Downloading all the image layers and creating the Docker containers takes about 5 minutes. 

6. To test open a browser and go to URL: `http://localhost:8085/`. You should see the landing page for Bento: 
![Home](assets/bento-landing-page.png)





