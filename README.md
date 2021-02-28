# kubernetes-dashboard-deployment
$ kubectl apply -f kubernetes-dashboard-deployment.yml
namespace/kubernetes-dashboard created
serviceaccount/kubernetes-dashboard created
service/kubernetes-dashboard created
secret/kubernetes-dashboard-certs created
secret/kubernetes-dashboard-csrf created
secret/kubernetes-dashboard-key-holder created
configmap/kubernetes-dashboard-settings created
role.rbac.authorization.k8s.io/kubernetes-dashboard created
clusterrole.rbac.authorization.k8s.io/kubernetes-dashboard created
rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard created
clusterrolebinding.rbac.authorization.k8s.io/kubernetes-dashboard created
deployment.apps/kubernetes-dashboard created
service/dashboard-metrics-scraper created
deployment.apps/dashboard-metrics-scraper created

$ kubectl get deployments -n kubernetes-dashboard
NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
dashboard-metrics-scraper   0/1     1            0           88s
kubernetes-dashboard        0/1     1            0           88s

$ kubectl get pods -n kubernetes-dashboard -o wide
NAME                                         READY   STATUS              RESTARTS   AGE     IP       NODE    NOMINATED NODE   READINESS GATES
dashboard-metrics-scraper-79c5968bdc-dxr5f   0/1     ContainerCreating   0          6m27s   <none>   node1   <none>           <none>
kubernetes-dashboard-9f9799597-jmdqh         0/1     ContainerCreating   0          6m27s   <none>   node1   <none>           <none>

$ kubectl get service -n kubernetes-dashboard
NAME                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)         AGE
dashboard-metrics-scraper   ClusterIP   10.109.68.11     <none>        8000/TCP        7m37s
kubernetes-dashboard        NodePort    10.108.229.192   <none>        443:31561/TCP   7m38s


Accessing Kubernetes Dashboard
My Service deployment was assigned a port 30038/TCP. Let’s confirm if access to the dashboard is working.
