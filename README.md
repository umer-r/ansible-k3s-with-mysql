# K3s with MySQL Datastore - Ansible Playbook

Installs a single-node K3s cluster with MySQL as the datastore

## Features
- MySQL installation
- Traefik ingress controller
- Bash completion for kubectl
- Idempotent operations

## Usage

1. Clone repo:
   ```bash
   git clone https://github.com/umer-r/ansible-k3s-with-mysql
   cd k3s-mysql-ansible
    ```

2. Create vault.yml
    ```bash
    cd group_vars/all
    ansible-vault create vault.yml
    ```
    Add variables:
        - mysql_root_password: ""
        - k3s_user_password: ""

3. Install collections:
    ```bash
    ansible-galaxy collection install -r requirement.yml
    ```

4. Run playbook:
    ```bash
    ansible-playbook -i inventories/production/hosts.ini playbook.yml --ask-vault-pass
    ```

