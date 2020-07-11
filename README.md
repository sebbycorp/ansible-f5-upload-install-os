# ansible-f5-upload-install-os

I was asked to upgarde 40+ f5 devices in AWS, so i thought it would be best to automate the entire procoess using a simple ansible playbook. 

* Inventory list of all the f5s i needed to upgrade (active and standby) .. because we need the code on all the versions.

The playbook perfoms the following actions
* saves the existing configurations
* uploads the latest OS
* installs it on a new partition
* prints out an output of when its complete

# There are you yaml files:
** install-os.yaml
* uploads, installs and verifies the install

