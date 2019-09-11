# Red Hat Solution Architect Demo Project 2019

## Ansible
- This folder holds playbooks and other Ansible related stuff to make your life and deploying the demo environment easier

## Accessing OCP via Ansible using API authentication
- Make sure you have API access

- Use oc to login to the OCP environment

`oc login --token=<YOUR TOKEN> --server=<API URL>`

- Store your credentials in $HOME/.kube/config.json

`kubectl config view -o json > $HOME/.kube/config.json`

- Run the ocp-test.yml playbook to test connectivity

`ansible-playbook -vvv playbooks/ocp-test.yml`
