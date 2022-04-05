# create key and distribute it

We want to automate launch of the cluster from the router pi3 (10.0.0.1) in our system.
This router is the one providing access to the Internet to the cluster. It also acts as a DHCP server (more to come on this).

To use Ansible, we need to set-up ssh Keys. For this, we create the same user on the 3 nodes of the cluster (here pi).
From  router, we generate key thanks to ssh-keygen, no paswword and we copy the pub key thanks so ssh-copyid "node".

We can now directly ssh to thos nodes.
