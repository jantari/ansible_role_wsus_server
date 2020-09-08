WSUS Server
=========

This role installs and configures the WSUS role for Windows 2016, and Windows 2019.

Requirements
------------

There are no special requirements apart from the standard items to allow Ansible to run on the target.

Role Variables
--------------

The following variables are defined in `/vars/main.yml`:
* `install_management_tools`: Whether to install the WSUS MMC or not.  Default is `yes`
* `content_folder`: Sets the folder location for WSUS to store its content.  Default is `C:\WSUS`
* `script_folder`: Sets the folder for storing WSUS scripts. Default is `C:\WSUS\Scripts\`
* `log_folder`: Sets the folder for logging WSUS related items. Default
is `C:\WSUS\Logs`
* `products_list`: A list of products which updates will be downloaded for.  Default items are `Windows Server 2016` and `Windows Server 2019`
* `classification_list`: A list of the Update Classifications that will be enabled.  Default items are `Critical Updates` and `Security Updates`
* `use_proxy`: Used to determine if proxy for WSUS Server will be configured. Default is `no`, only applies if `wsus_port` and `wsus_proxy` are defined.
* `wsus_facts`: Determines whether WSUS facts should be returned

Dependencies
------------

There are no known dependencies.

Example Playbook
----------------

An example playbook for using this role:
```
  ---
  - hosts: all
    vars:
      ansible_user: 'administrator'
      ansible_become_user: System
      ansible_become_method: runas
      ansible_shell_type: powershell
      ansible_host_key_checking: False
      ansible_ssh_common_args: '-C -o ControlMaster=auto -o   ControlPersi
  st=180s -o StrictHostKeyChecking=no -o UserKnownHostsFile=/ dev/null'
      wait_for_sync: True
    roles:
      - wsus
```
License
-------

MIT

Author Information
------------------
