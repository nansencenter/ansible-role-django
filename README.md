nansencenter.django
=========

[![Build Status](https://travis-ci.org/nansencenter/ansible-role-django.svg?branch=master)](https://travis-ci.org/nansencenter/ansible-role-django)

Initialize Django project for GeoSPaaS

Requirements
------------
See [meta/main.yml](meta/main.yml)

Role Variables
--------------
```yml
django_project_home: # Home directory of Django project
django_project_name: # Name of Django project
django_env_name: # Name of anaconda environment
django_conda_dir: # Directory for anaconda environment
django_dirs: # Names and location of directories for satellite products
django_apps: # Name of Django apps to add to 'settings.py'
django_urlpatterns: # Urls to add to 'urls.py'
django_pip_pkgs: # Packages for installations with PIP
```

Dependencies
------------

See [meta/main.yml](meta/main.yml)


Example Playbook
----------------

```yml
---
- hosts: geospaas
  vars:
    project_home:   '/vagrant'
    project_name:   'project'
    env_name: 'py3django'
    conda_dir: '/home/vagrant/anaconda'

  roles:
    - role: nansencenter.django
      django_project_home: '{{ project_home }}'
      django_project_name: '{{ project_name }}'
      django_conda_dir: '{{ conda_dir }}'
      django_env_name: '{{ env_name }}'
      django_apps:
        - geospaas.vocabularies
        - geospaas.catalog
        - geospaas.nansat_ingestor
        - geospaas.viewer
        - django_forms_bootstrap
      django_urlpatterns:
        - "path(r'^', include('geospaas.urls')),"

    - role: geospaas
      geospaas_project_home: '{{ project_home }}'
      geospaas_project_name: '{{ project_name }}'
      geospaas_env_name: '{{ env_name }}'
      geospaas_conda_dir: '{{ conda_dir }}'

  environment:
    PYTHONPATH: "/vagrant"
    PATH: "{{ conda_dir }}/envs/{{ env_name }}/bin:{{ ansible_env.PATH }}"
```

License
-------

GPLv3

Author Information
------------------

Anton Korosov, anton.korosov@nersc.no
Nansen Environmental and Remote Sensing Center, https://github.com/nansencenter/
