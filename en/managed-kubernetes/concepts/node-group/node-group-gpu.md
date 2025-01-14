# Node groups with GPUs

You can create node groups with graphics accelerators (GPUs) in {{ k8s }} clusters. A node is created from an image of a GPU-compatible VM with NVIDIA drivers and [CUDA libraries](https://developer.nvidia.com/gpu-accelerated-libraries) installed for GPU acceleration.

## Requirements {#requirements}

* A non-zero GPU quota.

  By default, the cloud has a [zero quota]({{ link-console-quotas }}) for using VMs with GPUs. To change the quota, contact [technical support]({{ link-console-support }}).
* The cluster is in the `{{ region-id }}-a` and `{{ region-id }}-b` [availability zones](../../../overview/concepts/geo-scope.md), where VMs with GPUs are available.

  When requesting a GPU quota, keep in mind which zones you're going to run your {{ k8s }} clusters in.

## Pricing {#pricing}

To run node groups with GPUs, you need a {{ k8s }} cluster, a VM with a GPU, and traffic. Therefore, billing consists of the following parts:
* Using a {{ k8s }} master is charged according to the [{{ managed-k8s-name }} pricing policy](../../pricing.md).
* VM with a GPU — according to the [{{ compute-full-name }} pricing policy](../../../compute/pricing.md#prices-instance-resources).
* Outgoing traffic — according to the [{{ vpc-full-name }} pricing policy](../../../vpc/pricing.md).