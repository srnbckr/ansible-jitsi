Role Name
=========

A brief description of the role goes here.

Requirements
------------

`ansible-galaxy install -r requirements.yml`


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

```yaml
- hosts: jitsi-meet
  remote_user: jitsi
  become: true
  vars:
    certbot_admin_email: email@test.com
    certbot_create_if_missing: true
    certbot_auto_renew_user: jitsi
    certbot_auto_renew_minute: "20"
    certbot_auto_renew_hour: "5"
    certbot_create_standalone_stop_services: []
    certbot_certs:
      - domains:
          - meet.test.com
  pre_tasks:
    - name: update apt cache
      apt:
        update_cache: yes
        cache_valid_time: 600
  roles:
    - role: geerlingguy.certbot # install certbot for letsencrypt
    - role: geerlingguy.nginx # install nginx
    - role: "{{ playbook_dir }}"

```


License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
