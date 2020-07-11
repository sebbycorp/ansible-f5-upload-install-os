# ansible-f5-upload-install-os
The following is a quick playbook that uploads and installs F5 .ISO to your device and starts installing it on a new partition

I had to upgrade about 40+ devices this week, so i spun up a quick playbook to do the upload and install for me. 

Note: To a


State string Choices:
* activated
* installed

When installed, ensures that the software is installed on the volume and the volume is set to be booted from. The device is not rebooted into the new software.
When activated, performs the same operation as installed, but the system is rebooted to the new software.
