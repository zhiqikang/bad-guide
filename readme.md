# Welcome to another bad guide to git? I guess

## TLDR

Introduction to a simple way to work with git, github and Visual Studio Code (VSCode) for complete beginners. 

## Short intro

This is a short guide that I put together for my colleagues to get familiar with git/github. 
This guide is for complete beginners, from other fields (for example, cognitive sciences), who want to use github as an overcomplicated dropbox with some versioning function. 
This guide should help you get started with using git without using command line tools. 
It should still help as a cheat sheet for some simple problems. 

In this guide, I will walk over a simple workflow where one use Visual Studio Code (vscode) to manage versioning and syncing the local files with github and use the github website to manage cooperation with other people. 

The tools you will need are:

- [Visual Studio Code](https://code.visualstudio.com/)
- [git](https://git-scm.com/downloads)
- a web browser to access github

## Advantages over other guides?

- less serious (don't laugh)
- minimum use of command line tools 
- should still stay relevant for more advanced users or bigger projects
- GUI/workflow stays similar across different OS (unlike other os dependent GUI of git)

## Better and more in depth guides

Though probably too verbose and complicated for now, the official guides

- [official guide on git website](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) 
- [documentation from github](https://docs.github.com/en)

Scientists have incorporated git into their workflow

- [git for scientist](https://milesmcbain.github.io/git_4_sci/index.html)
- [data scientists love git](https://happygitwithr.com/index.html)
- [they actually published a paper on this](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668)

*placeholder for more, a good place to practice sending pull request*

## Table of contents

This following part is structured as such

1. [why git?](#why-git-in-my-field)
2. [preparation](#preparations)
3. [single player campaign](#solo-work)
4. [multiplayer mode](#working-with-others)
5. [frequent trouble shooting](#in-trouble-here-are-some-common-problems-and-solutions)

## Why git in my field?

I am going to list a few cases where git is useful for people other than programmers. If you are reading this voluntarily, you probably also have some ideas.

A big starter is versioning. I am sure we all had a file that's named `presentationV3_final_last_edit_20210510_slight change the morning before.pptx`. Also, do you have that one colleague who would edit a file on a PC and a tablet and therefore create a thousand history conflict files in a commercial file hosting service? Yeah that used to be me. 
To avoid stuff like this, git is created as a versioning control software. It allows you to create manual checkpoints, called `commits`, for all your files that it tracks. In our case, vscode, there is a way a check all history changes of a file. On the github website, it's also possible to see all the commits that you synced to github. 
This is done by git storing all the change data in the `.git` folder in your project folder, usually as a hidden folder. Strictly speaking, this is called the git repository(repo). We can also loosely call the entire project folder a repo. 

Sharing and transferring files across different machines can also be a plus. This is simply done by syncing the local repo with the repo on github. Github allows a maximum file size of 100 MB and a maximum repo size of 5GB; however, you can have unlimited number of private repos. So if you would like to use github just to transfer files, it would still work, but definitely not the best tool on the market.

Cooperating in a group is also a huge point for developers. Within a repo, there can be multiple `branches`, like multiple "timelines". You can sometimes "prune the timeline" by just deleting the branch. You can also merge the different timelines by selecting what you would like to keep or discard from different timelines. By switching between branches within the same repo, one can safely test things out and discuss with colleagues about where the project should go. This git workflow is a widely discussed topic, like [here](https://nvie.com/posts/a-successful-git-branching-model/), [here](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows), [here](https://www.atlassian.com/git/tutorials/comparing-workflows) and [github gives a short intro as well](https://guides.github.com/introduction/flow/). Another thing you can do with git is to `fork` a repo, taking a particular version of a repo and building your own project on this project. A successful example is actually vscode, which comes from a long line of web technologies. Read more [here](https://stackoverflow.com/questions/29966093/what-is-the-visual-studio-code-editor-built-on). However, despite being an interesting topic, these are more important for bigger projects and beyond our scope in the guide. 

Maybe some system is integrated with git. For example, one of my old department can distribute a particular version of my repo across different machines by allowing them to access my repo. This is particularly useful for inviting large amount of people to do tasks on different computers at the same time. It allows me to make sure everybody gets the same tasks and keep track of what was eventually on their computer after years of time. 

Some keywords we will use later are `commit`, `branch` and `repo`. Right now, it's simple to think of commits as checkpoints; branches are different "timelines"; and repo is the encompassing "mutiverse", containing all the "timelines and checkpoints" and capable of jumping across different checkpoints. 

## Preparations

### Getting an GitHub account

It's supposed to be really easy. You can definitely find the green button which says "sign up" and easily get yourself a free, standard account. Github has made all core functionalities available for free for all users in 2020. 
However, just in case github policy changes in the future, keep an eye out on the [github account types](https://docs.github.com/en/get-started/learning-about-github/types-of-github-accounts). Make sure you can create and edit both public and **private** repos.

### Installing and setting up on your local machine

Download and run the installation file for both git and vscode. You can find some more instructions about git [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). 

After you are done, start up vscode. On the very left you will see a column of icons. Above the settings icon you can see a "profile" icon. You can log into your github account there. Some [older guide](https://code.visualstudio.com/docs/editor/github) might ask you to install a plugin called `GitHub Pull Requests and Issues` before you can log in to github, however, this feature should come out of the box as of a 2020 update to vscode.

In this section, we essentially skipped setting up your git credentials. As far as I know, on linux this can't be skipped. Check [here](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) for local setups and [here](https://docs.github.com/en/get-started/quickstart/set-up-git#setting-up-git) for github related setting up.

### If you don't have admin rights on your machine

This is probably most relevant for public Windows PCs. 
Both vscode and git offers a thumddrive version. That is, a stand alone `.exe` file capable of doing things mentioned here. The only difference, as far as I know, is that you have to manually set the path. In the vscode `Settings` panel, search for `Git: Path`. In the current version of vscode, you have to specify the path to your `git.exe` by editing the `settings.json` file. You can have a look [here](https://stackoverflow.com/questions/29971624/visual-studio-code-cannot-detect-installed-git). 
You need to watch out, due to how strings are parsed in json files, the usual forward slashes `\` needs to be written as `\\`. So an example would be `"C:\\Program Files\\Git\\bin\\git.exe"`. 

## Solo work

### Creating/Cloning/Forking a repo

There are 2 ways to create a repo. You can either create a repo and then upload the repo to github (publish to github); or you can create a repo on github, and then clone it as an existing repo.

To create a repo from scratch on your own computer, use vscode to open the folder containing your project (or an empty folder). Click the third icon on the left column (the cource control panel) and click `Publish to GitHub`. Vscode will ask you whether you want to publish it as "private" or "public" repo and ask you which files to include. After you clicked ok, you can check the github website if the repo has been successfully published. Also, in the vscode window several changes should appear. In the source control panel, you should see an empty list of changes with a dialogue bar on the top. If you make a change to your files and save it, the file should appear in this list. If you check the bottom ribbon on the left (called the git status bar), it should state `master` with a sync button on its right, both under the settings button. If you are seeing this, congrats, you have created a repo.

On the github website, you can also create a repo by clicking the `New` button on your homepage. After you input a name for the repo, you can create an empty repo. On the github page of your repo, click the green `Code` button and copy the HTTPS url for the repo to be clone. In vscode, use keys `ctrl + shift + p` (`command + shift + p`) to call the command pallette and search for `git:clone`. After you click it or press enter, paste the url you copied from github. Select a destination folder in the dialogue box after and wait a bit. If you are seeing files in this folder, congrats, you just cloned a repo. 

Sometimes you will be working on the existing work of others, either a big public project or a graduated member from your lab. A good way to leave the forerunners alone is to fork it. Go to the page of repo you want to fork and look for a `fork` button on the page. It should be on the top right corner, right under your good looking profile picture. After github has processed everything, you can clone it just like one of your own repos. 

### Creating a work branch 

When you have created or clone a new repo, its common that you land on the `master` branch. In vscode, you can check this by looking at the lower left corner on the ribbon (git status bar). Generally, it may be a better idea to create another branch and work on that branch. Normally, the master branch is seen as "stable", where changes have been discussed and finally decided. We will talk about [merging](#merging-branches) later.     

Click on the branch name, vscode will show you a list of existing branches as well as the options to create a new branch. Click on `Create new branch` and enter a name for your new branch and then you have created a branch.

On this list of branches, you can also see the hash number behind the name of each branch. It serves as an identifier for the progress/state for the indicated branch. You can find `master` as well as `origin/master` there as well. `origin/master` suggests that this branch is saved on github, as a remote branch. At this stage, they should be of the same identifier. However, later we will see, if we commited something locally without syncing the change with github, the identifier of the local branch will be different to that of the remote branch.

### Commit and sync your changes

After you have made some changes or you just feel like taking a breezer, its a good idea to frequently save your progress to git and github. Go to the vscode source control panel (the third icon on the left column looking kind of like a paw of a frog), check your changes and enter a short message on the top dialogue box. After that, click the tick or press `ctrl + enter` (`command + enter`)  to commit the changes. Vscode will alert you that there is no staged changes and ask you if you want to automatically stage and commit all changes. You should click yes and then you have commited your first changes. At this stage, you should see the sync button to the right of your branch name has changed to arrows of up and down, in particular our case, down 0 and up 1. That means you are 1 commit ahead of the remote branch. You can also click on the branch name to call the drop down list of branches. You should see different identifiers.

Simply click on the up/down arrows (where the sync button was) and vscode will automatically sync the changes with github. All is well.

For simplicity we ignored what staging means here as it's to our scope only a cache. To read [more](https://softwareengineering.stackexchange.com/questions/119782/what-does-stage-mean-in-git). We have also not talked about syncing vs push and pull actions of git. For dummy like me, I'd like to think [pull](https://www.atlassian.com/git/tutorials/syncing/git-pull) is to pull contents from github, while [push](https://www.atlassian.com/git/tutorials/syncing/git-push) is to push my changes to github. If you are one of those nerds like me who wants to know more about how syncing works, check [this](https://code.visualstudio.com/Docs/editor/versioncontrol#_git-status-bar-actions) out.

## Working with others

### Clone vs Fork and clone

If your colleague sent you a repo for you people to work on, what should you do? To clone, or to fork and then clone?

Essentially it comes down to who wants to own the repo and the state of the repo. Let's say in a situation where the colleague or the office/lab owns the repo and you just joined on this repo which is still growing and developing, it's better to clone the repo from the `owner/repo`. If you are taking over work from a previous member or want to build on an existing working project, it might be better to fork it as `your/repo` and work on it independently with your current colleagues. Watch out for licensing issues. 

There is a pretty good [section](https://happygitwithr.com/fork-and-clone.html) about the difference between the two. 

### Merging branches

Now, in this section we are talking about merging branches within one repo, where you have contributor(administrator) rights. For the moment, merging two repos is beyong the scope of this guide.

Do you remember in [branches](#merging-branches) I have very annoyingly asked you to create new branches? This is to get you used to paying attention to your branches and now your training will pay off. To merge two branches, go to the repo page on github. On the drop down menu of branches, select the branch you have been working on. If everything seems good, you should see a `contribute` button under the green `code` button. Click it and then click the green `Open pull request`. 

Most of the times github will tell you, the branches can be automatically merged. In plain text files, if there are conflicts which cannot be resolved automatically, you will be asked to examine each conflict individually and you can edit the changes straight on the webpage. If you have pictures or word `.docx` documents, I'm afraid you might have to manually check which version you would want and organize the files before opening a pull request. 

When all conflicts are resolved, you drag down to the bottom of the page and open the pull request. Then you click the `Pull requests` tab on the repo page and click accept pull request. Voila, you can now see your changes are in the master branch, and we can work further from here.  

Also, if you are wondering why github don't call it a merge request (well, gitlab actually does it), check [this](https://stackoverflow.com/questions/22199432/pull-request-vs-merge-request) out.

## In trouble? Here are some common problems and solutions

### Hey I changed the file name and then...

Stop right there criminal scum. Sorry, but unfortunately when you change the file name of a file in your repo, git considers you have deleted the original file and added a completely new file. Therefore, git will not consider them as the same file and will not continue loggin the history of the file under the same entry. Similarly, if you move a file out of the folder into another folder, git won't consider it as the same file either; as git sees it, you have deleted the file and added a new file elsewhere. 

On the other note, if you replace a file with another file that's totally different but still shared the same file name in the exact same location, git will see it as a same file. Later on, you would not understand how you changed the entirety of the file in one commit yet git will say it makes perfect sense. 

### Burn it all

With git, it's really easy to rebuild your empire after you burn it down. If you are constantly having troubles to, say, push to github or pull from github, but you can figure why on earth, it might be the time to do it. Here, have a good laugh on [xkcd](https://xkcd.com/1597/) or read more about [it](https://happygitwithr.com/burn.html).

Essentially, if you are having trouble, move your current files to a safe place, clone the repo again and move the files back. As you can imagine, this is very inelegant yet very effective to fix conflicts. I shamefully admit I do that when I don't want to figure out what went wrong. 

However, there are things to be careful about:

- commit and sync with github frequently and early
- be careful what are the files you want and avoid mixing up multiple copies of the same repo

# Help me with the guide by sending pull requests please

