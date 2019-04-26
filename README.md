# Ansible scripts for settings up AKS and managing EMQX deployments

## How to provision AKS

Create an env file
* az_environment defines name of the environment (used for naming resources in Azure)
* az_aks_node_count defines number of nodes in the AKS cluster

Run `ansible-playbook play-setup-aks.yml -e @env/<name of the env file>`

## Managing Kubernetes deployment secrets

Store password for ansible vault in vault_password file at the root of this repository. After that you can edit secrets in group_vars/all/encrypted.yml by running `ansible-vault edit group_vars/all/encrypted.yml`. Then you can define what gets decrypted and encrypted from roles/aks-deployment/files/ in roles/aks-deployment/tasks/mains.yml. It is possible to test that decryption works with `ansible-playbook play-aks-deployment.yml --tags decrypt` and that encryption works with `ansible-playbook play-aks-deployment.yml --tags encrypt`
