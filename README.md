# CLO835-K8S




ssh-keygen -t rsa -f k8assignment  
scp -i k8sassignment -r  <IP>:/tmp

cd /tmp

chmod +x init_kind.sh 

./init_kind.sh


alias k=kubectl

k get nodes 

kubectl cluster-info

k create ns mysql

k apply -f mysql-pod.yaml -n mysql 

k apply -f mysql-service.yaml -n mysql
 
k get svc -n mysql 
 
k create ns employee

k apply -f webserver-pod.yaml -n employee

k apply -f webserver-service.yaml -n employee

k port-forward svc/employee 8080:8080 -n employee  

k create ns employeepink

k apply -f webserver-podpink.yaml -n employeepink

k apply -f webserver-servicepink.yaml -n employeepink

k port-forward svc/employeepink 8081:8080 -n employeepink  

k logs employeeblue -n employee

k apply -f mysql-replica.yaml -n mysql

k apply -f webserver-replica.yaml -n employee

k apply -f mysql-deployment.yaml -n mysql

k apply -f webserver-deployment.yaml -n employee 

k apply -f webserver-deploymentpink.yaml -n employeepink 

k apply -f webserver-Nodeport.yaml -n employee

k apply -f webserver-Nodeportpink.yaml -n employeepink

k rollout restart deployment employee -n employee