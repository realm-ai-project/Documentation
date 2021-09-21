# Documentation for REALM_AI 

The documentation website can be accessed [here](https://realm-ai-project.github.io/documentation/). 

<!-- This website is built with [MkDocs](https://www.mkdocs.org/) using a [theme](https://github.com/readthedocs/sphinx_rtd_theme) provided by [Read the Docs](https://readthedocs.org/). -->
This website is built using the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme.

## Local Setup Guide
### Installation
MkDocs can be installed through pip with the following command: 
    
    pip install mkdocs
    pip install mkdocs-material

### Starting the MkDocs Server
```
mkdocs serve
``` 
## Contributing to REALM_AI Documentation
Please refer to MkDocs' official [Getting Started](https://www.mkdocs.org/getting-started/) and [User](https://www.mkdocs.org/user-guide/) guides for detailed documentation.

### Theme Configurations
Detailed customization options can be found at Material for MkDocs' [official website](https://squidfunk.github.io/mkdocs-material/).
    
## Instructions for GitHub Pages Hosting
Please make sure to `git pull` from the `main` branch before executing the following command:
```
mkdocs gh-deploy 
```
This command automatically builds the website, copies the built files to the `gh-pages` branch, and pushes it. This should then be reflected in the [project's documentation site](https://realm-ai-project.github.io/documentation/) after a few minutes. Therefore, please do not directly modify the files from the `gh-pages` branch as any manual changes to it will be overridden whenever the above command is executed.
