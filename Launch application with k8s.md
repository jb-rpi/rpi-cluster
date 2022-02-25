Now that the cluster has been created, it is possible to start an application and let k8s manages it.

Create a yaml file containing the description and launhc it with:


$ kubectl apply -f xxx.yaml.

Here, we have created a dockerized miner (for XMR) and use the xmrig-example.ymal
