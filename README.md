
# PanOS Deployment using Ansible and Bootstrapper

This is an example playbook that shows how to use the PanOS bootstrapper
utility along with Ansible to deploy a VM Series Firewall in KVM. 

## Setup

This playbook depends on the [PanOS Bootstrapper Utility](https://github.com/PaloAltoNetworks/panos-bootstrapper)
\>= v0.5. There is no special configuration necessary for this playbook to run. 

Edit the group_vars/all file to reflect your environment. 

## Running

Example output below:
```bash
vistoq@vistoq:~/provision-pan$ ansible-playbook -i inventory/ provision-pan-vm.yaml

PLAY [kvm] ***********************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************************************************************************
ok: [localhost]

TASK [provision-pan-vm : include_tasks] ******************************************************************************************************************************************************************************
included: /home/vistoq/provision-pan/roles/provision-pan-vm/tasks/generate_bootstrap.yaml for localhost

TASK [provision-pan-vm : Generate Bootstrap ISO] *********************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Set permissions on Bootstrap ISO] ***********************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : include_tasks] ******************************************************************************************************************************************************************************
included: /home/vistoq/provision-pan/roles/provision-pan-vm/tasks/launch_pan_vm.yaml for localhost

TASK [provision-pan-vm : Removing stale instance file] ***************************************************************************************************************************************************************
ok: [localhost]

TASK [provision-pan-vm : Create backing file for VM Image] ***********************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Define KVM VM] ******************************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Start KVM VM] *******************************************************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ***********************************************************************************************************************************************************************************************************
localhost                  : ok=9    changed=5    unreachable=0    failed=0

vistoq@vistoq:~/provision-pan$
```
