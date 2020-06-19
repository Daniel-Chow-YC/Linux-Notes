# Linux System Administration

## Optimising Your Linux Sytem

### Monitoring System Resources
- ``top`` - displays Linux processes
- ``htop`` - interactive process viewer

- ``free -h`` -  Display amount of free and used memory in the system
  - -h, --human shows human readable output

- ``df -h``
  - df displays the amount of disk space available on the file system

### Managing System Processes
- ``ps aux`` - snapshot of the current processes

- ``kill`` and ``killall <some_command>``
  - killall sends a signal to all processes running any of the specified commands. Kills process by name.

- ``sytemctl`` - Use Systemctl to Manage Systemd Services
- eg ``systemctl status application.service`` or ``sudo systemctl enable application.service``

### Accessing Log Data
- ``journalctl`` - query all linux logs messages
- ``journalctl --since "10 minutes ago"``
  - used to query the contents of the systemd(1) journal / logs


- ``cd /var/log``

- ``dmesg``
  - dmesg is used to examine or control the kernel ring buffer
  - The kernel ring buffer is a data structure that records messages related to the operation of the kernel.

### Managing Process Priorities

- ``nice -n 19 <some_command>`` --> ``nice -n <niceness-value> [command args]``
  - nice - run a program with modified scheduling priority
  - Niceness values range from -20 (most favourable to the process) to 19 (least favourable to the process)
- ``renice -n -20  -p 1055``
  - -p, --pid

## Administrating Users and Groups
- ``su <username>`` - substitute user (change user ID or become superuser)
  - by default if no name is given then become root

- ``sudo useradd -m jane`` -- create a new user or update default new user information
  -  -m, --create-home, --> Create the user's home directory if it does not exist.

- ``passwd`` -- change user password