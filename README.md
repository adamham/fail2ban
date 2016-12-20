fail2ban
=========

A brief description of the role goes here.

Requirements
------------

Ansible 2+


Role Variables
--------------

The fail2ban.local and jail.local are commented to explain how each configuration item works.

Role variables are set in defaults/main.yml

```yml
---
# fail2ban.local
fail2ban_loglevel: '3'
fail2ban_logtarget: '/var/log/fail2ban.log'
fail2ban_syslogsocket: 'auto'
fail2ban_socket: '/var/run/fail2ban/fail2ban.sock'
fail2ban_pid: '/var/run/fail2ban/fail2ban.pid'
fail2ban_dbfile: '/var/lib/fail2ban/fail2ban.sqlite3'
fail2ban_dbpurgeage: '86400'

# jail.local
fail2ban_ignoreip: '127.0.0.1/8'
fail2ban_bantime: '600'
fail2ban_findtime: '600'
fail2ban_maxretry: '5'
fail2ban_backend: 'polling'
fail2ban_usedns: 'warn'
fail2ban_logencoding: 'auto'
fail2ban_enabled: 'false'
fail2ban_filter: '%(__name__)s'

fail2ban_destemail: 'root@localhost'
fail2ban_mta: 'sendmail'
fail2ban_protocol: 'tcp'
fail2ban_chain: 'INPUT'
fail2ban_port: '0:65535'
fail2ban_agent: 'Fail2Ban/%(fail2ban_version)s'
fail2ban_banaction: 'iptables-multiport'
fail2ban_banaction_allports: 'iptables-allports'

fail2ban_action: 'action_'

# add service here
fail2ban_services:
  - name: ssh
    port: 'ssh'
    filter: 'sshd'
    logpath: '%(sshd_log)s'
    #enabled
    #protocol
    #banaction
    #action_
    #maxretry

apt_cache_valid_time: 86400
```


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      become: true
      roles:
         - fail2ban

License
-------

MIT
