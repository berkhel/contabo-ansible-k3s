# Deploy K3S on top of Docker Swarm with Ansible

## On WSL
```
"[WARNING]: Ansible is being run in a world writable directory (/mnt/c/Users/.../.../ansible-deploy-factory/k3s-swarm), ignoring it as an ansible.cfg source."
```
To make Ansible use correctly ansible.cfg
```bash
export ANSIBLE_CONFIG=./ansible.cfg
```

## How to run
```bash
ansible-playbook -i inventory.yml playbook.yml
```

### Only clean
```bash
ansible-playbook -i inventory.yml playbook.yml --tags=clean
```
### Only deploy
```bash
ansible-playbook -i inventory.yml playbook.yml --tags=deploy
```

### Rebuild only K3S cluster
```bash
ansible-playbook -i inventory.yml playbook.yml --tags=k3s
```

### Delete K3S cluster
```bash
ansible-playbook -i inventory.yml playbook.yml --tags=k3s --skip-tags=deploy
```

### Enable "debug" tagged tasks execution
On ansible.cfg, comment the last line "skip=debug" 