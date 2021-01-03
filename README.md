# helm-kube
#deploy ingress (ingress-ngnix)
# kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.42.0/deploy/static/provider/cloud/deploy.yaml

#deploy cert manger (ingress-ngnix)
# helm install \
cert-manager \
--namespace ingress-nginx \
--version v0.16.1 \
--set installCRDs=true \
--set nodeSelector."beta\.kubernetes\.io/os"=linux \
jetstack/cert-manager

# deploy cluster issuer
kubectl apply -f ClusterIssuer.yaml

#Create the namespace
# kubectl create ns jitsi

#install through helm
# helm install jitsi . --namespace jitsi

#upgrade through helm
# helm upgrade jitsi . --namespace jitsi

#uninstall through helm
# helm uninstall jitsi --namespace jitsi

#Check all PODs
# kubectl get po -n jitsi

#Restarting prosody PODs 
# kubectl delete po jitsi-meet-prosody-0 -n jitsi

#Restating jbv PODs
# kubectl delete po jitsi-meet-jvb-0-d844f869f-b6wh5 -n jitsi

#to check the prosody logs
# kubectl logs -f jitsi-meet-prosody-0 jitsi-meet-prosody -n jitsi

#to check the jicofo logs
# kubectl logs -f jitsi-meet-prosody-0 jitsi-meet-jicofo -n jitsi

#Entering into PODs
# kubectl exec -it jitsi-meet-jvb-0-74ff4fd97b-6px5h -n jitsi bash

