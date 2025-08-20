# 🎯 Argo CD Deployment Guide


## 📘 Step 1: Add and Update the Argo Helm Repository

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
```

## 🚀 Step 2: Deploy Argo CD Using Helm

```bash
cd apps/argocd
helm upgrade -i argocd argo/argo-cd -n argocd --create-namespace -f values.yaml --wait
```

💡 Note: The --install (-i) flag ensures Helm installs Argo CD if it’s not already present. The --wait flag pauses execution until all resources are ready.

---

# 🚀 Bootstrap Argo CD Applications

To initialize the Argo CD applications following the app pattern, we need to bootstrap them accordingly.

## 📦 Bootstrap ApplicationSets

```bash
cd bootstrap
kustomize build . | kubectl apply -f -
```