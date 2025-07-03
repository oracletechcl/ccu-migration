# Documentation for La Barra

## sample-files Directory Documentation
This directory contains example Kubernetes manifests for configuring ingress controllers and persistent storage, suitable for use with Oracle Cloud Infrastructure (OCI).

Structure
```shell
sample-files/
├── ingress-controller/
│   ├── 00-configMap.yaml
│   ├── 01-ingress-controller.yaml
│   ├── 02-ingress-rule.yaml
│   └── 03-app-service.yaml
└── pv-pvc/
    ├── pv.yaml
    ├── pvc.yaml
    └── storage-class.yaml
```
--- 
### ingress-controller/
```yaml 00-configMap.yaml```
Defines a ConfigMap for the NGINX ingress controller, setting options such as regex support, rewrite logging, and trailing slash preservation.

```yaml 01-ingress-controller.yaml```
Contains the full deployment manifest for the NGINX ingress controller, including the namespace, service accounts, roles, and other required resources.

```yaml 02-ingress-rule.yaml```
Defines an Ingress resource with annotations for NGINX, TLS configuration, and routing rules. Placeholders are used for namespace, FQDN, secret, and service name.

```yaml 03-app-service.yaml```
Defines a Service resource for exposing an application within Kubernetes. Placeholders are present for the service name, namespace, and selector.

---

### pv-pvc/
```yamlpv.yaml```
Defines a PersistentVolume using the OCI File Storage Service (FSS) via NFS, with a storage class of oci-fss and mount options suitable for OCI.

```yamlpvc.yaml```
Defines a PersistentVolumeClaim that binds to the above PV, requesting 50Gi of storage in the generic-benchmark-fss namespace.

```yamlstorage-class.yaml```
Defines a StorageClass named oci-fss for dynamic provisioning of persistent volumes using the OCI FSS CSI driver.

These files provide a starting point for deploying ingress controllers and persistent storage on Kubernetes clusters running in Oracle Cloud Infrastructure. Be sure to replace placeholder values with your actual configuration before applying them.