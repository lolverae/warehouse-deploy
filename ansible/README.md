Role Name
=========

This roles serves to install minikube, kubectl and k9s in a newly created VM to host a cluster

Requirements
------------

Having the two VMS connected and recognized by each other via usernames and sharing an SSH key

Role Variables
--------------

See defaults/main.yml
And vars/main


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
