# Teamspeak 3 Server Ansible Role

Basic Teamspeak 3 Server Ansible Role which is setup with Vagrant for quick setup.

## Getting Started

Make sure prerequisits are installed and follow instructions for full setup.

### Prerequisites

OS:

```
Linux (Ubuntu, Fedora, etc.)
Mac OS X
```

Packages:

```
Virtualbox
Vagrant
Ansible
git
```

### Setup

1. Install prerequsites

2. Clone the repository

```
git clone https://www.github.com/cruno91/ansiblets3server
```

2. Change directories into the project

```
cd ansiblets3server
```

3. Start the VM

```
vagrant up
```

4. Choose a host adapter for your network

You will see something like this:

```
==> default: Available bridged network interfaces:
1) enp0s31f6
2) docker0
```

Select which adapter you want to use.  This will likely be something like "eth0" or "wlps0".  On my machine it is "enp0s31f6".

Enter the number next to the adapter you want to use.

5. Wait for the machine to finish provisioning

```
PLAY RECAP *********************************************************************
default                    : ok=15   changed=13   unreachable=0    failed=0 
```

6. SSH into the VM

```
vagrant ssh
```

7. Find the log file with your teamspeak server's privilege key

```
sudo ls -al /home/teamspeak/teamspeak3-server_linux_amd64/logs/
```

You should see an output like this:

```
total 20
drwx------ 2 teamspeak teamspeak 4096 Jan  7 20:08 .
drwxrwxr-x 9 teamspeak teamspeak 4096 Jan  7 20:08 ..
-rw-r--r-- 1 teamspeak teamspeak 1625 Jan  7 20:08 ts3server_2019-01-07__20_08_23.036609_0.log
-rw-r--r-- 1 teamspeak teamspeak 2105 Jan  7 20:08 ts3server_2019-01-07__20_08_23.663876_0.log
-rw-r--r-- 1 teamspeak teamspeak  537 Jan  7 20:08 ts3server_2019-01-07__20_08_23.663876_1.log
```

You want to note the file with the "_1.log" suffix.

8. Output the contents of the log file

```
cat /home/teamspeak/teamspeak3-server_linux_amd64/logs/ts3server_2019-01-07__20_08_23.663876_1.log
```

You should see output like this:

```
2019-01-07 20:08:24.492080|INFO    |VirtualServer |1  |listening on 0.0.0.0:9987, [::]:9987
2019-01-07 20:08:24.492642|WARNING |VirtualServer |1  |--------------------------------------------------------
2019-01-07 20:08:24.492668|WARNING |VirtualServer |1  |ServerAdmin privilege key created, please use the line below
2019-01-07 20:08:24.492682|WARNING |VirtualServer |1  |token=OoT2QYnIalLsXikypOKPVEqzYQeESVVQfn7RXLu+
2019-01-07 20:08:24.492695|WARNING |VirtualServer |1  |--------------------------------------------------------
```

9. Make note of the ServerAdmin privilege key

Ex from above output:

```
token=OoT2QYnIalLsXikypOKPVEqzYQeESVVQfn7RXLu+
```

10. Get your IP Address

```
ifconfig -a
```

Note the IP Address that is on your local network and use that to connect to teamspeak.