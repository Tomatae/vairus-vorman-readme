# Kubernetes preparations
For Auto installation use bat/sh script depending on your system.

> Windows version uses an awful python bodge due to my poor skills in batch


Manual installation command list

```
kubectl create ns vairus-vorman
kubectl create secret generic db-pass -n vairus-vorman --from-literal db-password=<password>
kubectl create sa deploy -n vairus-vorman
kubectl create rolebinding deploy -n vairus-vorman --clusterrole edit --serviceaccount vairus-vorman:deploy
```
---
for Linux:
	
`kubectl get secret -n vairus-vorman $(kubectl get sa -n vairus-vorman deploy -o jsonpath='{.secrets[].name}') -o jsonpath='{.data.token}'`

for Windows:

`kubectl get sa -n vairus-vorman deploy -o jsonpath='{.secrets[].name}'`

Copy returned value to the following command:
`kubectl get secret -n vairus-vorman <value> -o jsonpath='{.data.token}'`

---
- Use the returned value to create Kuberneters Deploy Token via GitLab

- Create Gitlab Deploy Token and insert value in following command:

`kubectl create secret docker-registry vairus-vorman-deploy-pull --docker-server git.codenrock.com:5050 --docker-username <username> --docker-password <password> --namespace vairus-vorman`



