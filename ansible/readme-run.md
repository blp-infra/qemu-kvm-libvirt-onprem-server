# Dry run first - see what will happen
ansible-playbook -i inventory/hosts.ini playbook.yml --check

# Real run
ansible-playbook -i inventory/hosts.ini playbook.yml

# dry run single role
ansible-playbook -i inventory/hosts.ini playbook.yml --tags partition-disk --check

# real run single role
ansible-playbook -i inventory/hosts.ini playbook.yml --tags partition-disk

ansible-playbook -i inventory/hosts.ini playbook.yml --tags partition-disk --check --ask-become-pass


#We feed it commands via echo piped into fdisk like this concept:
```
echo -e "n\np\n1\n\n+500G\nn\np\n2\n\n\nw" | sudo fdisk /dev/sda
But before writing — let me explain what those keystrokes mean so you understand the role completely:
n   → new partition
p   → primary
1   → partition number 1
    → default start sector (enter)
+500G → size 500GB

n   → new partition
p   → primary  
2   → partition number 2
    → default start (enter)
    → default end = rest of disk (enter)

w   → write and exit
```
