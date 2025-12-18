flowchart LR
  A[Developer push to user-cms-app] --> B[GitLab CI: build/test]
  B --> C[Docker build]
  C --> D[Push image to GitLab Registry (SHA tag)]
  E[Update user-cms-deploy manifests] --> F[ArgoCD sync]
  F --> G[Kubernetes: Deployments/Service/PVC]
  G --> H[User accesses API via NodePort/Ingress]
  F --> I[Rollback via Git revert / ArgoCD history]
