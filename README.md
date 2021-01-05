# helm-kube
### deploy ingress (ingress-ngnix)

 ```sh
 kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.42.0/deploy/static/provider/cloud/deploy.yaml
```
### deploy cert manger (ingress-ngnix)

```sh
 helm install \
cert-manager \
--namespace ingress-nginx \
--version v0.16.1 \
--set installCRDs=true \
--set nodeSelector."beta\.kubernetes\.io/os"=linux \
jetstack/cert-manager
```
### deploy cluster issuer

```sh
kubectl apply -f ClusterIssuer.yaml
```
### Create the namespace
```sh
kubectl create ns jitsi
```
### install through helm

```sh
helm install jitsi . --namespace jitsi
```
### upgrade through helm

```sh
helm upgrade jitsi . --namespace jitsi
```
### uninstall through helm

```sh
helm uninstall jitsi --namespace jitsi
```
### Check all PODs

```sh
kubectl get po -n jitsi
```

### Restarting prosody PODs 

```sh
kubectl delete po jitsi-meet-prosody-0 -n jitsi
```

### Restating jbv PODs

```sh
kubectl delete po jitsi-meet-jvb-0-d844f869f-b6wh5 -n jitsi
```
#### to check the prosody logs

```sh
kubectl logs -f jitsi-meet-prosody-0 jitsi-meet-prosody -n jitsi
```
### to check the jicofo logs

```sh
kubectl logs -f jitsi-meet-prosody-0 jitsi-meet-jicofo -n jitsi
```
### Entering into PODs

```sh
kubectl exec -it jitsi-meet-jvb-0-74ff4fd97b-6px5h -n jitsi bash
```
