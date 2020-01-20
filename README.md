# Ansible scripts for settings up AKS and managing EMQX deployments

## How to provision AKS

Create an env file
* az_environment defines name of the environment (used for naming resources in Azure)
* az_aks_node_count defines number of nodes in the AKS cluster

Run `ansible-playbook play_setup_aks.yml -e @env/<name of the env file>`

## Deploy kubernetes manifests

Applying all manifests into an environment 
* Run `ansible-playbook play_apply_manifests.yml -e @env/dev.yml`

Applying a specific manifest into an environment
* Run `ansible-playbook play_apply_manifests.yml -e @env/dev.yml -e service=<filename without .yml postfix>`

