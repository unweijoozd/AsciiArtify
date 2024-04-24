# Minimum Viable Product (MVP):

`Goal`: Implement and lauch basix version of a product that includes only essential features in order to receive early feedback and validate core idea and concept,
reduce time to market, minimize consts, mitigate risks associated with building a full-featured product without sufficient validation.

1. Check functionality of the application
- Forward the ports with the following command:
```bash
$ k port-forward -n demo svc/ambassador 8088:80&
Forwarding from 127.0.0.1:8088 -> 80
Forwarding from [::1]:8088 -> 80
```
- Make request to this port and check an answer as the app version:
```bash
$ curl localhost:8088
k8sdiy-api:819ff80#
```

2. Fix config issue
- Check network config of the app:
```bash
$ k get svc -n demo
NAME               TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)               AGE
ambassador         LoadBalancer   10.43.13.90   <pending>     80:32432/TCP          84s
```
- In [repo with helm config files](https://github.com/unweijoozd/go-demo-app/blob/master/helm/values.yaml) change `api-gateway:` to `NodePort`
- Sync and apply these changes using ArgoCD
- Check the result
```bash
✗ k get svc -n demo
NAME               TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)         AGE
ambassador         NodePort       10.43.13.90   <none>        80:32432/TCP    62s
```

3. Check the app behavior after fixing config issue.
- Upload file from local repo to remote server:
```bash
curl -F 'image=@g.png' localhost:8088/img/
```
- See result in console