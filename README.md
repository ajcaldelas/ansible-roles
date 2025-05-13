# ansible-roles

## Pre-Reqs

- DNS entries need to exist for the API VIP and the Ingress VIP
- Bastion host to serve the agent ISO

## OpenShift role

- Attempts to download pre-reqs:
    - OpenShift Client (OC)
    - OpenShift Installer (openshift-install)
- Installs NGINX to host the agent ISO
- Templates the Install Config and the Agent Config to generate an ISO to deploy a cluster
- Atttempts to connect baremetal hosts via Redfish to mount an HTTP ISO file to boot
    - Vendors
        - Lenovo (Partial Not completed)
        - Dell (Not supported currently)
        - HPE (Not supported currently)

### OpenShift Role Variables

| Name              | Description                    | Default |
|-------            | ------------                   | --------|
| openshift_version | Version of OpenShift to install | `4.18` |
| openshift_release_channel | The Channel release for the OpenShift Installer | `stable`|
| cluster_name | **Required** The name of the OpenShift Cluster | `example-cluster` |
| base_domain | **Required** The base domain, example amd.com | `amd.com` |
| api_vip | **Required** IP Address of the API VIP | `10.216.189.199` |
| ingress_vip | **Required** IP address of the Ingress VIP | `10.216.189.199` |    
| worker_node_count | **Required** Number of worker nodes on the cluster | 2 |
