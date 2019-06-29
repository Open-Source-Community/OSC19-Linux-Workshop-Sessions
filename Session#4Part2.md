# Session#4 Part 2

![](./Artwork/Session%204/logo-osc.png)

# Managing a Remote Shell

## SSH

It stands for Secure SHell
You can use it to connect to remote device. 
To connect to a server you should know its address(ip) or name (DNS server will resolve the name to ip address) and have a user in it.
**Usage** : ``ssh <user_name>@<host> -p <port_number>(defualt 22)``

**Example:**

Assume we have host : ``127.0.0.1`` and user : ``user1`` with password : ``pass``
using ***ssh*** to connect to the server : ``ssh user1@127.0.0.1``

![](./Artwork/Session%204/login%20ssh.png)

### SSH-KEYGEN

This command used to create a public and private key.
You can you thoses keys with ***ssh*** to connect the server instead the password. It's more secure than password text.

 **Usage** : ``ssh-keygen -t <encryption algorithm>``
 
 **Example:**

We want to create keys to log in  ``127.0.0.1`` with ``rsa``  algorithm.

Using ***ssh-keygen*** : ``ssh-keygen -t rsa``

![](./Artwork/Session%204/ssh-keygen.png)

This will create 2 keys (public/private) under ``~/.ss/`` directory.

We'll change the permission of the ``.ssh/`` directory using  ``chmod``
``sudo chmod -R 700 ~/.ssh/``

> **Note:** -R means recursively to change permission for all files and directories under .ssh/

After we create the keys we need to put the public key in the server side to make the server recognize us. There are many ways to do this but we will use ``scp``

### SCP

It stands for Secure CoPy

To copy from server to client :
 ``scp <user_name@host_name/ip:path_in_server> <path_in_client>``

To copy from client to server :
``scp <path_in_client> <user_name@server_name/ip:path_in_server>``

>**Note:** we need to copy the public key to the server and put it in ***.ssh/authorized_keys*** file. If it doesm't exist create it.

![](./Artwork/Session%204/scp.png)

After that we will go to ``/etc/ssh/sshd_config`` and change 3 things to **no** :

1. challengeresponseauthentication no
2. passwordauthentication no
3. usepam no

Then restart ssh service and it work fine.  ``sudo service ssh restart``

# Network Configuration

In this section we will know some commands to configure a network and some network concepts.

## Ifconfig

It stands for InterFace CONFIGurator
This command will give you some useful information about a network.
**like:** your internal ip address (you can assign a new ip address with this command too), mac address, MTU(Maximum Transmission Unit) size and also you can enable or disable a network.

When you type ``ifconfig``

It will provide you with 3 interfaces information.

![](./Artwork/Session%204/ifconfig.png)

**eth0 ->**     This for wired network
**lo ->**         This for the internal device network. [For more about lo](https://www.webopedia.com/TERM/L/loopback.html)
**wlan 0 ->** This for wifi network

Let's take a close look in **wlan0** interface :

![](./Artwork/Session%204/wlan.png)

**UP ->** means it's enable
**BROADCAST ->** means it's suppoet broadcasting
**RUNNING ->** means it's operating
**MULTICAST ->** means it's support multicasting
**MTU ->** it's the size of transmission unit (frame/packet)
**INET ->** it's the local network ip
**NETMASK ->** it's the netmask for the network. [for more info](./Session%234Part1.md#subnet-masking)
**BROADCAST ->** it's the broadcast address

### Assigning IP

``ifconfig <interface_name> <new_ip> netmask <netmask_address>``

![](./Artwork/Session%204/assign%20ip.png)

> **Note:** this will last until you close or reboot the system

***To active or inactive interface : *** ``sudo ifconfig <interface_name> up/down``

![](./Artwork/Session%204/ifconfig%20down.png)

## Ping

This command test the connectivity between 2 hosts.
We can use ``ping`` with ``-c`` option to specifiy the number of package will be sent. ``ping -c 5 www.google.com``

![](./Artwork/Session%204/ping.png)

## Traceroute

This command show you the road to reach the host and the number of hops it pass through.

``traceroute www.google.com``

![](./Artwork/Session%204/traceroute.png)

## NSLOOKUP

this command search for the ip of the given name

``nslookup www.google.com``

![](./Artwork/Session%204/nslookup.png)

## MTR

This command combines the functionality of the traceroute and pin programs in a single network diagnostic tool.

``mtr www.google.com``

![](./Artwork/Session%204/mtr.png)

## Hostname

This command for show and change the hostname

To show the hostname : ``hostname``

To change the hostname: ``hostname <new name>``

> **Note:** this name will last until you close or reboot the system. To make it permanently you should write the new name in ``/etc/hosts`` and ``/etc/hostname`` files.


## NMAP

This command is port scanner

Let's scan google ports : ``nmap www.google.com``

![](./Artwork/Session%204/nmap.png)

>**Importan Note:** every command has man options try to have fun with these options and search for they in man pages.



## Network Configuration File

In linux there are many important files to configure a network some of it are :

### /etc/hosts 

 It has ips of the local hosts

![](./Artwork/Session%204/hosts.png)

### /etc/protocols 

It has protocols and their usage

![](./Artwork/Session%204/protocols.png)

### /etc/services

It has tcp/udp services and their ports

![](./Artwork/Session%204/services.png)

### /etc/resolve.conf 

It has the ips of DNS servers

![](./Artwork/Session%204/resolve.png)

### /etc/NetworkManager/system-connections/  

This directory has all information about network you have logged in before.

![](./Artwork/Session%204/info%20of%20network.png)




 




