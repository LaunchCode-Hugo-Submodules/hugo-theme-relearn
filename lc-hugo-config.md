## Pre-Requisites

You should have the following things installed on your computer before you start working with a LaunchCode Education site. 
1. Hugo
2. Git
You will also need access to the LaunchCode-Hugo-Submodules Github organization.

## Set Up a New Site

The first time you set up a site, you should follow the following directions to get an understanding of each step and its effect. After that, we do have a Curriculum Initialization script that will quickly run all of these steps for you.
1. Run hugo new site <project-name>.
2. Navigate into the new project directory.
3. Run git init.

 Now, it is time to configure the theme. This is a two-step process.
1. git submodule add https://github.com/LaunchCode-Hugo-Submodules/hugo-theme-relearn themes
2. echo 'theme = "hugo-theme-relearn"' >> config.toml
  
  Remove the layouts, archetypes, and static directories that are provided. You will then add connections to the submodules that are in the LaunchCode-Hugo-Submodules. To do so, run the following commands in the order provided.

3. rm -rf layouts
4. git submodule add https://github.com/LaunchCode-Hugo-Submodules/layouts
5. rm -rf static
6. git submodule add https://github.com/LaunchCode-Hugo-Submodules/static
7. rm -rf archetypes
8. git submodule add https://github.com/LaunchCode-Hugo-Submodules/archetypes

  With the submodules set up, you are ready to edit the configuration file. Run these two commands to do so.
  
9. echo -e '\n[params]' >> config.toml
10. echo -e '  themeVariant = ["lc-light", "lc-dark-blue", "lc-dark-blue-two"]' >> config.toml

  You can add some content to the homepage now in order to get started editing. When you are ready to make a new chapter,  run the command hugo new --kind segment <chapter-name>.
