# Deploy Argo CD

~~~
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
~~~

# Modify the service

The Argo CD UI is served by argocd-server service. By default, argocd-server is of type ClusterIP.

We have multiple options to access the UI. The easiest way to access the UI on macOS is forwarding the Argo CD server HTTPS port 443 to a different port.

We need to create argocd namespace before execute below cmd
~~~
kubectl port-forward -n argocd service/argocd-server 8443:443
~~~

# Grab the password to login to the dashboard

~~~
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
~~~

#  Login to the dashboard

https://localhost:8443/ 
