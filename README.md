# server_setup_playbooks

A collection of playbooks to configure and manage servers for MyVM.Solutions

## Installation

```bash
python3 -m venv ./ansible_venv
source ansible_venv/bin/activate
pip install --upgrade pip
# pip install lxml setuptools # not sure if these are necessary on ansible server?
# pip install ansible-core==2.18.1 ansible  # try installing a specific version
pip install ansible-core ansible

ansible-galaxy collection install ansible.posix
```

The below requirements are needed on the host that executes this module (VMHOSTS, not ansible server)

    libselinux-python
    libsemanage-python
    python3-libsemanage

### In Rocky
sudo dnf install python3-libselinux.x86_64 python3-libsemanage.x86_64

### Ubuntu (added to selinux baseline role):
python3-semanage
python3-selinux

## Run plays

```bash
cd baseline_server/; time ansible-playbook run_play.yml -i inventory.yml -k -K  -T 15 && \
cd ../create_vm && time ansible-playbook run_play.yml -i inventory.yml -k -K  -T 15; \
cd /home/garrettj/code/server_setup_playbooks
```
