# What is Ansible?

Ansible is a configuration management and orchestration tool. It works as an IT automation engine.

Ansible can be run directly from the command line without setting up any configuration files. You only need to install Ansible on the control server or node. It communicates and performs the required tasks using SSH. No other installation is required. This is different from other orchestration tools like Chef and Puppet where you have to install software both on the control and client nodes.

Ansible uses configuration files called playbooks for a series of tasks. The playbooks are written in YAML syntax.

# Install
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-with-pip

```$ pip install ansible```

# Example: CMD Line 
```
$ ansible --version
$ ansible --help
$ ansible -m ping localhost
localhost | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
$ ansible -m command -a "ls" localhost
localhost | CHANGED | rc=0 >>
README.md
```

# Example Playbook
- Ansible command line is great for executing a single task. But in playbooks are more useful for multiple tasks. Playbooks are text files written in the YAML format. Let’s take our list example above and create a playbook.
```
$ ansibe-playbook example-playbook.yaml
PLAY [example-playbook.yaml] ***********************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************
ok: [localhost]

TASK [pwd] *****************************************************************************************************************************************************************************************************************************
changed: [localhost]

TASK [list files in folder] ************************************************************************************************************************************************************************************************************
changed: [localhost]

TASK [Debug msg] ***********************************************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": [
        "Debug msg 1", 
        "Debug msg 2"
    ]
}

PLAY RECAP *****************************************************************************************************************************************************************************************************************************
localhost                  : ok=4    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

# Ref
- https://github.com/ansible/ansible
- https://www.ansible.com/
- https://linuxhint.com/ansible-tutorial-beginners/
- https://linuxhint.com/ansible-roles-tutorial/
- https://ansible-docs.readthedocs.io/zh/stable-2.0/rst/playbooks_filters.html