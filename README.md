Sonarr
======
This role deploys [Sonarr](https://sonarr.tv), a mart PVR for newsgroup and bittorrent users.

Requirements
------------
This role requires Ansible 2.0

Supported Platforms
-------------------
- Ubuntu: 15.04
- Debian: 8
- EL: 7

Role Variables
--------------
All variables have sensible defaults, which can be found in `defaults/main.yml`.
The current version includes the following variables:

### Defaults
| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| `sonarr_user_name`  | sonarr | The user to run the Sonarr service |
| `sonarr_group_name` | sonarr | The primary group for `sonarr_user_name` to run the Sonarr service |
| `sonarr_user_uid` | 1005 | UID of the Sonarr service user |
| `sonarr_group_gid` | 1005 | GID of the Sonarr service group |
| `sonarr_user_home` | /var/lib/{{ sonarr_user_name }} | home directory for the Sonarr service user |
| `sonarr_exe_url` | _See `defaults/main.yml`_ | The remote URL to fetch the Sonarr archive from |
| `sonarr_data_path` | {{ sonarr_user_home }}/data | Root data path for the Sonarr service |
| `sonarr_dependencies` | - mono-devel | A list of dependency packages for Sonarr |
| `sonarr_mono_gpg_key` | _See `defaults/main.yml`_ | The URL to the GPG key for the Mono package repository |
| `sonarr_service_file` | | |
| `    src`                  | sonarr.service.j2 | The source template for the Sonarr service manifest |
| `    dest`                 | /etc/systemd/system/sonarr.service | The destination to deploy the Sonarr service manifest to |
| `sonarr_service_reload_command` | `systemctl daemon-reload` | The command to use when reloading the Sonarr service configuration |


Example Playbook
----------------

    - hosts: sonarr_servers
      roles:
        - role: cmacrae.sonarr

Or, passing parameter values:

	- hosts: sonarr_servers
	  roles:
	    - { role: cmacrae.sonarr, sonarr_user_name: downld, sonarr_group_name: downld }
License
-------
MIT

Author Information
------------------
Created by [Calum MacRae](http://cmacr.ae)

Feel free to:  
Contact me - [@calumacrae](https://twitter.com/calumacrae), [mailto:calum0macrae@gmail.com](calum0macrae@gmail.com)  
[Raise an issue](https://github.com/cmacrae/ansible-sonarr/issues)  
[Contribute](https://github.com/cmacrae/ansible-sonarr/pulls)  
