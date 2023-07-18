# Playbook_ansible
Play 1 - Provision OpenStack Instances using Heat:
It sets up variables required for provisioning instances like key name, image, flavor, network, etc.
It uses the os_stack module to create a Heat stack with the specified parameters.
After creating the stack, it updates the inventory with the new instance IP addresses.


Play 2 - Setting up the Kubernetes Environment:

This play is responsible for setting up the Kubernetes environment on the provisioned instances.
It performs various tasks like creating a kube user account, setting up Docker, installing Kubernetes packages, etc.

Play 3 - Creating the Cluster and Integrating Cloud Controller:

This play is executed on the master node.
It downloads necessary Kubernetes manifest files, initializes the Kubernetes cluster, and sets up the kubeconfig for the kube user.
It also creates a secret for cloud-config and applies RBAC resources for the OpenStack cloud controller manager.

Play 4 - Generating the Joining File:
This play runs on the master node to generate a file containing the information needed for worker nodes to join the cluster.

Play 5 - Joining Worker Nodes to the Cluster:
This play is executed on the worker nodes to join them to the Kubernetes cluster using the joining file.

Play 6 - Cinder Integration:
This play is run on the master node and sets up the Cinder CSI (Container Storage Interface) plugin.
