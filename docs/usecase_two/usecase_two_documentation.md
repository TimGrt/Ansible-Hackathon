# Use-Case 2 Dokumentation

!!! warning "TODO"
    Hier soll eure Dokumentation für den **zweiten** Use-Case entstehen!  

Die Dokumentation ist *einfach* Markdown, im verwendeten [*MkDocs Material*](https://squidfunk.github.io/mkdocs-material/) Theme könnt ihr noch einige zusätzliche Dinge hinterlegen. Schaut in die Doku oder auch in den *Contributing Guide* dieses Repositories.

Generell sollte die Dokumentation die folgenden Punkte enthalten:

````markdown
# Title

Brief description of the role, what it does and what not.

## Architecture

Here is a brief overview of the architecture

## Challenges and ToDo's

If anything is missing, add a short description here.

## Installation guide

Description of the installation

## Requirements

Technical requirements, e.g. necessary packages/rpms, own modules or plugins.

## Dependencies

This role expects to run **after** the following roles:
* repository
* networking
* common
* software

## Tool definition 1

Description of the first tool used

## Tool definition 2

Description of the second tool used

## Tool definition 3

Description of the third tool used

## Ansible playbook

### Role Variables

The role uses the following variables:

| Variable Name | Type    | Default Value | Description            |
| ------------- | ------- | ------------- | ---------------------- |
| example       | Boolean | false         | Brief description      |

### Tags

The role can be executed with the following tags:
* install
* configure
* service

### Example Playbook

Use the role in a playbook like this (after running plays/roles from dependencies section):
```yaml
- name: Execute role
  hosts: example_servers
  become: true
  roles:
    - example_role
```

## Authors

Tim Grützmacher - <tim.gruetzmacher@computacenter.com>
Jonathan Schmidt - <jonathan.schmidt@computacenter.com>
````
