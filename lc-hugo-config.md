## Pre-Requisites

You should have the following things installed on your computer before you start working with a LaunchCode Education site. 
1. Hugo
2. Git
You will also need access to the LaunchCode-Hugo-Submodules Github organization.

## Set Up a New Site

The first time you set up a site, you should follow the following directions to get an understanding of each step and its effect. After that, we do have a Curriculum Initialization script that will quickly run all of these steps for you.
1. Run `hugo new site <project-name>`
2. Navigate into the new project directory.
3. Run `git init`

 Now, it is time to configure the theme. This is a two-step process.
1. `git submodule add https://github.com/LaunchCode-Hugo-Submodules/hugo-theme-relearn themes`
2. `echo 'theme = "hugo-theme-relearn"' >> config.toml`
  
  Remove the layouts, archetypes, and static directories that are provided. You will then add connections to the submodules that are in the LaunchCode-Hugo-Submodules. To do so, run the following commands in the order provided.

3. `rm -rf layouts`
4. `git submodule add https://github.com/LaunchCode-Hugo-Submodules/layouts`
5. `rm -rf static`
6. `git submodule add https://github.com/LaunchCode-Hugo-Submodules/static`
7. `rm -rf archetypes`
8. `git submodule add https://github.com/LaunchCode-Hugo-Submodules/archetypes`

With the submodules set up, you are ready to edit the configuration file. Run these two commands to do so.
  
9. `echo -e '\n[params]' >> config.toml`
10. ```echo -e "themeVariant = ['lc-light', 'lc-dark-blue', 'lc-dark-blue-two']" >> config.toml```

  You can add some content to the homepage now in order to get started editing. When you are ready to make a new chapter,  run the command hugo new --kind segment <chapter-name>.
  
## Existing Site Configuration 
  
## Initial Setup
Since you have everything set up on your computer, you can start by cloning the project. 
When you clone the project, you should use the --recurse-submodules flag. This will ensure that you receive any updates to the submodules and make sure that the submodules are connected to their remote repositories. Here is an example of how this command would look with the proper flag:
 
1. ```git clone --recurse-submodules https://github.com/chaconinc/MainProject```  

Before you start coding, navigate into one of the directories for a submodule. Run the command git status. You should be on the default branch for that submodule and see no changes staged. You can also run `git remote -v` to see that the remote of the submodule is the repository on the LaunchCode-Hugo-Submodules Github organization.
  
Once you have confirmed that the submodules are ready to go, navigate back up to the project directory and run the hugo serve command. The project should be at localhost:1313.
  
You can now edit or review the code behind the book!

## Notes on Regular Workflow
Whenever you need to run a git pull, you should do `git pull <remote-name> <branch-name> --recurse-submodules`. With this flag, when Git pulls from the remote, it will also run a fetch for each submodule. This will help you make sure that your local copy is not missing any updates to the submodules.

## Updating Submodules
If you are working on a textbook and need to update a submodule, navigate to the submodule's directory.  A submodule is its own Git repository within the project repository so you need to be within its directory to make sure you are connected to the submodule remote not the project remote.

1. Run `git log` to see the latest commits. Confirm which commit is missing and check what the name of the default branch is.
2. Run `git fetch origin`
3. Run `git merge origin/<default-branch-name>`
  
Navigate back up to the project directory. If you now have unstaged changes from the submodules to commit, do so now so you don't forget.
