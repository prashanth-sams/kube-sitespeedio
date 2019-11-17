# Kubernetes sitespeed.io
> Kubernetes orchestrated container system for sitespeedio

### **Deploy Kubernetes**

`Services`, `Deployments`, and `Pods`; and eventually `volumes`
```
kubectl create namespace sitespeed-io
kubectl create -f kubeconfig/ --namespace=sitespeed-io
```

### **Data manipulation**

Clone data and copy it inside your sitespeed container

```
sitespeed_pod=$(kubectl get pods -n sitespeed-io | grep sitespeed-io | awk '{print $1}')

kubectl cp ~/<path>/. sitespeed-io/$sitespeed_pod:.

kubectl exec -it --namespace=sitespeed-io $sitespeed_pod -- bash -c "/start.sh urls.txt --budget.configPath budget.json --graphite.host=graphite --browsertime.iterations 1 --browsertime.browser chrome"
```

### **SitespeedIO runner #generic**
```
kubectl exec -it --namespace=<custom-namespace> <custom_pod_name> -- bash -c "/start.sh urls.txt --budget.configPath budget.json --graphite.host=graphite --browsertime.iterations 1 --browsertime.browser chrome"
```
Example: 
```
kubectl exec -it --namespace=sitespeed-io sitespeed-io-677775db6d-kgnw5 -- bash -c "/start.sh urls.txt --budget.configPath budget.json --graphite.host=graphite --browsertime.iterations 1 --browsertime.browser chrome"
```