# Deploying Cassandra cluster in Vagrant using Ansible

## Required tools set:
- Virtualbox
- Vagrant

## Execution steps:
- Install virtual box and vagrant
- git clone https://github.com/apkan/vagrant-cassandra-ansible.git
- cd vagrant-cassandra-ansible
- vagrant up

## Output:
Ansible playbook will execute a set of tasks and eventually a Cassandra cluster status will be displayed.

## Directory structure
``` sh
└── cassandra-cluster
    ├── handlers
    │   └── main.yml
    ├── tasks
    │   └── main.yml
    ├── templates
    │   ├── cassandra.sh
    │   └── cassandra.yaml.j2
    └── vars
        └── main.yml
```

