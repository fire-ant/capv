### CAPI CLUSTER-API-PROVIDER-VSPHERE Infrastructure Provider Chart

This chart is derived from the cluster-api-provider-vsphere infrastructure provider of the [Cluster API](https://cluster-api.sigs.k8s.io) project 

see https://github.com/kubernetes-sigs/cluster-api-provider-vsphere

### Values
for Chart Values see [here](charts/capv/README.md)

#### Notes

Note that Chart releases correlate image versions with CRDs and as such may need to upgrade/replace CRD versions over time.
the cluster-api-provider-vsphere project requires a bootstrap secret/credential which is hardcoded to:

apiVersion: v1
kind: Secret
metadata:
  labels:
    cluster.x-k8s.io/provider: infrastructure-vsphere
    cluster.x-k8s.io/v1beta1: v1beta1
  name: capv-manager-bootstrap-credentials
  namespace: capv-system
stringData:
  credentials.yaml: |-
    username: '${VSPHERE_USERNAME}'
    password: '${VSPHERE_PASSWORD}'
type: Opaque

The credentials will need to be generated separately and managed outside of the chart.
