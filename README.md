indigo-dc.galaxycloud_docker
============================

This role has been developed to be used in the Laniakea project in order to run the official [Galaxy Docker](https://github.com/bgruening/docker-galaxy-stable) containers and its flavours on a UBUNTU 20.04 Virtual Machine

Galaxy customization
--------------------

- User administrator creation
- Galaxy brand customization
- Anonymous login disabled
- Allow user creation
- Allow user impersonation
- CVMFS customization (default: data.galaxyproject.org)

Requirements
------------

This ansible role supports Ubuntu 20.04.

Minimum ansible version: 2.9.6.

Role Variables
--------------

### Main variables ###
 
``galaxy_instance_description``: set galaxy brand, **default** = "ELIXIR-IT"

``export_dir``: directory hosting Galaxy database files and docker images, **default** ="/export"

``galaxy_flavor``: "\<owner>/\<docker\>:<docker_flag\>\", set the Galaxy Docker container, **default** = "bgruening/galaxy-stable:20.05"


### Galaxy admin user creation ###

``GALAXY_ADMIN_PASSWORD``: Galaxy administrator password.

``GALAXY_ADMIN_API_KEY``: Galaxy administrator API KEY.

``GALAXY_ADMIN_EMAIL``: Galaxy administrator email.

### Role templates ###

``mygalaxyenv.j2``: env file with the environment variables needed to configure the Galaxy Docker.


Dependencies
------------

[geerlingguy.docker](https://galaxy.ansible.com/geerlingguy/docker) : install Docker engine and store the docker images inside the external volume (/export).

Example Playbook
----------------

    - name: minimum playbook
      hosts: localhost
      roles:
        - { role: galaxycloud_docker }
      vars:
        GALAXY_ADMIN_EMAIL: "<your@email>"



License
-------

Apache Licence v2

http://www.apache.org/licenses/LICENSE-2.0


Reference
---------
Galaxy docker: https://github.com/bgruening/docker-galaxy-stable

Laniakea project documentation: https://laniakea.readthedocs.io/en/latest/

Official cvmfs documentation: http://cvmfs.readthedocs.io/en/stable/cpt-repo.html
