Assignment 1
Name: Jahnavi Marthala
SJSU Id: 015351323

![image](https://user-images.githubusercontent.com/78889688/164864547-0d0d25c1-8506-4382-a202-f12b60232ded.png)

Aim:
The aim of this assignment is to create a Linux kernel module that queries various MSRs to determine virtualization features available in CPU. The module reports the features it discovers. Following things needs to be developed.
•	Configure a Linux machine, either VM based or on real hardware. You may use any Linux distribution you wish.
•	Download and build the Linux kernel source code
•	Create a new kernel module with the assignment functionality
•	Load (insert) the new module
•	Verify proper output in the system message log.
Functionalities:
•	Read the VMX configuration MSRs to ascertain support capabilities/features
•	Entry / Exit / Procbased / Secondary Procbased / Pinbased controls
•	For each group of controls above, interpret and output the values read from the MSR to the system
•	via printk(..), including if the value can be set or cleared.
    
Implementation details:
•	Install VMware Workstation on the Windows 11 machine.
•	Downloaded the Operating system image of the Ubuntu 22.04 LTS Desktop version.
•	Spin up a new virtual machine with below settings of Ubuntu OS in VMware Workstation.
•	Device configurations are 8GB RAM, 50GB memory, dual core CPU with nested virtualization.
Hardware Settings:
 

Options:
 

•	Once all the configurations are don, click on finish to load the OS and spin up the virtual machine.
•	Execute “cat /proc/cpuinfo” to understand if nested virtualization is enabled.
 
•	Fork the Linux github repository of Torvald.
https://github.com/torvalds/linux
•	Clone the github repository in the Ubuntu VM and install GIT if not present using “sudo apt install git”
•	To disable characters on pressing arrows, go to vimrc file and add “set nocompatible”.
•	Upload cmpe283-1.c and Makefile from the canvas to VM.
•	Add “MODULE_LICENSE("GPL v2");” at the end of cmpe283-1.c file to eliminate error with respect to license.
•	Execute “sudo apt install make” to install make.
•	Execute “sudo apt install gcc” to install make.
•	Execute make.
 

•	Execute insmod of cmpe283-1.ko file and execute lsmod to check if kernel module is loaded.
 

•	Execute dmesg to get the system log of pin based control
 

•	Exit the module using “sudo rmmod cmpe283-1”
 

•	SDM is referred and structs are created with name and bit positions for entry, exit, procbased and secondary procbased controls.
•	report_capability() is called with necessary parameters to print the controls.
•	 In order to determine if true controls are available, a new function has been written to check the 55th bit of IA32_VMX_BASIC MSR. If this bit is set, then true controls are available and another function will be called to print the corresponding true VMX capabilities.
•	In order to determine if Secondary Procbased controls are available, , a new function has been written to check 63rd bit of IA32_VMX_PROCBASED MSR. If this bit is set, then secondary procbased controls are available and another function will be called to print the corresponding secondary procbased capabilities.
•	After making necessary changes run make again.
•	Load the kernel using sudo insmod cmpe283-1.ko.
•	Execute dmesg
IA32_VMX_PINBASED_CTLS

 

IA32_VMX_PROCBASED_CTLS
 

IA32_VMX_PROCBASED_CTLS2
 

IA32_VMX_EXIT_CTLS
 


IA32_VMX_ENTRY_CTLS
 






•	Exit the module using “sudo rmmod cmpe283-1”

