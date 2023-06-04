# File Manipulation

1. Create a directory called "devops" and navigate into it.

`
cloud_user@90f764fca72c:~$ mkdir devops
cloud_user@90f764fca72c:~$ ls
devops  test  test1`

2. Create a file named "file1.txt" and add some content to it.
   
   `cloud_user@90f764fca72c:~/devops$ touch file1.txt
    cloud_user@90f764fca72c:~/devops$ ls
    file1.txt
   cloud_user@90f764fca72c:~/devops$ nano fiel.txt
    cloud_user@90f764fca72c:~/devops$ cat fiel.txt
    salom bu men`

3. Make a copy of "file1.txt" named "file2.txt" in the same directory.

`cloud_user@90f764fca72c:~/devops$ cp file2.txt fiel.txt
cloud_user@90f764fca72c:~/devops$ ls
fiel.txt  file2.txt`

4. Rename "file2.txt" to "newfile.txt".

`cloud_user@90f764fca72c:~/devops$ mv fiel.txt newfile.txt
cloud_user@90f764fca72c:~/devops$ ls
newfile.txt`

5. Delete "file1.txt".

`cloud_user@90f764fca72c:~/devops$ rm -r file2.txt
`

# User Management

1. Create a new user account called "devUser" with a home directory.\

`cloud_user@90f764fca72c:/home$ sudo adduser sunnat
Adding user `sunnat' ...
Adding new group `sunnat' (1002) ...
Adding new user `sunnat' (1002) with group `sunnat' ...
Creating home directory `/home/sunnat' ...
Copying files from `/etc/skel' ...
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for sunnat
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n]
cloud_user@90f764fca72c:/home$
cloud_user@90f764fca72c:/home$ ls
cloud_user  sunnat  ubuntu
cloud_user@90f764fca72c:/home$
`

2. Grant "devuser" sudo privileges.

``

# Package Management

1. Update the package repository and upgrade all installed packages.

`
cloud_user@90f764fca72c:~$ sudo apt-get update
[sudo] password for cloud_user:
Hit:1 http://ap-southeast-1.ec2.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://ap-southeast-1.ec2.archive.ubuntu.com/ubuntu jammy-updates InRelease
Get:3 http://ap-southeast-1.ec2.archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Fetched 218 kB in 1s (163 kB/s)
Reading package lists... Done
`

2. Install the "nginx" web server package and Start the "nginx" service and verify that it is running.

        cloud_user@90f764fca72c:~$ sudo apt-get install nginx
        cloud_user@90f764fca72c:~$ systemctl status server
        Unit server.service could not be found.
        cloud_user@90f764fca72c:~$ systemctl status nginx
        ● nginx.service - A high performance web server and a reverse proxy server
        Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
        Active: active (running) since Wed 2023-05-31 14:10:51 UTC; 1min 31s ago
        Docs: man:nginx(8)
        Process: 4095 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
        Process: 4096 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
        Main PID: 4197 (nginx)
        Tasks: 3 (limit: 4632)
        Memory: 4.7M
                CPU: 30ms
        CGroup: /system.slice/nginx.service
                ├─4197 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
                ├─4199 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
                └─4200 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
        cloud_user@90f764fca72c:~$


3. Stop the "nginx" service.

        cloud_user@90f764fca72c:~$ systemctl stop nginx


# Networking

1. Check the IP address and network configuration of your machine.

        cloud_user@90f764fca72c:~$ ifconfig
        ens5: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
                inet 172.31.7.1  netmask 255.255.240.0  broadcast 172.31.15.255
                inet6 fe80::1a:7dff:fe10:68f8  prefixlen 64  scopeid 0x20<link>
                inet6 2406:da18:77c:6101:270c:52d6:eaa4:fcd9  prefixlen 128  scopeid 0x0<global>
                ether 02:1a:7d:10:68:f8  txqueuelen 1000  (Ethernet)
                RX packets 153863  bytes 191171209 (191.1 MB)
                RX errors 0  dropped 0  overruns 0  frame 0
                TX packets 29895  bytes 4557151 (4.5 MB)
                TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
                inet 127.0.0.1  netmask 255.0.0.0
                inet6 ::1  prefixlen 128  scopeid 0x10<host>
                loop  txqueuelen 1000  (Local Loopback)
                RX packets 2074  bytes 228835 (228.8 KB)
                RX errors 0  dropped 0  overruns 0  frame 0
                TX packets 2074  bytes 228835 (228.8 KB)
                TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

2. Ping a known external IP address (e.g., 8.8.8.8) to test internet connectivity.

        cloud_user@90f764fca72c:~$ ping 172.31.7.1
        PING 172.31.7.1 (172.31.7.1) 56(84) bytes of data.
        64 bytes from 172.31.7.1: icmp_seq=1 ttl=64 time=0.040 ms
        64 bytes from 172.31.7.1: icmp_seq=2 ttl=64 time=0.059 ms
        64 bytes from 172.31.7.1: icmp_seq=3 ttl=64 time=0.048 ms
        64 bytes from 172.31.7.1: icmp_seq=4 ttl=64 time=0.043 ms
        64 bytes from 172.31.7.1: icmp_seq=5 ttl=64 time=0.045 ms
        64 bytes from 172.31.7.1: icmp_seq=6 ttl=64 time=0.044 ms
        64 bytes from 172.31.7.1: icmp_seq=7 ttl=64 time=0.043 ms
        64 bytes from 172.31.7.1: icmp_seq=8 ttl=64 time=0.042 ms
        64 bytes from 172.31.7.1: icmp_seq=9 ttl=64 time=0.042 ms
        64 bytes from 172.31.7.1: icmp_seq=10 ttl=64 time=0.042 ms


3. Change the DNS server settings on your machine to use a different DNS server (e.g., Google DNS).

# Process Management

1. View all running processes on your machine.

        sudo apt-get update


2. find a specific progress by its name or ID


3. Kill a running process using its process ID.

        Which you use will determine the command used for termination. There are two commands used to kill a process:

        kill – Kill a process by ID
        killall – Kill a process by name`
        pkill - pkill java : it will close all the processes that are containing name java. 

# File Permissions

1. Create a file called "secret.txt" with sensitive information.

        touch secret.txt
        nano secret.txt
        doston@internship-01:~$ cat secret.txt
        Bu yerda bir qancha secret malumotlar bulishi kerak edi

2. Set the permissions of "secret.txt" so that only the owner can read and write, and no one else has any access.

        chmod 700  secret.txt


3. Verify the permissions by trying to access "secret.txt" as a different user.
   

        doston@internship-01:~$ ls -l
        -rwx------ 1 doston doston      57 Jun  2 09:45 secret.txt

# Shell Scripting

1. Write a shell script that takes a directory path as an argument and lists all the files in that directory.

        doston@internship-01:~$ ls rustam/
        rustam1.txt  rustam2.txt

2. Make the script executable and run it, passing a directory path as an argument.

        nano shellExam
                 #!/bin/bash
                echo "Today is " `date`

                echo -e "\nenter the path to directory"
                read the_path

                echo -e "\n you path has the following files and folders: "
                ls $the_path
        - chmod u+x shellExam
        - bash shellExam
                Today is  Fri Jun 2 05:30:34 PM +05 2023

                enter the path to directory
                you path has the following files and folders:
                go  kind  mv  My_Portolya  rustam  secret.txt  shellExam  sunnat



#  Cron Jobs

1. Create a cron job that runs a script every day at a specific time.



# Log analysis

1. View the contents of a log file (e.g., /var/log/syslog) and identify specific events or errors.

2. Use the "grep" command to search for specific patterns or keywords in the log file.

        grep -w type *

3. Filter the log file output to show only specific types of logs (e.g., errors, warnings).

        grep "type" new


# System Monitoring

1. Use the "top" command to monitor system resource usage (CPU, memory, etc.).


```
doston@internship-01:~$ top
top - 19:05:45 up 36 days,  9:17,  0 users,  load average: 0.58, 0.63, 0.64
Tasks: 197 total,   1 running, 195 sleeping,   1 stopped,   0 zombie
%Cpu(s): 33.3 us,  2.0 sy,  0.0 ni, 64.5 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
MiB Mem :   1927.7 total,    284.6 free,    887.2 used,    755.9 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    822.8 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0  166712  10404   6488 S   0.7   0.5 160:19.28 systemd
   5269 syslog    20   0  222400   5024   2792 S   0.3   0.3  23:51.08 rsyslogd
  39603 root      20   0 1357596  14828      0 S   0.3   0.8 145:09.42 containerd
 123847 root      20   0       0      0      0 I   0.3   0.0   0:00.04 kworker/1:3-events
 124866 doston    20   0   10900   4284   3436 R   0.3   0.2   0:00.03 top
3010855 mysql     20   0 1785568 356044    624 S   0.3  18.0  23:07.59 mysqld
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.77 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp
```

2. Identify the processes consuming the most system resources. 

```
doston@internship-01:~$ ps -eo pid,ppid,cmd,comm,%mem,%cpu --sort=-%mem | head -10
    PID    PPID CMD                         COMMAND         %MEM %CPU
3010855       1 /usr/sbin/mysqld            mysqld          18.0  0.5
 127739       1 /usr/local/bin/k3s server   k3s-server      12.1  109
3010815   59212 node /home/azikreed/coworki node /home/azik  3.7  0.2
  90788   59212 node /home/azikreed/excel-m node /home/azik  3.2  0.6
  59212       1 PM2 v5.3.0: God Daemon (/ho PM2 v5.3.0: God  2.1  0.1
1923704 1923681 python bot.py               python           1.6  0.0
3457607       1 /usr/bin/dockerd -H fd:// - dockerd          1.4  0.0
4107080       1 /sbin/multipathd -d -s      multipathd       1.3  0.0
3324202 3324179 postgres                    postgres         1.0  0.0
```

3. Experiment with different sorting options and customize the "top" output.

``` ps -eo pid,ppid,cmd,comm,%mem,%cpu --sort=-%mem | head -10

- Bu yerda  -eo pid,ppid,cmd,comm,%mem,%cpu lar kategoriyalar hisoblanib ularning qaynisini qo'llash uzimizga bog'liq
```






























