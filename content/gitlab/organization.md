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

Existing folders : 
- \<entity\>/project/ contains repositories for projects
- \<entity\>/doc/ contains repositories for documentations
- \<entity\>/template/ contains repositories for starter kits or configurations
- \<entity\>/library/ contains repositories for reusable libraries

### Projects

Projects are applications.

The path for projects is of the form \<entity\>/project/\<city\>/\<client\>/\<year\>/\<application\>/\<service\>

### Documentations

Documentations are written in Markdown and built as a website with Hugo.
The theme used is Hugo Geekdoc.

The path for documentations is of the form \<entity\>/doc/\<topic\>

### Templates

Templates are reusable pieces of code that will help start a new project.
For example it can be a starter kit for a given framework or configuration files for container based architecture. 

The path for templates is of the form \<entity\>/template/\<language\>/\<framework\>/\<type\>
Framework may not be used if not applicable.

Possible types are : 
- **starter** for starter kits
- **conf** for configurations

Example : 
- \<entity\>/template/Javascript/angular/starter/

### Libraries

Libraries are reusable independent code snippets that can be used and reused in several projects to perform common functions.
They are written and maintained internally by the teams.

The path for libraries is of the form \<entity\>/library/\<language\>/\<framework\>/\<name\>
Framework may not be used if not applicable.

