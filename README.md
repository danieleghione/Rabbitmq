1 step:
  Installing RabbitMQ Cluster Operator in a Kubernetes Cluster: https://www.rabbitmq.com/kubernetes/operator/install-operator.html

2 Step:
  download the repository files
  
3 step:
  install the rabbitmq instance: kubectl create -f rabbitmq.yaml

4 step:
  creates the service that exposes the management interface. I use Metallb as a LoadBalancer: kubectl create -f rabbitmq_svc_management.yaml
  
5 step:
  creates the service that exposes the port for the mqtt protocol. I use Metallb as a LoadBalancer: kubectl create -f rabbitmq_svc_mqtt.yaml
  
6 step:
  create your user account: kubectl exec NAME_OF_YOU_POD -it -- rabbitmqctl add_user myUser myPass

7 step:
  To make user an administrator run: kubectl exec NAME_OF_YOU_POD -it -- rabbitmqctl set_user_tags myUser administrator

8 step:
  Make it Admin on everything: kubectl exec NAME_OF_YOU_POD -it -- rabbitmqctl set_permissions -p / myUser ".*" ".*" ".*"
