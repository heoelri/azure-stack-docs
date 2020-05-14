---
title: Support policies for AKS engine on Azure Stack Hub  
description: This topic contains the support policies for AKS engine on Azure Stack Hub.
author: mattbriggs

ms.topic: article
ms.date: 3/19/2020
ms.author: mabrigg
ms.reviewer: waltero
ms.lastreviewed: 3/19/2020

# Intent: Notdone: As a < type of user >, I want < what? > so that < why? >
# Keyword: Notdone: keyword noun phrase

---


# Support policies for AKS engine on Azure Stack Hub

This article provides details about technical support policies and limitations for AKS engine on Azure Stack Hub. The article also details third-party open-source components, and security or patch management. 

## Self-managed Kubernetes clusters on Azure Stack Hub with AKS engine

Infrastructure as a service (IaaS) cloud components, such as compute or networking components, give users access to low-level controls and customization options. AKS engine allows the user to laydown Kubernetes clusters utilizing these IaaS components transparently, users can access and affect all aspects of their deployments.

When a cluster is created, the customer defines the Kubernetes masters and worker nodes that AKS engine creates. Customer workloads are executed on these nodes. Customers own and can view or modify the master and worker nodes. Carelessly modified nodes can cause losses of data and workloads and can render the cluster non-functional. Also, AKS engine operations such as Upgrade or Scale will overwrite any out-of-bound changes. For example, if the cluster has static pods these will not be preserved after an AKS engine upgrade operation.

Because customer cluster nodes execute private code and store sensitive data, Microsoft Support can access them in only a limited way. Microsoft Support can't sign in to, execute commands in, or view logs for these nodes without express customer permission or assistance.

## AKS engine supported areas

Microsoft provides technical support for the following:

-  Issues with AKS engine commands: deploy, generate, upgrade, and scale. The tool should be consistent with its behavior on Azure.
-  Issues with a Kubernetes cluster deployed following the [Overview of the AKS engine](azure-stack-kubernetes-aks-engine-overview.md).
-  Issues with connectivity to other Azure Stack Hub services 
-  Issues with Kubernetes API connectivity
-  Issues with Azure Stack Hub Kubernetes provider functionality and connectivity with Azure Resource Manager
-  Issues with the AKS engine-generated configuration of Azure Stack Hub native artifacts such as Load Balancers, Network Security Groups,  VNETs, Subnets, Network Interfaces, Route table, Availability sets, Public IP addresses, Storage account, and VM Machines 
-  Issues with network performance and latency
-  Issues with the AKS base image used by the AKS engine in disconnected deployments. 

## AKS engine areas not supported

Microsoft does not provide technical support for the following:

-  Using the AKS engine on Azure.
-  Using the following AKS engine cluster definition options and addons.
    -  Not supported addons:  
            -  AAD Pod Identity  
            -  ACI Connector  
            -  Blobfuse Flex Volume  
            -  Cluster Autoscaler  
            -  Container Monitoring  
            -  KeyVault Flex Volume  
            -  NVIDIA Device Plugin  
            -  Rescheduler  
            -  SMB Flex Volume  
        
    -  Not supported cluster definition options:  
            -  Under KubernetesConfig:  
                    -  cloudControllerManagerConfig  
                    -  enableDataEncryptionAtRest  
                    -  enableEncryptionWithExternalKms  
                    -  enablePodSecurityPolicy  
                    -  etcdEncryptionKey  
                    -  useInstanceMetadata  
                    -  useManagedIdentity  
                    -  azureCNIURLLinux  
                    -  azureCNIURLWindows  
            -  Under masterProfile:  
                    -  availabilityZones  
            -  Under agentPoolProfiles:  
                    -  availabilityZones  
                    -  singlePlacementGroup  
                    -  scaleSetPriority  
                    -  scaleSetEvictionPolicy  
                    -  acceleratedNetworkingEnabled  
                    -  acceleratedNetworkingEnabledWindows

-  Kubernetes configuration changes persisted outside the Kubernetes configuration store etcd. For example, static pods running in nodes of the cluster.
-  Questions about how to use Kubernetes. For example, Microsoft Support doesn't provide advice on how to create custom ingress controllers, use application workloads, or apply third-party or open-source software packages or tools.
-  Third-party open-source projects that aren't provided as part of the Kubernetes cluster deployed by AKS engine. These projects might include Kubeadm, Kubespray, Native, Istio, Helm, Envoy, or others.
-  Using the AKS engine in use-case scenarios outside the ones specified in [Supported scenarios with the AKS engine](azure-stack-kubernetes-aks-engine-overview.md#supported-scenarios-with-the-aks-engine).
-  Third-party software. This software can include security scanning tools and networking devices or software.
-  Issues about multicloud or multivendor build-outs. For example, Microsoft doesn't support issues related to running a federated multipublic cloud vendor solution.
-  Network customizations other than those listed in the [AKS engine supported areas](#aks-engine-supported-areas) section.

##  Security issues and patching

If a security flaw is found in one or more components of AKS engine or Kubernetes provider for Azure Stack Hub, Microsoft will make available a patch for customers to patch affected clusters to mitigate the issue. Alternatively, the team will give users upgrade guidance. Notice that patches may require downtime of the cluster. When reboots are required, Microsoft will notify the customers of this requirement. If users don't apply the patches according to Microsoft guidance, their cluster will continue to be vulnerable to the security issue.

## Preview features

For features and functionality that requires extended testing and user feedback, Microsoft releases new preview features or features behind a feature flag. Consider these features as prerelease or beta features. 
Preview features or feature-flag features aren't meant for production. Ongoing functionality changes and behavior, bug fixes, and other changes can result in unstable clusters and downtime. These features are not supported by Microsoft.

## Next steps

- Read about the [The AKS engine on Azure Stack Hub](azure-stack-kubernetes-aks-engine-overview.md)
