testtesttest
============

## Summary

So in case you guys weren't aware, importing a git java project into eclipse is kind of a mess.

Eclipse stores project settings in two files:
.project (for general project settings)
.classpath (for java-specific settings)
But sometimes the specific format of those files differes depending on what system and version of eclipse you're developing on. So it's not a super idea to commit both of those to a repository, if more than one person is using the repo.

So it would be cool if we could just commit the java files, and then have eclipse link a project to those files. But that's not easy either--see http://stackoverflow.com/questions/8070017/how-to-import-a-git-non-eclipse-java-project-into-eclipse.
But we're going to do that anyway. What follows is a step-by-step of how to replicate this repo.

## Setting up this repo in Eclipse

This was written for eclipse Indigo on ubuntu linux, but it should be similar for any setup.

First, make sure you have the eGit plugin for eclipse. It's the momst popular git eclipse plugin. You probably already have it.

Next, clone this repo to your system:
 - If the Git Repositories view isn't open, open it. Window > Show View > Other... > Git > Git Repositories
 - In the Git Repositories view, click 'Clone a Git Repository and add the clone to this view'. Paste in the git http url, and keep all the default settings. You can also use 'Add an existing local repository' if you've already cloned the project.

By default, this clones the project to /home/USERNAME/git/testtesttest (or a similar directory if you're not using Ubuntu), but you might have put it somewhere else. Remeber the location.

Now create an empty java project inside of the repo. In the Java perspective, that's File > New > Java Project. Name it whatever you want, but uncheck 'Use default location'. As the Location, use /home/USERNAME/git/testtesttest/java, or your own path to the project. Here, I appended the directory 'java', because I was planning on having a couple different projects in a couple different languages.

At this point, you should be able to run the project (though you might have to specify some build dependencies on a larger project). For this repository, there's a HelloWorld file you can run. Run it to make sure you're sane.
The eclipse project now knows where all the repository files are, so we just need to tell it how to update the git repo. 
Right click on the project in project view > Team > Share Project... > Git > Next. Check 'Use or create repository in parent folder of project', since we're using an existing repo. Hopefully the correct repo is already selected now. Finish.

Excellent! You* can now do a number of cool operations:

 - Save your local changes to your local repo: Team > Commit...
 - Pull remote changes to your repo: Team > Pull
 - Push your local commit to a remote repo: Team > Push to Upstream

You'll probably want to always do those in that specific order, to avoid merge conflicts. If you do have merge conflicts, it helps to know the command-line usage of git. Otherwise you'll probably be hopelessly lost about which commands to run. =/

*Well, unless you're me, you can't actually do any pushes, since you don't have write access to this repo.
