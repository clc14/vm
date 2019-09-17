# vm
Blank VMware Workstation/Player files to create CentOS 7 VMs for RHCSA/RHCE practice

Instructions for use:

* Download and install VMware Workstation or Player
* Download vms.zip
* Extract vms.zip
* Go into the ELLIS folder
* Double-click on the .vmx file
* Edit the virtual machine settings, and for the first CD/DVD device, select use Image ISO file
   * click Browse, and choose the CentOS-7-x86_64-DVD-1804.iso you downloaded
   * If necessary, you can increase the memory for the VM. Make sure it is at least 4GB. If you are going to run the 3 VMs concurrently, it should be at least 6GB.
* (OPTIONAL) When the machine boots and the Install CentOS 7 menu comes up, press tab
   * After "quiet" at the end of the line, go to Edit->Paste and copy/paste ks=https://raw.githubusercontent.com/clc14/vm/master/ellis.cfg.txt then press enter to install CentOS automatically or install manually.

    * The DVD is mounted on /var/www/html/repo. If you want to copy the DVD locally instead, then unmount it with umount /var/www/html/repo; remove the line from /etc/fstab. Refer to https://github.com/sdoconnell/ELLIS#setup-and-installation to copy the files from the DVD to /var/www/html/repo. You can create different VM versions like Red Hat 7.0 by choosing the ISO in VMware and mounting the ISO to /var/www/html/repo in Linux.

* Type cd to go back to /root. 
* Running ./mkserver0.sh will create the first VM; ./mkserver1.sh will create the 2nd and ./mkserver2.sh will create the 3rd.

To delete the VMs you created, type virsh destroy server0; virsh undefine server0; rm -f /var/lib/libvirt/images/server0.qcow2 in server0, 1, 2.
