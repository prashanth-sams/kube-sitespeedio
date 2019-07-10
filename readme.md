# Kubernetes sitespeed.io
> Kubernetes orchestrated container system for sitespeedio

### **Deploy Kubernetes**

`Services`, `Deployments`, and `Pods`; and eventually `volumes`
```
kubectl create -f kubeconfig/ --namespace=sitespeed-io
```

### **sitespeedio runner**
```
kubectl exec -it --namespace=<custom-namespace> <custom_pod_name> -- bash -c "/start.sh urls.txt --budget.configPath budget.json --graphite.host=graphite --browsertime.iterations 1 --browsertime.browser chrome"
```
Example: 
```
kubectl exec -it --namespace=sitespeed-io sitespeed-io-677775db6d-kgnw5 -- bash -c "/start.sh urls.txt --budget.configPath budget.json --graphite.host=graphite --browsertime.iterations 1 --browsertime.browser chrome"
```