# born2beroot
## Mandatory Part
### What is a Virtual Machine?
It is a virtual enviroment that works as a computer inside another computer.
Using software to simulate virtual hardware, we can run various operating systems inside one machine.

### What is the difference between Rocky/CentOS and Debian?
Rocky is considered to be a sucessor to CentOS anyways.

### Why choose one over another in this exercise?
I have choosen Debian. Setting up Rocky is quite complex. if you are new to system administration Debian is highly recommended. Or at least that's what the pdf says.

### What is the difference between aptitude and appt? (For Debian)
Package manager or package management system: A collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

aptitude: a text-based interface to the Debian GNU/Linux package system.
It allows the user to view the list of packages and to perform package management tasks such as installing, upgrading, and removing packages. Actions may be performed from a visual interface or from the command-line.

APT, on the other hand, lacks UI. This is because of the nature of apt-get as it is a low-level package manager and hence restricted to the command-line interface.

Aptitude is smarter and will automatically remove unused packages or suggest installation of dependent packages
Apt will only do explicitly what it is told to do in the command line
APT is lower level which can be used by other higher level package managers

### What is APPArmor?
 Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles
Linux security system that provides Mandatory Access Control (MAC) security. Allows the system admin to restrict the actions that processes can perform. It is included by default with Debian

You can aa-status to check if it is running.

### What are the advantages and diasadvantages of the password policy we implemented in this project?

### How do we view the partitions for this virtual machine?
 lsblk - list block devices
### What are the advantages of your password policy? What are the advantage and disadvantages of its implementation.

Your reason should be more than "The pdf told me to do it that way".

### What is LVM, how does it work?


### What is UFW? What is the value in using it?

### What is SSH?  What is the value in using it?

### Explain the operation of your script by displaying its code.

### What is cron?

