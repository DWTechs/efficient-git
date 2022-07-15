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

Templates are reusable pieces of code that will help start a new project.
For example it can be a starter kit for a given framework or configuration files for container based architecture. 

The path for templates is of the form \<entity\>/template/\<language\>/\<framework\>/\<type\>/\<precision\>

- Possible \<type\>/ folders are : 
    - **starter** for starter kits
    - **conf** for configurations
- \<framework\> and \<precision\> folders are optional and may not be used if not applicable.
- \<precision\> folder allow to add a specificity to the template. Allowing us to create several templates for the same framework with strategic differences. 
- \<precision\> folder could be duplicated if more templates of the same kind are needed (ie: \<precision1\>/\<precision2\>...)

Example : 
- \<entity\>/template/javascript/angular/starter/material
For an Angular starter kit built with Material design.

This schema may not apply for every case. Like for example a microservices template which can use several languages and frameworks by definition.
In this situation we try to stay in the schema above as much as possible with a bit of flexibility, by keeping a \<language\> and \<framework\> tags. Language would be "web" as opposed to embedded or heavy client. Framework would be "microservices" as opposed to monolith. The goal is to keep a readable folder for easy understanding and access.
Then we can add a precision like "multi-repo" or "mono-repo" ti give us the ability to create both.

Example:
- \<entity\>/template/web/microservices/starter/mono-repo


### Libraries

Libraries are reusable independent code snippets that can be used and reused in several projects to perform common functions.
They are written and maintained internally by the teams and bundled as independent libraries we can publish and install with the package manager of the targeted language.

The path for libraries is of the form \<entity\>/library/\<language\>/\<framework\>/\<name\>
- \<framework\> tag is optional and may not be used if not applicable.

