# argocd setup steps we should have 1)kubernet cluster 2)for declerative we should have argo cd cli 
this is my argocd yaml project
1) create namespace kubectl create namespace argocd 
2)kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
3)kubectl get svc -n argocd   ---to so service argocd-server
4)kubectl edit svc argocd-server -n argocd or path it kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
5)change clusteip service to NodePort or LoadBalancer
6)Access service port 
7)username -admin and for password enter command as fallows
8)kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" ---for docker engine or[kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 –d]
9)decrypt password on browser with base64 and enter passowrd
10)copy declerative argocd yaml---->install.yaml
11)deploy service and deployment in same namespace wheather uoy wont acess it
