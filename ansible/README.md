Role Name
=========

This roles serves to install minikube, kubectl and k9s in a newly created VM to host a cluster.

Requirements
------------

Having the two VMS connected and recognized by each other via usernames and sharing an SSH key.

Role Variables
--------------

On **defaults/main.yml**
Variables related to target architecture and versioning of the software used.

On **vars/main.yml**
Variables used on tasks. Composed by variables on the default folder.



Example Playbook
----------------


    ---
      remote_user: ansadmin
      roles:
        - minikube


License
-------

MIT

Author Information
------------------

Alberto Olvera | https://github.com/lolverae
