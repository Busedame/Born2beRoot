# Born2beRoot, notes

Created by: Natalie
Created time: January 9, 2024 5:08 PM

# Born2beRoot - a peak into the basics of system administration🖥️

## ✅Chapter 1 - Important words and expressions:

### Virtual Machine 💻

A virtual machine (VM) is a software emulation of a computer system. 

—> It operates based on computer architecture and functions **like a physical computer**. 

—> Its implementation involves specialized software, called a **hypervisor (Oracle VM VirtualBox)**, that separates the VMs from the host system, allocating resources to each VM as needed.

**********************************How does it work?**********************************

- The VM includes a full copy of an operating system, the application, necessary binaries, and libraries - everything needed to run the application that the VM was designed for.
- This allows the VM to run as an independent system, isolated from the host and other VMs.

**************What is the purpose of a virtual machine?**************

- Can be used to test applications in a safe, separate environment. Works by using software to simulate virtual hardware and run on a host machine.
- This isolation provides a secure environment where applications can run **without affecting the rest of the system.**
- It also **allows for the running of different operating systems simultaneously** on the same physical machine. For example, you could run a Linux VM on a Windows machine.

### Debian VS Rocky⚖️

**************************************************What is Debian and Rocky?**************************************************

- Debian and Rocky Linux are both **distributions** of the Linux operating system.
- **Distribution** = A particular **version of the operating system** that includes the Linux kernel, system utilities, and applications, all bundled together.
    
    —> Each distribution may have different default settings, software packages, and system configurations, which can lead to different user experiences even though they're all based on the same underlying Linux kernel. 
    
    —> Examples of Linux distributions include Debian, Ubuntu, Fedora, and Rocky Linux.
    

**Why did I choose Debian?**

- It's **known for its stability and reliability**, which makes it a popular choice for servers.
- It has a large repository of precompiled packages, which can make **software installation easier**.
- It uses the **APT package management system,** which is powerful and flexible.
- It's not tied to any commercial entity, which is pretty nice for ethical or independence reasons 😊

**What’s the main differences between Debian and Rocky?**

**Package Management**: 

- Debian uses the **Advanced Package Tool (APT)** for package management.
- Rocky Linux uses the **Yellowdog Updater, Modified (YUM).**

**Software Availability**: 

- Debian has one of the largest software repositories, which means a **wide range of applications are readily available for installation**.
- Rocky Linux, being a CentOS replacement, focuses more on stability and compatibility with Red Hat Enterprise Linux, and might **not have as extensive a software repository.**

**Release Cycle**: 

- Debian has a longer release cycle, with new stable versions released approximately every two years.
- RockyLinux aims to provide a stable, production-ready enterprise platform, and its release cycle follows that of RHEL.

**Community and Support**: 

- Debian has a **large, active community** and a wealth of online resources due to its long history.
- Rocky Linux, while newer, has a **growing community** and is backed by the creator of the CentOS project.

### UFW🔥

- **Uncomplicated Firewall**. A program to administrate a Firewall, designed to be simple to use.
- You use it to configure which ports to allow connections to and which ports to close.

### Net-tools🛜

- A package of **networking utilities**, used for various
networking tasks and diagnostics. For instance:
→ **ifconfig** | Used to configure network interfaces + display it.
→ **route** | Displays and manipulates the IP routing table.
→ **netstat** | Network connections, routing tables etc.
→ **arp** | Address Resolution Protocol cache, display/modify.
→ **iptunnel** | Configures IPv4 and IPv6 tunnels.

### Crontab🕰️

- A **script/command** can be ran in **specified intervals** -
like a **"every five minutes, do this" kinda thing.**
- **sudo crontab -u root -e** —> This is the command to modify the intervals.
- **sudo systemctl disable cron.service** —> This is the command to disable cron-service.
- **sudo systemctl enable cron.service** —> This is the command to enable cron-service.

### LVM🗄️

- **Logical Volume Manager** - allows us to easily manipulate the partitions or logical volume on a storage device.
- Instead of being limited by the fixed sizes of partitions, with LVM you can **allocate disk space into logical volumes, which can be easily resized and moved around almost at will.**
- In LVM, the physical hard drive partitions are treated as physical volumes. Multiple physical volumes can be combined to create a volume group. From a volume group, logical volumes can be allocated. These logical volumes hold the file systems.

The main advantages of LVM include:

- The ability to **use space from multiple physical volumes as if they were one.**
- The ability to **resize logical volumes as needed (even while they're in use).**
- The ability to **take snapshots of the system at a particular point in time.**

### Package management (Apt and aptitude)📦

- **Packages** = Collections of files that allow you to install and run
software on your system
- **Apt** = **Advanced Package Tool**. A command-line tool that simplifies the
process of managing packages. It provides commands for installing,
upgrading and removing software.
- **Aptitude** = A higher-level interface for the package management
system. It provides text/based interface and **more advanced features
than apt**, such as the ability to resolve complex dependency issues.
**Is considered more user-friendly than apt.**
- Some examples on the **difference between apt and aptitude:**
    
    —> Aptitude installs suggested packages by default, apt does not.
    
    —> Aptitude provides more extensive logging than apt.
    

### Linux security modules (SELinux and AppArmor)👮🏾

—> Provide a way to support access control security policies. Debian has 

AppArmor set as a default security model.

- **SELinux** = Security-Enhanced Linux. Operates on the principle of
"**default deny**" - if a specific rule allowing access doesn't exist,
then access is denied. Use command **sestatus** to see the status.
- **AppArmor** = Application Armor. Path-based and simpler to set up/
manage. Contrary to SELinux - it's following the "**default allow**"
principle - if a rule DENYING access doesn't exist, then access
is allowed. Use command **sudo apparmor_status** to see the status.l

### SSH (Secure Shell Host)🔑

- Cryptographic network protocol for **operating network services/
sending commands securely over an unsecured network.**
- **Commonly used to log into a remote machine and execute commands.**
- SSH uses **public-key cryptography** to authenticate the remote
computer and allow the remote computer to authenticate the user,
if necessary.
- **Securely transferring** files between machines.
- Private and public key to authenticate users.
- **Allows you to execute a command on a remote machine without
logging in to a shell session.**
- **Port forwarding/tunneling:** Allowing access to another server on the
same network as the SSH server, but via a different port. Two ways -
either local or remote.
    
    —> **Local** = allows you to connect from your
    local machine to another server. 
    
    —> **Remote** = allows the server to connect
    to a port on your machine.
    
- Command execution: Allows you to execute a command on a remote
machine without logging into a shell session. You could use SSH to
execute a backup script on a remote server from your local machine.
The command would be executed in the context of the remote machine,
not your local one.

**********************************Using SSH to connect from local computer to virtual machine:**********************************

> ssh [nholbroo@127.0.1.1](mailto:nholbroo@127.0.1.1) -p 4243
> 

SSH is secure because **it uses encryption to protect the data that's being transmitted between your local machine and the remote machine**. 

- When you type in your **password, it's not being sent in plain text that could be intercepted and read**. Instead, it's encrypted before it's sent and then decrypted on the other end.
- The '-p 4243' in your command specifies the port number to connect to on the remote machine. This is part of the network protocol and doesn't directly affect the security of the SSH connection.
- However, using a **password for SSH does have some potential security risks**. If someone else can guess or find out your password, they could potentially use it to connect to your remote machine. That's why it's recommended to use **SSH keys instead of passwords when possible**. SSH keys are much more difficult to crack than passwords.

### IP-address and ports🌃

> A little metaphor to understand IP-addresses, ports and SSH.
> 

Imagine a city.

An IP-address is one address in the city, and in the address there are many ports (apartments).

An SSH-server is one of the apartments in the address - and if you give your keys to someone

else, they can access the apartment, even though they don’t know what is inside the lock.

**Public key** → The physical key (you can give it to someone else)

**Private key** → The lock (it just is there, you can’t see what it’s made of)

### Sudo🦹🏽‍♀️

- **Sudo** = “Superuser do”. When used a user can run programs with the security privileges of another user. Every part of the sudoers-file is parsed whenever the sudo command is entered.
- **Root user/Super user**= "Administrator". It's the most powerful user in a Unix-like operating system, with the ability to read, write, and execute any file.This user automatically has the rights to do whatever - while the sudo command can “manipulate” a non-root user to have similar rights.
- ************************Host name************************ = The name of the computer. A label that is assigned to a device connected to a computer network and that is used to identify the device in various forms of electronic communication, such as the internet.

## ✅Chapter 2 - How to get around in directories:

### cd **/**

—> Goes to the **root directory**. Home -> username goes into the user, which
is normally where I start on the school computer.

### /bin

—> Contains **binaries or executables** that are **essential to the operative
system**. You can run these commands from anywhere, like "ls" or "lsblk".

### /sbin

—> Contains **system binaries or executables,** that are **essential to the operative
system, but *only accessible for super user (root)***. Commands like "deluser".

### /lib

—> **Shared code between binaries.** Many of the commands from sbin and
bin have shared libraries, that are stored in /lib.

### /usr/bin

—> Contains **user binaries or executables** that are **NOT essential
to the operative system**, only intended for the user.

### /usr/local/bin

—> Contains **user binaries/executables** that are **NOT essential
to the operative system, and are compiled MANUALLY**. To provide a safe place
that won't conflict with any software installed by a system package manager.

<aside>
💡 All the binaries get mapped together with a **path environment variable.** That's
why you can use commands from wherever.

</aside>

<aside>
💡 If you ever wonder where a binary is stored - and what type of binary it is - you can use this command:

**which <command>**
*Example: which norminette || which ls*

</aside>

### /etc

—> If you want to customize the behavior of the software in the system.
**Editable text configuration**. 

—> .conf-files are text-based configurable files.

—> **This is where I edited password policies:**
——> How often to change password etc: **vim /etc/login.defs**
——> Change the password strength, how many tries, how the
password should look like etc: **vim /etc/pam.d/common-password**

<aside>
💡 You can also use the command **vim /etc/security/pwquality.conf** for a
more visually pleasing password policy overview (plus the abillity to change enforce_for_root).

</aside>

—> **And also where I edited sudo rights:**
——> **The path** to the file which contains sudo rights: **sudo vim /etc/sudoers**
——> **For actually changing** who has sudo rights and similar: **sudo visudo**

******NB! USE SUDO VISUDO COMMAND IF YOU ACTUALLY WANT TO MODIFY THE CONTENT FOR SUDO RIGHTS.******

### /boot

—> The files needed to **boot the system**, like the Linux kernel itself.

### /dev

—> **Device files**. You can interface with hardware/drivers, as if they
were regular files. You might create disk partitions here.

### /opt

—> Optional/add-on software.

### /var

—> **Variable files that will change** as the operative system is being used
(logs, cache-files, etc.). 

—> The **/var/log contains various log files** generated by system processes,
applications, and services.

—> ****Also sudo logs:
**The command “vim /var/log/sudo” makes me see when sudo command was used, and where.**

### /tmp

—> Temporary files, that will no longer exist the next time the system
is getting booted.

### /proc

—> An illusionary file system, that doesn't really exist on the disk.
—> It is created in memory on the fly by the Linux kernel - to keep track of running
processes.

## ✅Chapter 3 - Changing the sudo policies:

These are the different Defaults that were set (changed through command **sudo visudo**, and located in the file **/etc/sudoers):**

**Defaults  passwd_tries=3**

- Total tries for entering the sudo password

**Defaults  badpass_message="Password is wrong, please try again!"** 

- The message that will show up if password fails.

**Defaults  logfile="/var/log/sudo/sudo.log"**

- Path to the sudo log-file.

**Defaults  log_input, log_output**

- What will be logged in sudo log. Stores the command input and output whenever the sudo command is used.

**Defaults  iolog_dir="/var/log/sudo"**

- In which directory is the sudo log stored.

**Defaults requiretty**

- You can't run scripts/other automated tasks with the sudo command - it can only be written in the terminal (TTY).

**Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"**

- Folders that will be excluded of sudo.

**Defaults env_reset**

- Resets the user's environment to a set of predefined values when sudo command is run. Security measure - avoiding the behavior of sudo command being influenced by the user.

**Defaults mail_badpass**

- Sends an email to the system administrator whenever a user enters an incorrect password for the sudo command. Security measure.

> I also changed the sudo rights for different users:
> 

```jsx
User privilege specification
nholbroo        ALL=(ALL:ALL) ALL
root            ALL=(ALL:ALL) ALL

Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
nholbroo ALL=(ALL) NOPASSWD: /usr/local/bin/monitoring.sh
```

`nholbroo/root ALL=(ALL:ALL) ALL`: 

- This line allows the user `nholbroo` to run any command as any user on any host.
- The first `ALL` specifies that this rule applies to all hosts.
- The `=(ALL:ALL)` part means `nholbroo` can run commands as any user or any group.
- The last `ALL` means `nholbroo` can run all commands.

`%sudo ALL=(ALL:ALL) ALL`: This line allows any user in the `sudo` group to run any command as any user on any host.

`nholbroo ALL=(ALL) NOPASSWD: /usr/local/bin/monitoring.sh`: 

- This line allows `nholbroo` to run the `monitoring.sh` script as any user without needing to enter a password.
- The `NOPASSWD:` directive makes this possible.

## ✅Chapter 4 - Script:

### What does the script look like when it’s executed?

Broadcast message from nholbroo@nholbroo42 (pts/0) (Tue Jan  9 19:46:21 2024):

```
#Architecture: Linux nholbroo42 6.1.0-17-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.69-1 (2023-12-30) x86_64 GNU/Linux
#CPU physical: 1
#vCPU: 1
#Memory Usage: 215/960MB (22.40%)
#Disk Usage: 1704/13Gb (16%)
#CPU load: 100.0%
#Last boot: 2024-01-09 19:05
#LVM use: yes
#Connections TCP: 2 ESTABLISHED
#User log: 2
#Network: IP 10.0.2.15  (08:00:27:02:ee:f0)
#Sudo: 31 cmd

```

### #!/bin/bash

- Means Shebang. It tells the system what interpreter to use to execute the
script - in this case Bash shell.
- This is so you can run the script by
typing its name in the terminal, without having to precede it with bash.
- You still have to be in the right directory or make a path to be able to
execute it.
- Like this: ./monitoring.sh
Instead of this: bash ./monitoring.sh

### 1. Architecture

- Provides system information.

Shows like this: 

```jsx
#Architecture: Linux nholbroo42 6.1.0-17-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.69-1 (2023-12-30) x86_64 GNU/Linux
```

> **Command: uname -a**
> 

**What does the command do?**

—> **uname** would in itself simply just output the kernel name “Linux”.
—> With the **-a flag**, which means "all", it gives more detailed information.

**This is the information being shown:**

1. **Kernel name** - Linux.
2. **Host name**: nholbroo42
3. **Kernel release:** 6.1.0-17-amd64
4. **Kernel version** (incl. the date the kernel was compiled): 1# SMP
PREEMPT_DYNAMIC Debian 6.1.69-1 (2023-12-30)
5. **Machine's hardware architecture:** x86_64. Can sometimes show more, like
processor type and hardware platform - but in this case only shows one -
might be because they are all the same. Indicates that it is a 64-bit
system.
6. **Operating system:** GNU/Linux

<aside>
💡 **"|"** is called a pipe, and it takes the **output of the command
on its *left*** and uses it as the **input for the command on its *right.***

</aside>

### 2. CPU Physical

- The physical core count of a Central Processing Unit. A processor
unit that reads and executes instructions.
- **The number of cores affects the performance as several cores can allow for more tasks to happen at the same time.**
- The performance still depends on the computer's ability to deal with multiple cores.

Shows like this:

```jsx
#CPU physical: 1
```

> **Command: grep "physical id" /proc/cpuinfo | sort | uniq | wc -l**
> 

**What does the command do?**

- **grep "physical id" /proc/cpuinfo** —> Searches for the lines *containing* "physical id" in the targeted file.
- **sort** —> Sorts the output from the previous command
- **uniq** —> Removes duplicate lines from the sorted output
- **wc -1** —> Counts the number of lines in the final output, which corresponds to the
number of physical CPUs, which then again is the final output.

### 3. vCPU

- Virtual CPU - the **portion of a physical CPU** that is assigned to a
Virtual Machine.
- The hypervisor (e.g. Oracle VM VirtualBox) manages VMs and
controls the distribution of vCPUs to different VMs.
- **Multiple VMs can share the resources of one single physical CPU.**
- **In my case, I have assigned one CPU to my VM, and one portion (vCPU) from that
specific CPU.**

Shows like this:

```jsx
#vCPU: 1
```

> **Command: grep "^processor" /proc/cpuinfo | wc -l**
> 

**What does the command do?**

- **grep "^processor" /proc/cpuinfo** —> Searches for the lines *starting with* "physical id" in the targeted file.
- **********wc -1********** —> Counts the number of lines in the final output, which corresponds to the
number of processors, which then again is the final output. Processors in this
case will correspond to the number of vCPUs.

<aside>
💡 Bash scripts can operate with “variables” in the same way as C.

**uram=$(free -m | awk '$1 == "Mem:" {print $3}')**

In this case “uram=$” indicates that it is a variable, and its value given by the command, will show in the output like this:
#Memory Usage: **$uram**/${fram}MB ($pram%)

</aside>

### 4. Memory Usage

- Refers to the **amount of memory that is currently being used by processes in your system.**
- The processes can include system processes, user applications, and so on.
- Typically refers to the **amount of RAM currently being used.**
- **In this case it is shown as MB.** It shows the amount of MB RAM that is being used, compared to the total amount of MB available.

Shows like this:

```jsx
#Memory Usage: 215/960MB (22.40%)
```

> **Command 1: free -m | awk '$1 == "Mem:" {print $2}’** (Total available RAM)
> 

> **Command 2: free -m | awk '$1 == "Mem:" {print $3}'** (RAM being used)
> 

> **Command 3: free | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}’** (Percentage of RAM being used compared to total amount of RAM)
> 

**What does the command do?**

**Command 1**

- **free -m** —> “Free” displays the total amount of **free and used physical + swap memory in the system**, as well as the buffers and caches used by the kernel. **The -m flag displays the information in megabytes**.

The “free -m”-command would output this in itself:

```
              total        used        free      shared  buff/cache   available
Mem:           7862        1256        4741         140        1864        6232
Swap:          2047           0        2047
```

- **awk** —> A text processing command in Unix. It's used to manipulate data and generate reports. The `awk` command processes the output line by line.
- **awk '$1 == "Mem:" {print $2}’**
1. **‘$1 == “Mem:”** —> This is a condition that checks if the **first field/column of a line** is "Mem:". If the condition is true, which it is in this case, it goes on to the next step.
2. **{print $2}** —> Prints the second field/column of the line, which shows the **total available RAM.**

****Command 2****

- This command does the same as the previous one, only difference is the field/column being printed.
1. **{print $3}** —> Prints the third field/column of the line, which shows the **amount of RAM being used.**

****Command 3****

- A little reminder: **free | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}’**
- `printf("%.2f")` —> a function that prints a formatted string.
- The `%.2f`is a format specifier - it means that the **number should be printed as a
 floating-point number** with 2 digits after the decimal point.
- In this case, it's used to print the result of `$3/$2*100`. `$3` and `$2` refer to the third and second fields of the line, respectively. So `$3/$2*100` **calculates the percentage of used memory.**

### 5. Disk Usage

- Refers to the **amount of storage space that is currently being used** on your computer's hard drive or other storage devices.
- **In this case it is shown as MB.** It shows the amount of MB storage space that is being used, compared to the total amount of GB available.

Shows like this:

```jsx
#Disk Usage: 1720/13Gb (16%)
```

> **Command 1: df -BG | grep '^/dev/' | grep -v '/boot$' | awk '{ft += $2} END {print ft}'** (Total amount of disk space available)
> 

> **Command 2: df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} END {print ut}'** (Total amount of disk space used)
> 

> **Command 3: df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} {ft+= $2} END {printf("%d"), ut/ft*100}’** (Percentage of disk space being used compared to total amount of disk space)
> 

**What does the command do?**

******Command 1******

- **df -BG** —> `df` reports the **amount of disk space used by file systems**. The `-BG` **option stands for "gigabytes"**.

The “df -BG”-command would output this in itself:

```
Filesystem                      1G-blocks  Used Available Use% Mounted on
udev                                   1G    0G        1G   0% /dev
tmpfs                                  1G    1G        1G   1% /run
/dev/mapper/nholbroo42--vg-root        3G    2G        2G  57% /
tmpfs                                  1G    0G        1G   0% /dev/shm
tmpfs                                  1G    0G        1G   0% /run/lock
/dev/mapper/nholbroo42--vg-home        7G    1G        7G   1% /home
/dev/mapper/nholbroo42--vg-var         2G    1G        1G  38% /var
/dev/mapper/nholbroo42--vg-tmp         1G    1G        1G   1% /tmp
/dev/sda1                              1G    1G        1G  25% /boot
tmpfs                                  1G    0G        1G   0% /run/user/1000
```

- `grep '^/dev/'` filters the output to **only include lines that start with '/dev/'**.
- `grep -v '/boot$'` further filters the output to **exclude lines that end with '/boot'.** **The `-v` option is what makes it exclude instead of include.**
- `awk '{ft += $2} END {print ft}'` is an `awk` command that **adds up the values in the second field of each line (which, in the output of `df -BG`, represents the size of each file system)** —> **and then prints the total at the end.**
- `{ft += $2}`: This is executed for each line. `$2` **refers to the second field in the line.**
- `ft` is a variable that `awk` is using to keep a running total of the values in the second field. So for each line, `awk` adds the value of the second field to `ft`.
- `END {print ft}`: This is executed after all lines have been read. `END` is a special pattern that matches the end of the input. When `awk` has finished reading all the input, it prints the final value of `ft`, **which is the total of all the values in the second field.**

<aside>
💡 Awk variables like “ft” and “ut” are dynamically created, and don’t need to be declared first. If they already exist, the already existing variables will be used. If they don’t exist, they will automatically be created and initialized to 0.

</aside>

******Command 2******

- A little reminder: **df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} END {print ut}'**
- **df -BM** —> `df` reports the **amount of disk space used by file systems**. The `-BM` **option stands for "megabytes"**.
- `awk '{ut += $3} END {print ut}'` **adds up the values** in the third field of each line (which, in the output of `df -BM`, represents **the used space of each file system**), and then **prints the total at the end.**

******Command 3******

- A little reminder: **df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} {ft+= $2} END {printf("%d"), ut/ft*100}’**
- Follows the same procedure as the two previous commands, by adding together and storing the values from column 2 and 3, but the output is different in the end.
- When `awk` has finished reading all the input, it calculates the ratio of `ut` to `ft`, multiplies it by 100 to get a percentage, and **then prints this percentage as an integer** (`%d` is the format specifier for an integer in `printf`).

### 6. CPU load

- A measure of the **amount of computational work** that a computer's processor (CPU) is doing.
- It's important to note that consistently high CPU load can lead to performance issues, as the CPU doesn't have any spare capacity to handle additional tasks.

Shows like this:

```jsx
#CPU load: 0.0%
```

> **Command: top -bn1 | grep '^%Cpu' | cut -c 9- | xargs | awk '{printf("%.1f%%"), $1 + $3}'**
> 

**What does the command do?**

`top -bn1`:

- The `top` command provides a dynamic real-time view of a running system.
- When `top` is run in batch mode with the `-b` option, **it doesn't expect any user input and outputs the result just once, or as many times as the**  `-n1` **option tells it to.**
- The `-n1` option tells `top` to **only run once**, instead of continually updating.

The first part “top -bn1”-command would output this in itself: (it is very long):

```
top - 15:25:00 up  2:03,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
**%Cpu(s):**  0.0 us,100.0 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :    960.8 total,    731.2 free,    224.7 used,    139.2 buff/cache     
MiB Swap:    976.0 total,    976.0 free,      0.0 used.    736.1 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0  102064  12220   9180 S   0.0   1.2   0:00.40 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par+
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 slub_fl+
```

- `grep '^%Cpu'`: This filters the output of the `top` command to **only include lines that start with '%Cpu'**, which typically contains the CPU usage statistics.
- `cut -c 9-`: This **trims the first 8 characters from each line**, effectively removing the '%Cpu(s):' part (in ******************bold text****************** in the example over) and leaving only the numbers and their associated categories (The rest of the yellow line in the example over; us, sy, ni, id, wa, hi, si, st).
- `xargs`: This is used to **convert the input from standard input into arguments for the next command**. In this case, **it's used to convert the multi-line output from** `cut` **into a single line.**

`awk '{printf("%.1f%%"), $1 + $3}'`: 

- This `awk` command adds the first and third fields (which are the user (`us`) and system (`sy`) CPU usage percentages).
- It prints the result with one decimal place (eg. 0,0 %).
- The '%%' in the `printf` statement is an escape sequence that prints a single '%' character.

### 7. Last boot

- Shows the **date and time of the last system boot** (when was the last time the machine was started/booted).

Shows like this:

```jsx
#Last boot: 2024-01-10 13:21
```

> **Command: who -b | awk '$1 == "system" {print $3 " " $4}'**
> 

**What does the command do?**

`who -b`: 

- The `who` command is used to get **information about the system and the users.**
- The `-b` option specifically retrieves the **time of the last system boot**.

The “who -b”-command would output this in itself:

```
system boot  **2024-01-10 13:21**
```

`awk '$1 == "system" {print $3 " " $4}'`: 

- This is an `awk` command that filters the output of the `who -b` command.
- It checks if the first field (`$1`) is "system", which would indicate a line showing the last boot time.
- If it is, it prints the third and fourth fields (`$3` and `$4`), separated by a space (the ********************bold text******************** in the example over). These fields typically contain the date and time of the last boot.

### 8. LVM

- A method of **allocating space on mass-storage devices** that is more flexible than conventional partitioning methods.

Shows like this:

```jsx
#LVM use: yes
```

> **Command: if [ $(lsblk | grep "lvm" | wc -l) -eq 0 ]; then echo no; else echo yes; fi**
> 

**What does the command do?**

- **if, then, else, fi** = Regular if [this is the case]; then <something>; else <something else>; fi (end of statement).
- `lsblk`: Lists information about all available or the specified block devices.

The “lsblk”-command would output this in itself:

```
NAME                        MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINTS
sda                           8:0    0   12G  0 disk  
├─sda1                        8:1    0  487M  0 part  /boot
├─sda2                        8:2    0    1K  0 part  
└─sda5                        8:5    0 11.5G  0 part  
  └─sda5_crypt              254:0    0 11.5G  0 crypt 
    ├─nholbroo42--vg-root   254:1    0  2.6G  0 lvm   /
    ├─nholbroo42--vg-var    254:2    0  1.2G  0 lvm   /var
    ├─nholbroo42--vg-swap_1 254:3    0  976M  0 lvm   [SWAP]
    ├─nholbroo42--vg-tmp    254:4    0  280M  0 lvm   /tmp
    └─nholbroo42--vg-home   254:5    0  6.6G  0 lvm   /home
sr0                          11:0    1 1024M  0 rom
```

- `grep "lvm"`: Filters the output of `lsblk` to only include lines that contain **"lvm".**
- `wc -l`: Counts the number of lines in the output from `grep`. This effectively counts the number of LVM volumes.

`if [ $(...) -eq 0 ]; then echo no; else echo yes; fi`: 

- This is an `if` statement that checks if the number of LVM volumes is equal to 0.
- If it is, it echoes "no", indicating that there are no LVM volumes.
- If it's not equal to 0, it echoes "yes", indicating that there are one or more 
LVM volumes.

### 9. Connections TCP

- TCP, or Transmission Control Protocol, is one of the **main protocols in the Internet protocol suite.**
- It's used to send data over the network in a reliable and ordered way.
- **A TCP connection is established between two endpoints (like your computer and a server) for the duration of their communication.** *It's like a phone call: you dial a number, someone on the other end picks up, and you start talking. When you're done, you hang up the connection.*
- In the context of the command I have written, an "established" TCP connection means that the **connection has been successfully made, and data can be sent back and forth.**

Shows like this:

```jsx
#Connections TCP: 2 ESTABLISHED
```

> **Command: ss -neopt state established | wc -l**
> 

**What does the command do?**

`ss -neopt state established`: 

- The `ss` command is used to dump socket statistics. It allows showing information similar to `netstat`.

<aside>
💡 **Netstat** is a command-line tool that **displays network connections** (both incoming and outgoing), **routing tables, and a number of network interface and network protocol statistics**. It is used for finding problems in the network and to determine the amount of traffic on the network as a performance measurement.

</aside>

- The `-n` option tells `ss` to **not resolve service names** (i.e., to show port numbers instead of names like 'http').
- The `-e` option shows detailed information, `-o` shows timer information, `-p` shows process using socket, and `state established` filters the output to only include established TCP connections.

The “ss -neopt state established”-command would output this in itself:

```
Recv-Q    Send-Q       Local Address:Port       Peer Address:Port    Process    
0         0                10.0.2.15:4242           10.0.2.2:60272    timer:(keepalive,52min,0) ino:14964 sk:1 cgroup:/system.slice/ssh.service <->
```

`wc -l`: This command counts the number of lines in the output from the `ss` command. This effectively counts the number of established TCP connections.

### 10. User log

- Shows the username of users currently logged in to the system.

Shows like this:

```jsx
#User log: 2
```

> **Command: users | wc -w**
> 

**What does the command do?**

- `users`: This is a command that prints the usernames of users currently logged in to the system.
- `wc -w`: This command counts the number of words in the output from the `users` command. In this context, each "word" is a username.

### 11. Network

- Shows the IP address and the MAC address of the system.

************IP-address:************

- “Internet protocol”
- **A unique identifier for a device on a network.**
- It's like the postal address for your computer, allowing it to send and receive data with other devices on the network.

There are two types of IP addresses: 

- **IPv4,** which are written as four sets of numbers separated by periods (e.g., 192.168.1.1)
- **IPv6**, which are written as eight groups of four hexadecimal digits, separated by colons (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

**MAC-address:**

- “Media Access Control”
- A unique identifier assigned to network interfaces for communications on the physical network segment.
- It's like a unique fingerprint for your device's network card that allows it to be identified when communicating over a network.
- It's typically represented as a series of six groups of two hexadecimal digits, separated by colons or hyphens, such as `00:11:22:AA:BB:CC`.

Shows like this:

```jsx
#Network: IP 10.0.2.15  (08:00:27:02:ee:f0)
```

> **Command 1: hostname -I** (IP-address)
> 

> **Command 2: ip link show | grep "ether" | awk '{print $2}’** (MAC-address)
> 

**What does the command do?**

******Command 1******

- The `hostname -I` command returns the IP address(es) associated with the current system. The `hostname` command without the `-I` -flag would only show the hostname (in my case nholbroo42).
- **It shows the IPv4 address.**

<aside>
💡 If I wanted to show the IPv6 address instead, I could simply add the `-i` -flag instead. Like this: `hostname -i`

</aside>

 ******Command 2******

- `ip link show`: Displays information about the network interfaces on the system.
- `grep "ether"`: Filters the output to only include lines containing the word "ether" (which typically indicates a MAC address).
- `awk '{print $2}'`: Prints the second field (separated by spaces) on each line. In this context, that's the MAC address.

### 12. Sudo

- Counts the number of times a command has been run with `sudo`.
- `sudo` = “Superuser do”.

Shows like this:

```jsx
#Sudo: 37 cmd
```

> **Command: journalctl _COMM=sudo | grep COMMAND | wc -l**
> 

**What does the command do?**

`journalctl _COMM=sudo`: 

- This command uses `journalctl`, a tool for querying and displaying logs from the systemd journal.
- The `_COMM=sudo` part is a filter that limits the output to entries where the COMM (command) field is `sudo`, i.e., entries related to the `sudo` command.

`grep COMMAND`: 

- Searches the output for lines containing the word "COMMAND".
- In the context of `sudo` logs, these lines typically represent instances where a command was run with `sudo`.

`wc -l`:

- This command counts the number of lines in the output from the previous command. In this context, each line represents an instance where a command was run with `sudo`.

### The final result!

The `wall` command in Unix-like systems is used to broadcast a message to all users logged into the system. 

The message to be broadcasted is provided as an argument to the `wall` command.

Like this: “**Broadcast message from nholbroo@nholbroo42 (pts/0) (Tue Jan  9 19:46:21 2024):”**

```jsx
#!/bin/bash
arc=$(uname -a)
pcpu=$(grep "physical id" /proc/cpuinfo | sort | uniq | wc -l)
vcpu=$(grep "^processor" /proc/cpuinfo | wc -l)
fram=$(free -m | awk '$1 == "Mem:" {print $2}')
uram=$(free -m | awk '$1 == "Mem:" {print $3}')
pram=$(free | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')
fdisk=$(df -BG | grep '^/dev/' | grep -v '/boot$' | awk '{ft += $2} END {print ft}')
udisk=$(df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} END {print ut}')
pdisk=$(df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{ut += $3} {ft+= $2} END {printf("%d"), ut/ft*100}')
cpul=$(top -bn1 | grep '^%Cpu' | cut -c 9- | xargs | awk '{printf("%.1f%%"), $1 + $3}')
lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')
lvmu=$(if [ $(lsblk | grep "lvm" | wc -l) -eq 0 ]; then echo no; else echo yes; fi)
ctcp=$(ss -neopt state established | wc -l)
ulog=$(users | wc -w)
ip=$(hostname -I)
mac=$(ip link show | grep "ether" | awk '{print $2}')
cmds=$(journalctl _COMM=sudo | grep COMMAND | wc -l)
wall "	#Architecture: $arc
#CPU physical: $pcpu
#vCPU: $vcpu
#Memory Usage: $uram/${fram}MB ($pram%)
#Disk Usage: ${udisk}MB/${fdisk}GB ($pdisk%)
#CPU load: $cpul
#Last boot: $lb
#LVM use: $lvmu
#Connections TCP: $ctcp ESTABLISHED
#User log: $ulog
#Network: IP $ip ($mac)
#Sudo: $cmds cmd"
```

## ✅****Chapter  5 - Evaluation:****

These are the commands used during the evaluation:

- `sha1sum Born2beroot.vdi`: Generates a fingerprint, meaning the current state of the virual machine. It should be identical to the one submitted to the project - to make sure it hasn’t been any changes since the project got submitted.
- `echo "some text" | diff - file.txt`: Compares the fingerprint from the git repo to the fingerprint generated by sha1sum.
- `whoami`: Prints the username of the current user.
- `sudo ufw status`: Checks the status of the Uncomplicated Firewall (UFW).
- `sudo systemctl status ssh`: Checks the status of the SSH service.
- `hostnamectl`: Shows the system hostname and other related information.
- `groups`: Shows the groups the current user is a part of.
- `sudo adduser new_user`: Creates a new user named "new_user".
- `su new_user`: Switches to the user "new_user".
- `chage -l new_user`: Shows password aging information for "new_user".
- `sudo groupadd evaluating`: Creates a new group named "evaluating".
- `sudo usermod -aG evaluating new_user`: Adds "new_user" to the group "evaluating".
- `sudo getent groupname`: Gets entries from Name Service Switch libraries, in this case for a group.
- `sudo hostnamectl set-hostname to “login42”`: Sets the system hostname to "login42".
- `lsblk`: Lists block devices.
- `sudo -V`: Prints the sudo version.
- `sudo ufw allow 8080`: Allows traffic on port 8080 through the firewall.
- `sudo ufw status numbered`: Shows the status of the firewall with rule numbers.
- `hostname -I` `hostname -i`: Shows IP addresses. (IPv4 and IPv6).
- `ssh new_user@127.0.1.1 -p 4243`: SSH into virtual machine as "new_user" on port 4243.
- `sudo crontab -u root -e`: Edits the crontab for the root user.
- `sudo systemctl list-units --type=service`: Lists all active service units.
- `sudo systemctl disable cron.service`: Disables the cron service.
- `sudo systemctl enable cron.service`: Enables the cron service.
- `sudo systemctl is_enabled cron.service`: Checks if the cron service is enabled.
- `sudo vim /etc/pam.d/common-password`: Opens the PAM password configuration file in the vim text editor.