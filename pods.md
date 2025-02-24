# Kubernetes Pods

## Overview
A **Pod** is the smallest and simplest deployable unit in Kubernetes. It represents a single instance of a running process in the cluster and can contain one or more containers that share storage, networking, and configuration.

## Key Features
- **Multiple Containers**: A Pod can contain multiple tightly coupled containers that share resources.
- **Shared Network**: All containers in a Pod share the same network namespace, including IP address and ports.
- **Shared Storage**: Pods can use shared volumes for persistent data storage.
- **Lifecycle Management**: Kubernetes manages Pod scheduling, scaling, and deletion.

## Pod Types
- **Single Container Pod**: The most common type, running a single application container.
- **Multi-Container Pod**: Containers work together in a single Pod, often using the **sidecar** pattern.

## Pod Lifecycle
1. **Pending** - Pod is created but not yet scheduled.
2. **Running** - Containers are running and ready.
3. **Succeeded** - Containers have completed execution successfully.
4. **Failed** - Containers have terminated due to an error.
5. **Unknown** - The state cannot be determined.

## Creating a Pod
You can define a Pod in YAML format:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: nginx:latest
      ports:
        - containerPort: 80
```

Apply the Pod using:
```sh
kubectl apply -f my-pod.yaml
```

## Managing Pods
- List Pods:
  ```sh
  kubectl get pods
  ```
- Describe a Pod:
  ```sh
  kubectl describe pod my-pod
  ```
- Delete a Pod:
  ```sh
  kubectl delete pod my-pod
  ```

## Conclusion
Kubernetes Pods are fundamental building blocks for deploying containerized applications. They enable efficient resource sharing, networking, and storage management within a cluster.

---

For more details, refer to the [Kubernetes Documentation](https://kubernetes.io/docs/concepts/workloads/pods/).
