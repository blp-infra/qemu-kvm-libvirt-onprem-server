# qemu-kvm-libvirt-onprem-server
this repo contain sample code to configure kvm and virtual server on ubuntu server as baremetal configuration

```
/ansible/
├── playbook.yml                    ← master playbook
├── inventory/
│   └── hosts.ini                   ← localhost
├── group_vars/
│   └── all.yml                     ← all variables
└── roles/
    ├── partition-disk/             ← one time, no destroy
    │   ├── tasks/main.yml
    │   ├── vars/main.yml
    │   └── templates/fstab.j2      ← fstab template
    │
    ├── bridge-network-create/      ← one time setup
    │   ├── tasks/main.yml
    │   └── vars/main.yml
    │
    ├── bridge-network-destroy/     ← rollback if needed
    │   └── tasks/main.yml
    │
    ├── kvm-install/                ← one time, no destroy
    │   └── tasks/main.yml
    │
    ├── vfio-setup/                 ← one time, needs reboot
    │   ├── tasks/main.yml
    │   └── vars/main.yml
    │
    ├── rhel-vm-create/             ← creates 3 VMs
    │   ├── tasks/main.yml
    │   └── vars/main.yml
    │
    └── rhel-vm-destroy/            ← destroys VMs cleanly
        └── tasks/main.yml
```
