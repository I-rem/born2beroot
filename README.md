# born2beroot evaluation
## General Instructions
- During the defense, as soon as you need help to verify a point, the student evaluated must help you.

- Ensure that the "signature.txt" file is present at the root of the cloned repository.

- Check that the signature contained in "signature.txt" is identical
to that of the ".vdi" file of the virtual machine to be evaluated. A simple ask the student being evaluated where their ".vdi" file is located.
- As a precaution, you can duplicate the initial virtual machine in order to keep a copy. (Copying seems to change the signature for me I need to figure this out)
- Start the virtual machine to be evaluated.
- If something doesn't work as expected or the two signatures differ,
the evaluation stops here.
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
Rocky is considered to be a sucessor to CentOS anyways.

#### Why choose one over another in this exercise?
I have choosen Debian. Setting up Rocky is quite complex. if you are new to system administration Debian is highly recommended. Or at least that's what the pdf says.

#### What is the difference between aptitude and appt? (For Debian)
Package manager or package management system: A collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

**aptitude:** a text-based interface to the Debian GNU/Linux package system.
It allows the user to view the list of packages and to perform package management tasks such as installing, upgrading, and removing packages. Actions may be performed from a visual interface or from the command-line.

**APT**, on the other hand, lacks UI. This is because of the nature of apt-get as it is a low-level package manager and hence restricted to the command-line interface.

Aptitude is smarter and will automatically remove unused packages or suggest installation of dependent packages
Apt will only do explicitly what it is told to do in the command line
APT is lower level which can be used by other higher level package managers

#### What is APPArmor?
 Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles
Linux security system that provides Mandatory Access Control (MAC) security. Allows the system admin to restrict the actions that processes can perform. It is included by default with Debian

You can use **aa-status** to check if it is running.

### Simple Setup
- Ensure that the machine does not have a graphical environment at launch.
- A password will be requested before attempting to connect to this machine.
- Finally, connect with a user with the help of the student evaluated.
- This user must not be root.
- Pay attention to the password chosen, it must follow the rules imposed in the subject.

*If your password does not follow the rules you can change it with the passwd command*
 
 **passwd [options] [LOGIN]:** The passwd command changes passwords for user accounts. A normal user may only change the password for their own account, while the superuser may change the password for any account.

`$sudo passwd` will ask you to authenticate yourself with your current user but ***root***'s password will be the one being changed.
`$sudo passwd user1` will change user1's password rather than your own or root's.
`$passwd' will simply change the current user's password 

- Check that the UFW service is started with the help of the evaluator.

`$sudo ufw status` or `$systemctl status ufw`
- Check that the SSH service is started with the help of the evaluator.

`$systemctl status ssh` or `$ssh` or `$sudo service ssh status`
- Check that the chosen operating system is Debian or Centos with the help of the reviewer.

`$hostnamectl` or `$cat /etc/os-relase`
#### What are the advantages and diasadvantages of the password policy we implemented in this project?

#### How do we view the partitions for this virtual machine?
 lsblk - list block devices
#### What are the advantages of your password policy? What are the advantage and disadvantages of its implementation.

Your reason should be more than "The pdf told me to do it that way".

#### What is LVM, how does it work?


#### What is UFW? What is the value in using it?

#### What is SSH?  What is the value in using it?

#### Explain the operation of your script by displaying its code.

#### What is cron?

