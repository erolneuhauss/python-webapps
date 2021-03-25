# python-webapps-infra

Kubernetes manifests for Flux v2

## Troubles: can NOT use **vars** for configMapRef or secretRef

```yaml
vars:
  - name: APP_COLOR
    objref:
      kind: ConfigMap
      name: app_color
      apiVersion: v1
```
 With a strategic merge patch, a list is either replaced or merged depending
 on its patch strategy. The patch strategy is specified by the value of the
 patchStrategy key in a field tag in the Kubernetes source code.
 And unfortunately, envFrom doesn't have patch strategy defined.
 using
 https://kubectl.docs.kubernetes.io/references/kustomize/kustomization/patchesjson6902/
 instead
