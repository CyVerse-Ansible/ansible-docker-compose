CyVerse Ansible Docker Compose
===================

This role will apply a docker compose file from a string or http link.

Requirements
------------

This role assumes you have docker installed but gives you the option to install compose.

Role Variables
--------------

The following table lists optional ansible variables along with the default values if not defined.

Variable Name | Default value if not defined | Description
------------- | ---------------------- | -----------
DOCKER_RESOURCE  | None | a required variable that is the .yaml file you want applied or an http address to one.
IS_HTTP       | true | indicates that you are using a http link to a yaml file. set to false to use a string of a full file.
IS_BASE64     | false | indicates that you are using a base64 version of a file string. set to false to use a normal string.
INSTALL_DOCKER_COMPOSE     | true | indicates if you need to install docker compose

Example Playbook
----------------

This is a sample playbook:
````
- hosts: all
  become: true
  roles:
    - ansible-docker-compose
  vars:
    INSTALL_DOCKER_COMPOSE: false
    DOCKER_RESOURCE: "version: '3'\n\nservices:\n  app:\n    build: .\n    image: takacsmark/flask-redis:1.0\n    environment:\n      - FLASK_ENV=development\n    ports:\n      - 5000:5000\n\n  redis:\n    image: redis:4.0.11-alpine"
    IS_BASE64: true
````

Author Information
------------------
Ryan Schneider (rschneider@cyverse.org)
