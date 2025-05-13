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
        