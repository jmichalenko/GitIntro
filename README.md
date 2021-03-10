# Introduction to Git

In this lab you will learn:
-What Git is
-What GitHub is
-How to set up a 'local' Git repositroy
-How to push changes from your local machine to the cloud

Git is a version control system that lets you manage and keep track of your source code history. GitHub is a cloud-based hosting service that lets you manage Git repositories.

Imagine a situation where you are writing an essay, and you decide to make some changes.  After reading the changes, you realize the essay just isn't going in the direction you want, and would like to go back to the version you had before you made the changes.  You realize that you saved your new version with the same name, and have lost your original version ---- OH NO!

{% next %}

This is where Git comes in.  Git is a tool that tracks version history.  You have a master timeline, and can create branches off of that timeline.  You can keep the changes on separate branches, or if you decide you like the changes, you can "merge" the changes back to the master timeline.

![gitTimeline](https://raw.githubusercontent.com/jmichalenko/cs50labs/2020/gitIntro/gitTimeline.png)

{% next %}

# Install & Configure Git

1. Register for an account on [github.com](https://github.com/).

__***CS50 IDE already has git installed.  But the instructions below are included incase you want to install git on a computer at home.***__

2. [Download](https://git-scm.com/downloads), install, and [configure](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) git. Windows users please install [Git for Windows](https://gitforwindows.org/).
3. Configure git in your local environment (CS50 IDE) by typing in the following commands (Be sure to replace the information in quotes with your infromation:

```
$ git config --global user.name "FirstName LastName"
$ git config --global user.email "email@example.com"
```
4.  In the IDE, use mkdir to create a directory calle "MyBio".  Make sure to cd into the newly created folder.

```
mkdir MyBio
cd MyBio
```

5.  In this directory, initialize git by typing:

```
git init
```
This sets up a hidden folder within your MyBio folder that will keep track of version changes.  You should also see (Master) beside your prompt now.

6.  Create a file in your new directory by using the touch command:

```
touch MyBio.txt
```

7.  Double click on the file to edit it.  Type in your name, and a fake student number.

{% next %}  

# Git Workflow
![gitTimeline](https://raw.githubusercontent.com/jmichalenko/cs50labs/2020/gitIntro/gitWorkflow.png)

Git has an interesting workflow.  Once you have initialized the folder (Git init), you need to tell git which files to watch for changes.  You do this with the git add command:

```
git add MyBio.txt
```
This moves the file from the local working directory to a "staging area".

Check to make sure the file was added to the stagging area properly by typing:

```
git status
```

After we are happy with some of the changes we've made to the MyBio.txt file, we will need to "commit" this change. When a commit is made, you always need to include a message to indicate what changes were made.
```
git commit -m "Added my name and a fake student number."
```
We can check that the change was commited to the master timeline by typing:
```
git log
```
video https://youtu.be/tI2H9gLmm0M


# Creating Branches
Lets now assume that I want to make a change to my file, that I just want to try out.  Lets make a new branch:
```
git checkout -b MyBioV1
```
This creates a newbranch off of the master branch.  You should see the new branch name in brackets beside the prompt.

Lets add to the MyBio.txt file by typing in some hobbies.  "Some of my favourite hobbies are swimming, rockclimbing, and hiking."

Go through the same process as we did above adding the file to the staging area, and then commiting the changes to the new branch: git add MyBio.txt, git status, git commit -m"Added Hobbies"

You should now be able to switch between the branches and see the different versions of the MyBio.txt file.
```
git checkout master
git checkout MyBioV1
```
You can also check what branches you have:
```
git branch
```
video https://youtu.be/PnMkr8ASQcU 


# Github

Github is a cloud based repository that can store your git files and branches.  You can also add collaborators (we will look at this in another tutorial).

Navigate to github.com, and login (create an account if you havn't already).  In the top right of the screen, there is a + sign.  Click on this and choose add new reop.  Call it MyBio (it can be called anything, but this flows with our example.)  

After you create the repo, you should be able to copy the url for that repo.

video https://youtu.be/Hdcf57q3QCY 

Now, we want to link our local git repository with the cloud based github repository.

```
git remote add origin 'paste your github url here, without quotes.'
```
To double check the link worked properly:

```
git remote show origin
```

# Pushing to GitHub
Now that our local repo is linked to github, we can push the changes locally to the cloud.
Lets push the master branch first.
```
git push master origin
```
Now go to github and you should see that your MyBio.txt file has been added to the cloud based repositiory.
{% next %}
# Pushing Branches
Now lets puch the branch MyBioV1
```
git push origin MyBioV1
```
Now when you go back to github, you will notice you have two branches stored in the cloud!
# Pull Changes from Github
Now that we know how to push information to Github, we should also know how to make sure cloud based changes are uptodate on our local machine.  Cloud based changes might be made if a collaborater changed something, or if you wanted to make a quick change to a file from the github editor.

Lets add an additional hobby in the github cloud based editor in the file MyBio.txt on branch MyBioV1.

{% video https://youtu.be/rPT93lAVYfk %}

__To avoid any conflicts, always "pull" the repo to your local machine. This will update any cloud based changes onto your local machine.  Do this before you start making changes to your local repo.  Otherwise you will get ugly conflicts!__

```
git pull origin MyBioV1
```
The changes that were made in the cloud should now be changed in your local repo!

# Hand in your work
To hand this lab in, add jmichalenko as a collaborator to your new github repo.  Settings, Manage access, add collaborator.
{% video https://youtu.be/tcnOzea-OA8 %}
