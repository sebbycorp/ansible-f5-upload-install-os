# ansible-f5-upload-install-os

I was asked to upgarde 40+ f5 devices in AWS, so i thought it would be best to automate the entire procoess using a simple ansible playbook. 

* Inventory list of all the f5s i needed to upgrade (active and standby) .. because we need the code on all the versions.

The playbook perfoms the following actions
* saves the existing configurations
* uploads the latest OS
* installs it on a new partition
* prints out an output of when its complete

Note: You can change the state to. what best suites yours requirements. 

State string Choices:
* activated
* installed

When installed, ensures that the software is installed on the volume and the volume is set to be booted from. The device is not rebooted into the new software.
When activated, performs the same operation as installed, but the system is rebooted to the new software.
