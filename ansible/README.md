# Red Hat Solution Architect Demo Project 2019

## Ansible
- This folder holds playbooks and other Ansible related stuff to make your life and deploying the demo environment easier

## Accessing OCP via Ansible using API authentication
- Make sure you have API access

- Create a dummy host in /etc/ansible/hosts

`echo "ocp-demo" >> /etc/ansible/hosts`

- Install the openshift and kubernetes python modules (if you don't have them already)

`pip install openshift kubernetes --user`

- Use oc to login to the OCP environment

`oc login --token=<YOUR TOKEN> --server=<API URL>`

- Store your credentials in $HOME/.kube/config.json

`kubectl config view -o json > $HOME/.kube/config.json`

- Run the ocp-test.yml playbook to test connectivity

`ansible-playbook -vvv playbooks/ocp-test.yml`

- You should receive a list of all running pods
