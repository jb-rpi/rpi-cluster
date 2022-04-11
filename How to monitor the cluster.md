In order to monitor our cluster, we will rely on Grafana and Prometheus.

The goal is to get from the router-pi3 the grafana runnning and displaying different KPIs of our cluster.

# Install Grafana

We will rely on this documentation:
https://grafana.com/tutorials/install-grafana-on-raspberry-pi/

After the installation, we enable the Grafana server. It is now accessible at http://<your ip>:3000
  
  
# Install Prometheus
  
We can follow:
http://www.d3noob.org/2020/02/installing-prometheus-and-grafana-on.html?m=1
  
or 
https://leanpub.com/rpcmonitor/read

Apparently, we need to install a prometheus server on our main node where grafana is located. HEre the 10.0.0.1.
  
And configure node_exporter to report to this node.
  
  
