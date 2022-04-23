Implementation details:

Building the kernel:

Following steps are followed to build the kernel

•	Nested virtualization is enabled while spinning up VM and environment is setup same as assignment 1 with 8GB RAM and 60 GB memory.
1.	We followed the insructions given in the Assignment pdf to build kernel.
2.	Copy kernel config from boot to linux folder with version same as OS version
3.	Install essential dependencies like bison, libssl-dev, libelf-dev, flex using sudo apt install
4.	Disable SYSTEM_TRUSTED_KEYS and SYSTEM_REVOCATION_KEYS to eliminate error with pem file
5.	As there are 2 core execute “make -j 2 modules”
6.	Execute make -j 2
7.	Execute make INSTALL_MOD_STRIP=1 modules_install && make install. This reduces debug info size
8.	Sudo reboot
9.	Above steps sets up the kernel.
10.	Change the files cupid.c and vmx.c. Updated the code for both CPUID leaf node %eax=0x4FFFFFFF and leaf node %eax=0x4FFFFFFE to get number of exits and total time to handle the exits.
11.	Execute the following commands 
•	sudo rmmod kvm-intel
•	sudo rmmod kvm
•	modprobe kvm
•	modprobe kvm-intel

![image](https://user-images.githubusercontent.com/78889688/164883343-53ac6de6-3f50-4397-95be-320aaf50dd33.png)


 

•	 Create the virtual machine inside the VM using the commands below.

•	sudo apt update

•	sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils

•	sudo systemctl status libvirtd

•	sudo systemctl enable --now libvirtd

•	sudo apt install virt-manager

•	sudo virt-manager


![virt](https://user-images.githubusercontent.com/78889688/164883673-1b14fedc-72ca-4ad0-8365-7b9b56b01a00.png)

Spin up new VM
![vm](https://user-images.githubusercontent.com/78889688/164883936-276eb656-e027-4d41-95bc-7e16ce48e90d.png)
 

Install CPUID using “sudo apt install cpuid”. And in the inner VM execute the following command. 

Also in the /etc/apt/sources.list file add 'deb http://mirrors.kernel.org/ubuntu bionic main universe'.

cpuid -l 0X4fffffff -s exit_number cpuid -l 0X4ffffffe -s exit_number




![cpu](https://user-images.githubusercontent.com/78889688/164883716-054ba9cd-6978-44a0-950b-240c63149c90.png)


