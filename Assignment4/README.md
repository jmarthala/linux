Assignment4

Name: Jahnavi Marthala

SJSU Id: 015351323

•	Set up the environment same as Assignment 2 and 3.

•	Reboot the test/inner VM.

•	Run ffd.sh bash script on inner VM once it comes up.

![image](https://user-images.githubusercontent.com/78889688/166092145-fe459333-282f-4b1d-abc1-b76f70c69f9b.png)

•	Execute dmesg on the outer VM to get the type of exit along with the count.

![image](https://user-images.githubusercontent.com/78889688/166092064-6779ccc3-27b9-4f35-913d-ce0f8b362f3c.png)

![image](https://user-images.githubusercontent.com/78889688/166092094-d16ab228-ed3d-46d7-b9b4-ad25c97a3f9f.png)

![image](https://user-images.githubusercontent.com/78889688/166092108-2b1cb5a5-b22d-4728-8f07-d3d854cd788f.png)

•	Shutdown the inner VM.

•	Remove 'kvm-intel' from the running kernel using "sudo rmmod kvm-intel"

•	From the outer VM, reload the kvm-intel module with ept=0 for disabling nested paging and forcing KVM to use shadow paging.

•	Execute "sudo insmod /lib/modules/5.18.0-rc3+/kernel/arch/x86/kvm/kvm-intel.ko ept=0"

![image](https://user-images.githubusercontent.com/78889688/166092130-02bffc97-29be-4e83-aa15-8c863d376430.png)

•	Boot up the inner/test VM.

• Execute ffd.sh bash script.	

![image](https://user-images.githubusercontent.com/78889688/166092145-fe459333-282f-4b1d-abc1-b76f70c69f9b.png)

•	Execute dmesg on the outer VM to get the type of exit along with the count.

![image](https://user-images.githubusercontent.com/78889688/166092161-3b27d842-bdf5-493c-a134-ceefcfcbf96a.png)

![image](https://user-images.githubusercontent.com/78889688/166092171-5d52dc2c-c839-4fe5-89fd-d24aa80ee42b.png)

![image](https://user-images.githubusercontent.com/78889688/166092175-3c4e378b-9259-485c-b8e6-dbcca062650b.png)

![image](https://user-images.githubusercontent.com/78889688/166092182-e0a58f93-d9cc-4fcc-b04b-d639170f7a13.png)


Output of shadow paging and nested paging are uploaded as files.

https://github.com/jmarthala/linux/blob/master/Assignment4/Shadowpaging.txt  - Without EPT

https://github.com/jmarthala/linux/blob/master/Assignment4/Nestedpaging.txt - With EPT


3. What did you learn from the count of exits? Was the count what you expected? If not, why not?

Exit count is more in shadow paging and less in nested paging. Yes, the count was expected due to the following reasons.

->There are two page tables in nested paging: a visitor page table and a host page table. In the TLB, there will be an additional file called TAG that will specify whether the item is for a host table or a guest table. When the hypervisor context switches inside the VM, there will be a field for PID that the hypervisor can refer to when it wants to clear the TLB for a specific VM process. With a nested page table, more memory locations (for instructions and their addresses) can be accessible in the 4-level page table, reducing the number of exits while increasing the number of memory accesses over shadow paging.

-> The VMM will manage the shadow page table if the VM switches from a nested page to a shadow page. CR3 points to the shadow page table of the hypervisor that needs to exit the #PF page fault in the shadow page. As a result, the VM will not be able to find the page in the guest page table, and the hypervisor will have to replicate the page. The shadow page table and TLB entries will also be filled. To address the memory release issue, we must also enable the TLB refresh exit function, which allows the shadow table to be synchronized and updated. As a result, shadow paging increases the number of exits, and its implementation is considered more difficult than nested paging.

4. What changed between the two runs (ept vs no-ept)?

Shadow paging has more exits compared to nested paging due to the overhead associated.







