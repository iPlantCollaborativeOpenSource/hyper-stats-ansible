```
 __  __    __  __    ______   ______    ______
/\ \_\ \  /\ \_\ \  /\  __ \ /\  ___\  /\  __ \    ____
\ \  __ \ \ \____ \ \ \  __/ \ \  __\  \ \  __<   /  __\
 \ \_\ \_\ \/\_____\ \ \_\    \ \_____\ \ \_\ \_\  /__ /
  \/_/\/_/  \/_____/  \/_/     \/_____/  \/_/\/_/
     ______    ______   ______    ______   ______
    /\  ___\  /\__  _\ /\  __ \  /\__  _\ /\  ___\
    \ \___  \ \/_/\ \/ \ \  __ \ \/_/\ \/ \ \___  \
     \/\_____\   \ \_\  \ \_\ \_\   \ \_\  \/\_____\
      \/_____/    \/_/   \/_/\/_/    \/_/   \/_____/
      
(ansible install) 
A service to collect VM stats from libvirt.

There are two main ansible playbooks:

client.yml
-----------------
This playbook installs on every client (compute node) an nrpe configured
for hyper-stats.  Specifically, nrpe is manually built to allow plugins to
send up to 16kb of data back to nagios. The main plugin
'roles/nagios_client/files/virt-stats.py' is included as an nrpe command and
is given privelege to be run as root. This is necessary because it queries the
libvirt api for stats on all hosted vms.

monitor.yml
------------------
This playbook adds host/service definitions for each client to run the
virt-stats plugin for ubuntu/nagios3.
```

# Setup
1) Add clients (compute nodes) to `hosts`
2) Insert the monitoring server's public ip in `client.yml` as a variable
