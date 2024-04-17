### Installation of the ArgoCD system

1. Creating a k3d cluster with the name argo:
      ``` bash
      k3d cluster create argo
      ```

2. Checking information about the Kubernetes cluster:
      ``` bash
      kubectl cluster-info
      ```

3. Creating a namespace for ArgoCD:
      ``` bash
      kubectl create namespace argocd
      ```

4. Application of manifests to install ArgoCD:
      ``` bash
      kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
      ```

5. Checking ArgoCD resources:
      ``` bash
      kubectl get all -n argocd
      ```

6. Checking the status of ArgoCD pods:
      ``` bash
      kubectl get pod -n argocd -w
      ```

7. Port forwarding to access the ArgoCD interface via a web browser:
      ``` bash
      kubectl port-forward svc/argocd-server -n argocd 8080:443&
      ```

8. Login to the ArgoCD web interface:
      - Login: `admin`
      - The password can be obtained using the command:
          ``` bash
          kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
          ```
      - You can decode and display the password as follows:
          ``` bash
          kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
          ```