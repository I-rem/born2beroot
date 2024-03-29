# born2beroot evaluation (mandatory part)
## General Instructions
- During the defense, as soon as you need help to verify a point, the student evaluated must help you.

- Ensure that the "signature.txt" file is present at the root of the cloned repository.

- Check that the signature contained in "signature.txt" is identical
to that of the ".vdi" file of the virtual machine to be evaluated. A simple ask the student being evaluated where their ".vdi" file is located.
- As a precaution, you can duplicate the initial virtual machine in order to keep a copy.
- Start the virtual machine to be evaluated.
- If something doesn't work as expected or the two signatures different, the evaluation stops here. (This happened at my first defence :'D )
## Mandatory Part
### Project Overview
- The student evaluated should simply explain to you:
- The basic functioning of its virtual machine.
- His choice of operating system.
- The basic differences between Centos and Debian.
- The interest of virtual machines.
- If the evaluated student has chosen Debien he will need to explain the difference between aptitude and apt and what APPArmor is. 
- During the defense, a script must display information all every 5 minutes. Its operation will be checked in detail later. 
- If the explanations are not clear, the evaluation stops here.

#### What is a Virtual Machine?
It is a virtual enviroment that works as a computer inside another computer.
Using software to simulate virtual hardware, we can run various operating systems inside one machine.

#### What is the difference between Rocky/CentOS and Debian?
Rocky is considered to be a sucessor to CentOS. Debian has more packages and new versions are relased quite often. It has a friendly desktop GUI. CentOS on the other hand is usually the choice of enterprises due to its stability. It has a longer developmental cycle and it can be quite hard to upgrade from one version to another.

#### Why choose one over another in this exercise?
I have choosen Debian. Setting up Rocky is quite complex. if you are new to system administration Debian is highly recommended. Or at least that's what the sıbject pdf says. Also I have used Ubuntu (which is based on Debian) before. So it shold be easier and more familiar this way. 

#### What is the difference between aptitude and appt? (For Debian)
**Package manager or package management system:** A collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

**aptitude:** a text-based interface to the Debian GNU/Linux package system.
It allows the user to view the list of packages and to perform package management tasks such as installing, upgrading, and removing packages. Actions may be performed from a visual interface or from the command-line.

**APT(Advanced Package Tool)**, on the other hand, lacks UI. This is because of the nature of apt-get as it is a low-level package manager and hence restricted to the command-line interface.

Aptitude is smarter and will automatically remove unused packages or suggest installation of dependent packages
Apt will only do explicitly what it is told to do in the command line
APT is lower level which can be used by other higher level package managers

#### What is APPArmor?
 Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles
Linux security system that provides Mandatory Access Control (MAC) security. Allows the system admin to restrict the actions that processes can perform. It is included by default with Debian

You can use `$aa-status` to check if it is running.

### Simple Setup
- Ensure that the machine does not have a graphical environment at launch.
- A password will be requested before attempting to connect to this machine.
- Finally, connect with a user with the help of the student evaluated.
- This user must not be root.
- Pay attention to the password chosen, it must follow the rules imposed in the subject.

*If your password does not follow the rules you can change it with the passwd command:*
 
 **passwd [options] [LOGIN]:** The passwd command changes passwords for user accounts. A normal user may only change the password for their own account, while the superuser may change the password for any account.

`$sudo passwd` will ask you to authenticate yourself with your current user but ***root***'s password will be the one being changed.

`$sudo passwd user1` will change user1's password rather than your own or root's.

`$passwd` will simply change the current user's password 

Then you can change the maxday/minday/warnday settings of your user account and you root account

`sudo chage --maxdays 30 your_username`

`sudo chage --mindays 2 your_username`

`sudo chage --warndays 7 your_username`

- Check that the UFW service is started with the help of the evaluator.

`$sudo ufw status` or `$systemctl status ufw`

- Check that the SSH service is started with the help of the evaluator.

`$systemctl status ssh` or `$ssh` (Will show a helpful cheatsheet is ssh is installed) or `$sudo service ssh status`

- Check that the chosen operating system is Debian or Centos with the help of the reviewer.

`$hostnamectl` or `$cat /etc/os-relase`

### User
The subject requests that a user with the login of the evaluated student is present on the virtual machine. Check that it has been added and that it belongs to the "sudo" and "user42" groups.

`$id your_login` or `getent group sudo user42` or `$groups`

Make sure the rules imposed in the subject concerning the password policy have been put in place by following the following steps.
- First, create a new user. Assign it a password of your choice, respecting the subject rules. 

`$useradd user_name` to add the user

`$chage -l user_name` to check if certain password rules are imposed to the user

- The evaluated student must now explain to you how he was able to set up the rules requested in the subject on their virtual machine. Normally there should be one or two modified files

`$cat /etc/pam.d/common-password`
`$cat /etc/login.def`

if you forget where these files are located you can check the man page for `login`and `passwd`

- Ask the student being evaluated to create a group named "evaluating" in front of you and assign it to this user. Finally, check that this user belongs to the "evaluating" group.

- Ask the student evaluated to explain the advantages of this password policy, as well as the advantages and disadvantages of its implementation.

We are forcing the users to use complicated passwords that will be hard to crack which is an obvious advantage. However when people have to change passwords constantly it becomes hard to remember so they generally choose to write down their passwords somewhere or use the same/similar passwords for every account they have both of which create security risks.

### Hostname and partitions
- Check that the hostname of the machine is correctly formatted as follows: login42 (login of the student evaluated).

`$hostnamectl`

- Modify this hostname by replacing the login with yours, then restart the machine.

`$sudo hostnamectl set-hostname new_hostname`

`$sudo reboot`

If on restart, the hostname has not been updated, the evaluation stops here.
- You can now restore the machine to the original hostname.

`$sudo hostnamectl set-hostname old_hostname`

- Ask the student evaluated how to view the partitions for this virtual machine.

`$lsblk` list block devices
- Compare the output with the example given in the subject. Please note: if the student evaluated makes the bonuses, it will be necessary to refer to the bonus example.

This part is an opportunity to discuss the scores! The student being evaluated should give you a brief explanation of how LVM works and what it is all about.
#### What Is LVM? (Logical volume management)

### SUDO
- Check that the "sudo" program is properly installed on the virtual machine.

- The evaluated student should now show assigning your new user to the "sudo" group.

`$usermod -aG sudo user_name` or `$sudo adduser user_name sudo`
- The subject imposes strict rules for sudo. The evaluated student must first explain the value and operation of sudo using examples of their choice.
In a second step, it must show you the implementation of the rules imposed by the subject.
- Verify that the "/var/log/sudo/" folder exists and has at least one file. Check the contents
of the files in this folder, You should see a history of the commands used with sudo. Finally, try to run a command via sudo.
### UFW
- Check that the "UFW" program is properly installed on the virtual machine.

- Check that it is working properly.

`sudo ufw status`
- The evaluated student being evaluated should explain to you basically what UFW is and the value of using it.
#### What is UFW (Uncomplicated Firewall)?

- List the active rules in UFW. A rule must exist for port 4242.

- Add a new rule to open port 8080. Check that this one has been added by listing the active rules.

`$ufw allow 8080`
`$ufw status`

- Finally, delete this new rule with the help of the student evaluated.

`$ufw status numbered`

`$ufw delete rule_number`

### SSH
- Check that the SSH service is properly installed on the virtual machine.
- Check that it is working properly.
- Verify that the SSH service only uses port 4242.

`$sudo service ssh status`

We can also show the modifications we made to the ssh configuration files at this point

`$vim /etc/ssh/ssh_config`
`$vim /etc/ssh/sshd_config`

- The evaluated student must be able to explain to you basically what SSH is and the value of using it.
#### What is SSH?
SSH or Secure Shell is an authentication mechanism between a client and a host. It uses encryption techniques so that all communication between clients and hosts is done in encrypted form

Its most notable applications are remote login and command-line execution.

It is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.

- The student evaluated should help you use SSH in order to log in with the newly created user.
To do this, you can use a key or a simple password. It will depend on the student being evaluated.
Of course, you have to make sure that you cannot use SSH with the "root" user as stated in the subject.

`$ssh your_username@127.0.0.1 -p 4242`

`$ssh root@127.0.0.1 -p 4242`

### Script monitoring
The student evaluated should explain to you simply :

- The operation of its script by displaying its code.

`$vim /usr/local/bin monitoring.sh`

`#!/bin/bash
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
	#Disk Usage: $udisk/${fdisk}Gb ($pdisk%)
	#CPU load: $cpul
	#Last boot: $lb
	#LVM use: $lvmu
	#Connections TCP: $ctcp ESTABLISHED
	#User log: $ulog
	#Network: IP $ip ($mac)
	#Sudo: $cmds cmd"
`

Uses the `uname` command to retrieve **system architecture information** and stores it in the `$arc` variable.

Uses the `grep`, `sort`, `uniq`, and `wc` commands to **count the number of physical CPUs** on the system and stores it in the `$pcpu` variable.

Uses the `grep` and `wc` commands to **count the number of virtual CPUs** on the system and stores it in the `$vcpu` variable.

Uses the `free` command to retrieve the **total amount of memory ($fram)** and the ,amount of **used memory ($uram)**. It also calculates the **percentage of memory usage ($pram)** and stores it in the variable.
Uses the `df` command to retrieve **disk usage information**, such as the **total disk space ($fdisk)**, **used disk space ($udisk)**, and the **percentage of disk usage ($pdisk)**.

Uses the `top` command to retrieve **CPU load information** and stores it in the `$cpul` variable.

Uses the `who` command to retrieve the system's **last boot time** and stores it in the `$lb` variable.

Uses the `lsblk` command to check **if the system is using LVM (Logical Volume Manager)** and stores it in the `$lvmu` variable.

Uses the `ss` command to **count the number of established TCP connections** and stores it in the `$ctcp` variable.

Uses the `users` command to **count the number of logged-in users** and stores it in the `$ulog` variable.

Uses the `hostname` and `ip` commands to retrieve the **system's IP address ($ip)** and the `ip` command to retrieve the **MAC address ($mac)**.

Uses the `journalctl` command to **count the number of sudo commands executed** and stores it in the `$cmds` variable.
Finally, the wall command is used to display all of the information gathered above on the console.

#### What is Cron?
Cron a command line utility to schedule commands or scripts to happen at specific intervals or a specific time each day. 
- How the evaluated student set up her script so that it runs every 10 minutes when the server starts up.

`$sudo crontab -l`

Once the correct functioning of the script has been verified, the student evaluated should ensure that this script runs every 30s. You can run whatever you want to make sure the script runs with dynamic values correctly, 

`$sudo crontab -e`

and the student evaluated should make the script stop running when the server starts up, but without modifying the script. in himself. To check this point, you will have to restart the server one last time.

`$sudo systemctl disable cron` The script will not stop immediately. We need to reboot first.

`$sudo reboot`

At startup, it will be necessary to check that the script still exists in the same place, that its rights have remained unchanged, and that it has not been modified.
