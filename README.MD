# ansible-f5-upload-install-os

I was asked to upgarde 40+ f5 devices in AWS, so i thought it would be best to automate the entire procoess using a simple ansible playbook. 

* Inventory list of all the f5s i needed to upgrade (active and standby) for the environment.

```
ansible-playbook -i inventory/hosts install-os.yaml
```

## install-os.yaml 

The playbook perfoms the following actions:
* saves the existing configurations
* uploads the latest OS
* installs it on a new partition
* copies the exiting configuration to the new parition and reboots the device
* prints out an output of when its complete

Note: 
* I tried to use the bigip_command to execute the cpcfg command but it only works for TMSH commands not CLI/BASH commands.
* if you dont want the device to boot just remove the following.

```
    - name: Copy the config from HD1.1 to HD1.2 cpcfg --source=HD1.1 --reboot HD1.2    
      raw: curl -u "{{ansible_user}}":"{{ansible_ssh_pass}}" -k https://"{{ansible_host}}":8443/mgmt/tm/util/bash  -H "Content-type:application/json" -d "{\"command\":\"run\",\"utilCmdArgs\":\"-c 'cpcfg --source=HD1.1 --reboot HD1.2'\"}"
      ignore_errors: True
      register: cpcfg
```


## How to use the playbook.
I am sure i will continue to edit this to make it better and learn as I go.. for F5 VEs and physical devices this is the cpfcg command

cpcfg --source=HD1.1 --reboot HD1.3

On a VIPRION system, ensure each blade receives the updated configuration by running the cpcfg command with the clsh utility on the primary blade.

For example:

clsh cpcfg --source=HD1.1 --reboot HD1.3

** Tested in VMware vsphere 6.7 = all good! 
** Tested in AWS
** Tested in GCP
** Tested in Azure
