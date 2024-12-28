# Kubernetes Interview Questions and Answers (With Practical Examples)

---

## **Basic Concepts**

### **1. What is Kubernetes, and why is it used?**
Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It ensures high availability, scalability, and efficient resource utilization.

---

## **Practical Questions with Commands**

### **Pod Management**

#### **1. How do you create a Pod using a YAML file?**
- Example YAML file (`pod.yaml`):
  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: my-pod
  spec:
    containers:
    - name: nginx
      image: nginx:latest
  ```
- Command to create the Pod:
  ```bash
  kubectl apply -f pod.yaml
  ```

#### **2. How do you check the status of all Pods in a Namespace?**
- Command:
  ```bash
  kubectl get pods -n <namespace>
  ```

#### **3. How do you delete a Pod?**
- Command:
  ```bash
  kubectl delete pod <pod-name>
  ```

#### **4. How do you update the image of a running Pod in a Deployment?**
- Command:
  ```bash
  kubectl set image deployment/<deployment-name> <container-name>=<new-image>
  ```

#### **5. How do you scale a Deployment?**
- Command:
  ```bash
  kubectl scale deployment <deployment-name> --replicas=<number-of-replicas>
  ```

---

### **Networking**

#### **1. How do you expose a Deployment as a Service?**
- Command:
  ```bash
  kubectl expose deployment <deployment-name> --type=<service-type> --port=<port> --target-port=<target-port>
  ```
  Example:
  ```bash
  kubectl expose deployment my-app --type=NodePort --port=80 --target-port=8080
  ```

#### **2. How do you list all Services in a cluster?**
- Command:
  ```bash
  kubectl get services
  ```

#### **3. How do you describe a Service?**
- Command:
  ```bash
  kubectl describe service <service-name>
  ```

#### **4. How do you create an Ingress resource?**
- Example YAML file (`ingress.yaml`):
  ```yaml
  apiVersion: networking.k8s.io/v1
  kind: Ingress
  metadata:
    name: my-ingress
  spec:
    rules:
    - host: example.com
      http:
        paths:
        - path: /
          pathType: Prefix
          backend:
            service:
              name: my-service
              port:
                number: 80
  ```
- Command to apply the Ingress:
  ```bash
  kubectl apply -f ingress.yaml
  ```

---

### **Storage**

#### **1. How do you create a Persistent Volume (PV)?**
- Example YAML file (`pv.yaml`):
  ```yaml
  apiVersion: v1
  kind: PersistentVolume
  metadata:
    name: my-pv
  spec:
    capacity:
      storage: 1Gi
    accessModes:
    - ReadWriteOnce
    hostPath:
      path: /data/my-pv
  ```
- Command to create the PV:
  ```bash
  kubectl apply -f pv.yaml
  ```

#### **2. How do you create a Persistent Volume Claim (PVC)?**
- Example YAML file (`pvc.yaml`):
  ```yaml
  apiVersion: v1
  kind: PersistentVolumeClaim
  metadata:
    name: my-pvc
  spec:
    accessModes:
    - ReadWriteOnce
    resources:
      requests:
        storage: 1Gi
  ```
- Command to create the PVC:
  ```bash
  kubectl apply -f pvc.yaml
  ```

#### **3. How do you check the status of Persistent Volumes?**
- Command:
  ```bash
  kubectl get pv
  ```

---

### **Logs and Debugging**

#### **1. How do you view logs for a specific Pod?**
- Command:
  ```bash
  kubectl logs <pod-name>
  ```

#### **2. How do you view logs for a specific container in a Pod?**
- Command:
  ```bash
  kubectl logs <pod-name> -c <container-name>
  ```

#### **3. How do you execute a command inside a container?**
- Command:
  ```bash
  kubectl exec -it <pod-name> -- <command>
  ```
  Example:
  ```bash
  kubectl exec -it my-pod -- /bin/bash
  ```

#### **4. How do you describe a Pod to check events?**
- Command:
  ```bash
  kubectl describe pod <pod-name>
  ```

---

### **Scaling and Autoscaling**

#### **1. How do you enable Horizontal Pod Autoscaling (HPA)?**
- Command:
  ```bash
  kubectl autoscale deployment <deployment-name> --min=<min-replicas> --max=<max-replicas> --cpu-percent=<target-cpu-utilization>
  ```
  Example:
  ```bash
  kubectl autoscale deployment my-app --min=1 --max=10 --cpu-percent=50
  ```

#### **2. How do you view the current HPA configuration?**
- Command:
  ```bash
  kubectl get hpa
  ```

---

### **Security**

#### **1. How do you create a Role with specific permissions?**
- Example YAML file (`role.yaml`):
  ```yaml
  apiVersion: rbac.authorization.k8s.io/v1
  kind: Role
  metadata:
    namespace: default
    name: pod-reader
  rules:
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["get", "watch", "list"]
  ```
- Command to create the Role:
  ```bash
  kubectl apply -f role.yaml
  ```

#### **2. How do you create a RoleBinding?**
- Example YAML file (`rolebinding.yaml`):
  ```yaml
  apiVersion: rbac.authorization.k8s.io/v1
  kind: RoleBinding
  metadata:
    name: read-pods
    namespace: default
  subjects:
  - kind: User
    name: jane
    apiGroup: rbac.authorization.k8s.io
  roleRef:
    kind: Role
    name: pod-reader
    apiGroup: rbac.authorization.k8s.io
  ```
- Command to apply the RoleBinding:
  ```bash
  kubectl apply -f rolebinding.yaml
  ```

---

This document now includes practical Kubernetes commands along with conceptual explanations.


