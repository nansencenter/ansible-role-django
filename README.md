nansencenter.django
=========

[![Build Status](https://travis-ci.org/nansencenter/ansible-role-django.svg?branch=master)](https://travis-ci.org/nansencenter/ansible-role-django)

Initialize Django project for GeoSPaaS

Requirements
------------
See [meta/main.yml](meta/main.yml)

Role Variables
--------------

django_project_home: Home directory of the Django project
django_project_name: Name of Django project
django_conda_dir: Anaconda directory
django_env_name: Name of the anaconda environment


Dependencies
------------

See [meta/main.yml](meta/main.yml)


Example Playbook
----------------

```yml
    - role: nansencenter.django
      django_project_home: /vagrant
      django_project_name: project
      django_conda_dir: py3django
      django_env_name: /home/vagrant/anaconda
```

License
-------

GPLv3

Author Information
------------------

Anton Korosov, anton.korosov@nersc.no
Nansen Environmental and Remote Sensing Center, https://github.com/nansencenter/
