# How to launch our cluster with Ansible

Inspired by https://devopssec.fr/article/creer-cluster-kubernetes-multi-noeud-vagrant-ansible

and:
https://buildvirtual.net/deploy-a-kubernetes-cluster-using-ansible/

The goal is to rely on ansible in order to launch the k8s cluster over our rpis.

It consists of hosts.ini indicating the hosts, the playbook in order to indicate to Ansible what to do.

# how to run it:

In the corresponding folder rpi-cluster/ansible, run:

ansible-playbook -i hosts.ini playbook.yaml -kK

(main.yaml files must be in tasks folder)

