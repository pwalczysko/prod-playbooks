OME production services playbooks
=================================

These playbooks encapsulate the running of various production servers run by the OME team.

At the moment, only the `ome-demoserver.yml` playbook is available here. This is a playbook for OMERO.demo server on https://demo.openmicroscopy.org OMERO.server and OMERO.web. You can read more about this [OMERO.demo server on our website](https://www.openmicroscopy.org/explore/).

We are in the process of adding more OME team's production playbooks here.

For other ansible examples, see [ome.omero_server](https://github.com/ome/ansible-role-omero-server) and [ome.omero_web](https://github.com/ome/ansible-role-omero-web) roles.

Run
---

- Install `Ansible` >=2.11
- Install required roles: `ansible-galaxy install -r requirements.yml`
- Run the `ome-demoserver.yml` playbook:

```
cd playbooks
ansible-playbook --ask-become --become -i $PATH/TO/INVENTORY ome-demoserver.yml -l $YOUR-HOST-ADDRESS-OR-IP --diff
```

Note: After first successful run of the playbook, it can be of advantage to skip some roles, e.g. the `ome.ssl_certificate` role. You can use the provided tag for it:

```
cd playbooks
ansible-playbook --ask-become --become -i $PATH/TO/INVENTORY ome-demoserver.yml -l $YOUR-HOST-ADDRESS-OR-IP --diff --skip-tags "ssl"
```



Testing
-------

We test the playbooks here on Rocky Linux 9 and Ubuntu 22.04 platforms via [Ansible Molecule](https://molecule.readthedocs.io/), see test scenarios under [`molecule`](molecule).

The main components of the playbooks (roles) are being independently tested on both Rocky Linux 9 and Ubuntu 22.04. See [ome.omero_server](https://github.com/ome/ansible-role-omero-server/tree/master/molecule) and [ome.omero_web](https://github.com/ome/ansible-role-omero-web/tree/master/molecule) roles.
