# argocd setup steps we should have 1)kubernet cluster 
this is my argocd yaml project

#1) install argocd 

#2)  kubectl create namespace argocd
 
 # kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml -n argocd

#3)kubectl get svc -n argocd   ---to so service argocd-server

#4)kubectl edit svc argocd-server -n argocd        or        path it       $ kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

# using cloud pord forward command 

 kubectl port-forward -n argocd svc/argocd-server 8443:443 --address=0.0.0.0 &

#5)change clusteip service to NodePort or LoadBalancer
6)Access service port 

#7)username -admin and for password enter command as fallows

#8)  kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" ---for docker engine or

kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo      -----for cloud

#9)decrypt password on browser with base64 and enter passowrd

#10)copy declerative argocd yaml---->install.yaml

11)deploy service and deployment in same namespace wheather uoy wont acess it

#12)we should have argocd yaml where speciified your repo url of deploymentyaml and service.yaml


#   for declerative apply yaml

# kubectl apply -f deploy.yaml -n nginx
# kubectl apply -f svc.yaml -n nginx
# kubectl apply -f argocd-application.yaml 

give path yoyr application and apply it 

# if you are deploing manually on gui you must copy repo url from browser link of github  then enter folder/path  name where yaml file are present 

# synchronise regularly when you update image or replicas

#replicas firstly create automatically new and then old delete when you update 

#13) delete argocd 

kubectl delete -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

