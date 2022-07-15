---
title: Organization
---

## Naming rules

Simple rules to name groups, subgroups and repositories : 

- Letters are in lowercase
- No whitespace. Use dash (-) instead
- No special characters

## Folders

### Overview

Current folders : 
- **\<entity\>/project/**: contains repositories for projects
- **\<entity\>/doc/**: contains repositories for documentations
- **\<entity\>/template/**: contains repositories to help architects, tech leads and devops to start a new project faster (ie: starter kits, configurations...)
- **\<entity\>/library/**: contains repositories for reusable code over several projects. This code is bundled as independent libraries; published and installed via the package manager of the targeted language.

The goal is to keep a readable folder structure for easy understanding and access.

### Projects

Projects are applications.

The path for projects is of the form \<entity\>/project/\<city\>/\<client\>/\<year\>/\<application\>

- Add a \<service\> folder at the end in case of mutli-repos application


### Documentations

Documentations are written in Markdown and built as a website with Hugo.
The theme used is Hugo Geekdoc.

The path for documentations is of the form \<entity\>/doc/\<topic\>

Example : 
- \<entity\>/doc/git/
- \<entity\>/doc/angular/

### Templates

Templates are reusable pieces of **architectures** that will help start a new project.
For example it can be a starter kit for a given framework, configuration files for cloud computing, or a set of pre-developped services for a microservice architecture. 

The path for templates is of the form \<entity\>/template/\<family\>/\<framework\>/\<type\>/\<precision\>


- Possible \<family\>/ folders could be : 
    - **web** for web applications
    - **desktop** for desktop applications
    - **embedded** for embedded applications
- \<framework\>/ folder should be used at the architectural level only. Like "micorservices/monolith" or "cloud/on-premise" (ie: not language based frameworks like Angular or React for Javascript) 
- Possible \<type\>/ folders could be : 
    - **starter** for starter kits
    - **conf** for configurations
- \<precision\> folders is optional and may not be used if not applicable. It allows to add a specificity to the template in case you need two or more templates of the same type in the future. For example several starter kits for the same monolith framework with important strategic differences.
- \<precision\> folder could be duplicated if more templates of the same framework and types are needed (ie: \<precision1\>/\<precision2\>...)

Example for a web application starter kit based on microservices architecture: 
- \<entity\>/template/web/microservices/starter/mono-repo



### Libraries

Libraries are reusable independent code snippets that can be used and reused in several projects to perform common functions.
They are written and maintained internally by the teams and bundled as independent libraries we can publish and install with the package manager of the targeted language.

The path for libraries is of the form \<entity\>/library/\<language\>/\<framework\>/\<name\>
- \<framework\> tag is optional and may not be used if not applicable.

