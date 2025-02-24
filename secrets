# Kubernetes Secrets Management

This repository provides an overview and examples of how to manage secrets in Kubernetes. Secrets are used to store sensitive information such as passwords, API keys, and certificates securely. Kubernetes provides a built-in mechanism to manage these secrets, ensuring they are stored and accessed securely.

## Table of Contents

- [What are Kubernetes Secrets?](#what-are-kubernetes-secrets)
- [Creating Secrets](#creating-secrets)
  - [Using `kubectl` Command](#using-kubectl-command)
  - [Using YAML Manifest](#using-yaml-manifest)
- [Using Secrets in Pods](#using-secrets-in-pods)
- [Best Practices](#best-practices)
- [References](#references)

---

## What are Kubernetes Secrets?

Kubernetes Secrets are objects that store sensitive data such as passwords, OAuth tokens, SSH keys, and other credentials. They are designed to keep this information secure while allowing pods to access it when needed. Secrets are stored in the Kubernetes cluster's etcd database, and access to them can be controlled using Role-Based Access Control (RBAC).

---

## Creating Secrets

### Using `kubectl` Command

You can create a secret using the `kubectl create secret` command. There are different types of secrets, such as generic, TLS, and docker-registry.

#### Example: Creating a Generic Secret

```bash
kubectl create secret generic my-secret \
  --from-literal=username=admin \
  --from-literal=password=secret
