# Linux System Administration

## Optimising Your Linux System

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

## Working with Users and Groups in Linux

### Users

- ``su <username>`` - substitute user (change user ID or become superuser)
  - by default if no name is given then become root

- ``sudo useradd -m jane`` -- create a new user or update default new user information
  -  -m, --create-home -> Create the user's home directory if it does not exist.

- ``passwd`` -- change user password
- ``sudo passwd jane``

### Groups

- ``groupadd <group_name>`` - create a new group

- ``chown <[OWNER]:[GROUP]> <name_of_file>`` - Change the owner and/or group of each file
  - eg ``sudo chown :<group_name> <file_name>``
  - eg ``sudo chown <username> <filename>``

##### Adding a user to a group

- ``usermod -a -G <group_name> <username>``
  - -a, --append -> Add the user to the supplementary group(s). Use only with the -G option.
  - -G, --groups

## Securing your Linux Server

### Object Permissions
````
 r -> 4    (read)               u -> user
 w -> 2    (write)              g -> group
 x -> 1   (execute)             o -> other
````

- ``chmod u+x <file1>``   -- add execute permissions for user
- ``chmod +x <file1>``    -- add execute permissions for all u, g and o
- ``chmod g-w <file1>``   -- remove write permissions for group
- ``chmod ug=rw <file1>`` -- make permissions for user and group read and write

### Port Scanning
- nmap - Network exploration tool and security / port scanner
- ``nmap -v -sT localhost`` or ``nmap -v -sT <some_IP>``
  - -v, for verbose
  - -sT scan using TCP connect

### Checking Network Connections
- netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
- ``sudo netstat -tupln``

<p> </p>

- ss - socket statistics
- ``sudo ss -tupln``
