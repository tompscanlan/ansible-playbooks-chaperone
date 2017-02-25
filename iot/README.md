# IoT plays

## initial setup

```
sshkeygen
ansible-playbook --ask-pass -i /mnt/inventory/  sshkeys.yaml

# to also copy ssh keys from github account:
ansible-playbook --ask-pass -i /mnt/inventory/  sshkeys.yaml -e 'github_userid=tompscanlan'

# download photon ova and install it as a template in vcenter
ansible-playbook -i /mnt/inventory/  vm_template_prep.yml --vault-password-file .vault_pass.txt

# After updating the template to have a known password,
# run this to clone copies for setup
ansible-playbook -i /mnt/inventory/  new_vsphere_vms_from_template.yml  --vault-password-file .vault_pass.txt

# populate the new vm IPs in /etc/hosts
# re-run the sshkeys play to push keys out to the new VMs
ansible-playbook --ask-pass -i /mnt/inventory/  sshkeys.yaml
```
