follow below steps to replicate
kubectl get pods

NAME                            READY   STATUS    RESTARTS   AGE
nginx-deploy-77b4fdf86c-hvxzx   1/1     Running   0          8m32s
nginx-deploy-77b4fdf86c-m8lcp   1/1     Running   0          8m32s
nginx-deploy-77b4fdf86c-q7vpp   1/1     Running   0          8m32s
nginx-deploy-77b4fdf86c-zrt42   1/1     Running   0          8m32s


kubectl get pdb
NAME       MIN AVAILABLE   MAX UNAVAILABLE   ALLOWED DISRUPTIONS   AGE
pdb-test   2               N/A               2                     3m23s

kubectl get nodes
NAME       STATUS   ROLES           AGE     VERSION
minikube   Ready    control-plane   5d12h   v1.27.3

kubectl drain minikube --ignore-daemonsets
node/minikube cordoned
error: unable to drain node "minikube" due to error:cannot delete Pods declare no controller (use --force to override): kube-system/storage-provisioner, continuing command...
There are pending nodes to be drained:
 minikube
cannot delete Pods declare no controller (use --force to override): kube-system/storage-provisioner


kubectl get nodes
NAME       STATUS                     ROLES           AGE     VERSION
minikube   Ready,SchedulingDisabled   control-plane   5d12h   v1.27.3

kubectl uncordon minikube
node/minikube uncordoned

kubectl get nodes
NAME       STATUS   ROLES           AGE     VERSION
minikube   Ready    control-plane   5d12h   v1.27.3




