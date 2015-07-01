Introduction to git and Source Control Management Systems
===

##GitHub and Collaborative Source Control

Now that we've learned most of the basics on our local machine, now we've got to get this setup for use with GitHub.


##What is GitHub?

[GitHub](https://github.com/) is a popular location for people to store code. During your time as a data scientist you'll frequently come across github when searching for packages, documentation, or for better understanding issues. You can do all sorts of great things with it like hosting projects or even your personal portfolio of projects.


##Getting Set up

First, you're going to need to create a GitHub account. You can do this on the [GitHub website](https://github.com/) by clicking the `Sign Up` button. Now we'll need to make sure that our local version of git can communicate with GitHub's.

Follow these instructions to set up Git and GitHub to work together.

[https://help.github.com/articles/set-up-git/](https://help.github.com/articles/set-up-git/)

Once that is set up, let's go ahead and create a repository, go ahead and create a public repository and follow the instructions!

[https://help.github.com/articles/create-a-repo/](https://help.github.com/articles/create-a-repo/)

##Committing to a Repository

Now that we've created our repository, we want to push the code we've written to it! To "push code" means to copy a branch from a local repository to a remote repository. Let's break that down

What we need:

- [X] Code (the code that we've written in our local repository)
- [X] A Local Repository (the one that we've been working with in previous lessons)
- [X] A Remote Repository (the Github repository you just created)
- [ ] A link between the remote repository and our local repository.


So we're really only missing one thing at this point, the link between the two and that's what we'll create now.

##Linking local and remote repositories

First we need to see which, if any, remote repositories we have connected to our repository. We do this by running:

```sh
git remote
```

If we run this in our local repository, we won't get any printout at all because we haven't added a remote repository yet, let's do that now.



The command to do this is `git remote add <name> <url>` (the name and url will be filled in by us).

So we need to give it a name, and a url, seems simple enough. Now by convention, the standard name for the core remote repository is `origin`. This can change as projects increase in complexity but it's what we'll be using here.

Now we need our url. On the GitHub repository page, on the right side you'll see a **Clone URL.** We'll be using this to allow our local repository to talk with our remote one. Copy the url there.

Now we can type the command into the command line.

```sh
git remote add origin git@github.com:MIDS-Python-Bridge-Course/Course-Overview.git
```

Your url will be different that the one listed above, however the layout should be the same. Now we can run

```sh
git remote
```

which should print `origin`.

##Pulling a repository

Now that we've created this remote repository, we're going to need to pull it down first in order to be able to push to it. Fundamentally, the two repositories need to be starting from the same starting point. We created a file when we created our github repository called a README and we're going to need that in our local repository before we can push code. This is common when you're working on a project with others and they committed some features while you were working on yours. A pull is simple, we just run `git pull <name> <branch>`. Now we want to pull the `master` branch from the `origin` repository so let's do that now.

```sh
git pull origin master
```

You should get a print out similar to:

```sh
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From github.com:MIDS-Python-Bridge-Course/Course-Overview
 * branch            master     -> FETCH_HEAD
   5b2de3f..7d12a82  master     -> origin/master
Updating 5b2de3f..7d12a82
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

While yours will certainly be a bit different, it will have the same basic structure. Basically we pulled down that the README file to our local repository. Now when we run `ls` we'll see the readme file in our local directory!

##Pushing code

Now that we've link our repositories and pulled down the changes, let's push our code up to that repository. Firstly we'll want to run `git status` to confirm the branch that we are on as well as what state our code is in. You cannot push code that is in `staging`, you can only push code that is committed (however you can run the command without fully committed code). For this exercise, make sure that you are on the master branch and that all your code is currently committed.

Now we can push our code, the layout of the command is straight forward `git push <remote_name> <branch>` where remote name and branch will be filled in by us. For this exercise we're going to be pushing to `origin` and we'll be pushing the `master` branch.


```sh
git push origin master
```

When we commit that we'll get some printout in return that should be similar to what is below.

```
Counting objects: 10, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (10/10), done.
Writing objects: 100% (10/10), 7.15 KiB | 0 bytes/s, done.
Total 10 (delta 2), reused 0 (delta 0)
To git@github.com:MIDS-Python-Bridge-Course/Course-Overview.git
   6e5921a..f975b78  master -> master
```

Now we're not going to concern ourself with exactly what that output is telling us, we just want to make sure that it ended positively and did not give us back an error. Now let's go look at GitHub and find our code is right there!

Congratulations, you've just pushed your first code to GitHub. We'll be doing this a lot through this course!

##Forking a repository

Now sometimes you won't be able to just push to a repository. Sometimes you'll have to have a more formal process for working with others - especially when you're working on a project where stability is important. For example, large open source projects commonly have a series of ways in which changes are controlled and people make contriubtions to repositories.

There are [several basic distributed models](http://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows) that you can read about on the git website.

Generally you'll be keeping things simple, either by being able to push directly to a repository or by simply creating a pull request. We'll get to that shortly and before we can we'll have to explain how to fork a repository.

Forking a repository is a way in which, on github, you create a copy of a repository that becomes your own copy on your own GitHub. This allows you to make any changes, and save those changes in your own repository. If you want to make a change that you believe belongs in the original repository, you can create a pull request by pushing up to your own GitHub fork, then navigating to the central repository and manually creating a pull request.

[GitHub's Pull Request Instructions.](https://help.github.com/articles/creating-a-pull-request/)

What's great about a pull request is that if you realize you may have misspelled something, or forgotten something, then you can just push again (to your repository) and those changes will be reflected in the pull request.

##Conclusion

Now you're done! You've covered the basics of git and how git works in the real work. You've created repositories on your own computer, you've forked them from other repositories, and you've pushed to other ones and you've understood how you would go about creating a pull request to work with others on projects.

For the purposes of this course, you've gotten an excellent introduction to git and the GitHub system. Don't worry if you don't understand everything in perfect detail so far. As you get more experience with GitHub, it will become more and more intuitive.

As a final word of advice, remember, any problem you ever have wanted to solve with Git has been solved before! Every single one. So, if you're ever trying to fix a problem, you can simply search for the answers on the internet - the important part is just to frame in using the "git" vocabulary. For example

- *How do you rollback a commit?*
- *how do you edit a git commit message?*

Those are questions using the contextual vocabulary. This is something that will help you over and over again in your technical and data science careers. It's essential that when you're asking technical questions, frame it using the vocabulary of the language or framework you're trying to solve the problem in.