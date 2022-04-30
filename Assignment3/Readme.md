
Assignment3 Documentation:

Name: Jahnavi Marthala

SJSU Id: 015351323


Implementation:

•	Set up the environment same as Assignment 2

•	Make changes to cpuid.c and vmx.c files.

•	Changes to cpuid.c gives higher 32 and lower 32 bits of exit processing time in ebx and ecx respectively.

•	Changes to vmx.c gives total time spent in processing of exit number and number of exits.

•	Execute the commands below.

make -j 2 modules

make -j 2

sudo make INSTALL_MOD_STRIP=1 modules_install

sudo make install

sudo rmmod kvm-intel

sudo rmmod kvm

modprobe kvm

modprobe kvm-intel

sudo apt update

sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils

sudo systemctl status libvirtd

sudo systemctl enable --now libvirtd

sudo apt install virt-manager

sudo virt-manager

•	Install ubuntu 20.4 version in inner VM. 

 ![image](https://user-images.githubusercontent.com/78889688/166085194-56263f1a-f183-4b77-852a-591eef18e56a.png)
 

•	Edit /etc/apt/sources.list file to add “deb http://mirrors.kernel.org/ubuntu bionic main universe”.

•	Execute the below commands.

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 9578539176BAFBC6

apt-key list

sudo apt-get -y update

sudo apt-get install cupid

•	Created 2 shell scripts ffd.sh and ffc.sh

![image](https://user-images.githubusercontent.com/78889688/166085211-7ca9c7c2-6aad-473f-8cfe-3f3403e8c07d.png)
 
•	 Execute the shell scripts to get the output below.

ffd.sh output:

 
![image](https://user-images.githubusercontent.com/78889688/166085226-11c03824-d314-4241-9125-0b15d59ee09f.png)

![image](https://user-images.githubusercontent.com/78889688/166085232-09bd7b43-b300-4e47-854f-6872eb55129d.png)
 

ffc.sh output:
 
![image](https://user-images.githubusercontent.com/78889688/166085247-1d5c03ba-7407-41a2-abe1-f4875cba9f41.png)

![image](https://user-images.githubusercontent.com/78889688/166085251-3a292c24-4d74-4887-aad6-1cfdc37e7b87.png)
 

•	Execute “dmesg” in outer Ubuntu VM

Dmesg output for 0x4FFFFFFD
 

![image](https://user-images.githubusercontent.com/78889688/166085266-3bdb5268-9ebd-499f-b378-3b66610fc5ad.png)

![image](https://user-images.githubusercontent.com/78889688/166085271-6dce4508-60ac-43b8-96ff-853027bf48d0.png)

![image](https://user-images.githubusercontent.com/78889688/166085275-cdefe509-1743-4eb7-bd1f-3e2079c64a60.png)

![image](https://user-images.githubusercontent.com/78889688/166085282-46ef825a-9084-4104-bdc8-7a1b9449106c.png)



Dmesg output for 0x4FFFFFFC
 
![image](https://user-images.githubusercontent.com/78889688/166085303-02fd2c3e-82ef-4622-abc5-b2fdd5e32774.png)

![image](https://user-images.githubusercontent.com/78889688/166085309-aacee30e-0344-44fe-943b-928e434f415b.png)

![image](https://user-images.githubusercontent.com/78889688/166085315-7bcc5e80-49a0-425b-abd3-08d05cc467e3.png)

![image](https://user-images.githubusercontent.com/78889688/166085318-732d039e-b956-4b8a-8792-6fc8d2ab5d99.png)

![image](https://user-images.githubusercontent.com/78889688/166085322-0a28c58a-abe3-4075-b481-e8a58fdd506c.png)

![image](https://user-images.githubusercontent.com/78889688/166085328-bae9d403-5947-421c-b267-a624b34ac3ac.png)

![image](https://user-images.githubusercontent.com/78889688/166085332-d2bfad93-f775-4aa1-9ec2-48c5ed90bec9.png)

 



3. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there 
more exits performed during certain VM operations? Approximately how many exits does a full VM 
boot entail?

Number of exits does not increase at a stable rate. It changes based on VM operations. Operations like External Interrrupt, I/O instruction etc will cause more exits. A full VM boot entails around a maximum of 5682048 exits.

![WhatsApp Image 2022-04-29 at 6 56 37 PM](https://user-images.githubusercontent.com/78889688/166086188-ee08dd7b-7038-4a64-938d-8fc0287ecee8.jpeg)


4. Of the exit types defined in the SDM, which are the most frequent? Least?

More frequent exit types are listed below according to their order:

• Exit number 48 - EPT Violation

• Exit number 32 - WRMSR

• Exit number 1- External Interrupt

• Exit number 10- CPUID

• Exit number 12- HLT


Least recorded frequent exit types are

• Exit number 29 - MOV DR

Apart from this there are many exits with 0 count.



 



 

 

 


