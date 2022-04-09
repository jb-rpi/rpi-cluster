# Launch cluster remotly from the rpi3

From the rpi3, we first launch the master on 10.0.0.50 with:

> ansible-playbook -i hosts.ini install_master.yaml -kK -v

and then we ask workers to join the cluster with:

> ansible-playbook -i hosts.ini join_worker.yaml -kK -v


# Launch a docker app in the cluster:

and finally  to push our miner in the cluster:

> ansible-playbook -i hosts.ini push_docker_app.yaml -kK -v
