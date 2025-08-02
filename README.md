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
   git clone https://github.com/umer-r/ansible-k3s-with-mysql.git
   cd ansible-k3s-with-mysql
   vim inventory/hosts.ini # replace host
    ```

2. Create vault.yml
    ```bash
    ansible-vault create group_vars/all/vault.yml
    ```

    Add variables:
    ```
    mysql_root_password: ""
    k3s_user_password: ""
    ```

    Configure variables in vars:
    ```bash
    echo "pass" > group_vars/all/.vault_pass.txt
    vim group_vars/all/vars.yml # replace tls-sans 
    ```

3. Install collections:
    ```bash
    ansible-galaxy collection install -r requirements.yml
    ansible -i inventory/hosts.ini all -m ansible.builtin.ping
    ```

4. Run playbook:
    ```bash
    ansible-playbook -i inventory/hosts.ini --check playbook.yml --ask-vault-pass
    ansible-playbook -i inventories/production/hosts.ini playbook.yml --ask-vault-pass
    ansible-playbook -i inventory/hosts.ini playbook.yml
    ```

## Run locally (ubuntu)

1. Install ansible:
   ```bash
   apt update
   apt install software-properties-common
   add-apt-repository --yes --update ppa:ansible/ansible
   apt install ansible
    ```

2. Run playbook:
    ```bash
    ansible-playbook --connection=local --inventory 127.0.0.1, playbook.yml
    ```
