# cilium-gateway-api

⚠️ **Work in progress** for a future blog post [here](https://blog.ogenki.io/)

## Dependencies matters

```mermaid
graph TD;
    Namespaces-->CRDs;
    CRDs-->Observability;
    CRDs-->Security;
    CRDs-->Infrastructure;
    Crossplane-->Infrastructure;
    Crossplane-->Security;
    Observability-->Apps;
    Infrastructure-->Apps;
    Security-->Apps;
    Security-->Observability;
    Security-->Infrastructure
```

This diagram can be hard to understand so these are the key information:

* Namespaces are the first resources to create, all other resources may be cluster scoped
* CRDs that allow to extend Kubernetes capabilities must be present in order to use them in all other applications if needed.
* Crossplane creates IRSA permissions which are required by some components
* Security defines `external-secrets` that are needed by some applications in order to start.
