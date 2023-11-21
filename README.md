Role Name
=========

This role configures a general-purpose CVMFS client on RPM-based systems.
Refer to https://cernvm.cern.ch/portal/filesystem for more general information on CVMFS.
Refer to [Accessing CVMFS](https://docs.computecanada.ca/wiki/Accessing_CVMFS) for more information on Compute Canada CVMFS.

Role Configuration
--------------

See [defaults/main.yml](defaults/main.yml).


Role Functionality
------------------

The following features are supported:
- Static repository mounts (using `/etc/fstab`) as well as the more standard method of dynamically mounting repositories using autofs
- Automatically reload configuration when the configuration file is updated
- Setting the autofs timeout
- Optional fuse3 installation
- Optionally creating a dedicated volume group, logical volume, and filesystem for the CVMFS cache
- Automatic testing and configuration validation
- Creating a CVMFS user and group with a specific UID/GID if desired (recommended for alien cache use)
- Modular installation of CVMFS configuration packages
- Support for applying any arbitrary client configuration setting

Author Information
------------------

Provided by Compute Canada under the GPLv2 license.


Example playbook
----------------

```
---

- hosts: my_nodes
  roles:
    - ansible-cvmfs-client
  vars:
    cvmfs_cache_size: "40000"
    cvmfs_http_proxy: "http://cache1.example.org:3128|http://cache2.example.org:3128"
  become: yes
  become_user: root

```
