Refer to [Create an AI-optimized GKE cluster with default configuration](https://cloud.google.com/ai-hypercomputer/docs/create/gke-ai-hypercompute#use-cluster-toolkit) for instructions on creating the GKE-A4 cluster.

Refer to [Deploy and run NCCL test with Topology Aware Scheduling (TAS)](https://cloud.google.com/ai-hypercomputer/docs/create/gke-ai-hypercompute#deploy-run-nccl-tas-test) for instructions on running a NCCL test on the GKE-A4 cluster.

## Using Spot VMs

You can easily deploy Spot VMs for the A4 node pool by modifying the `spot` variable. When `spot: true` is configured, any reservation settings are ignored, and the nodes will be provisioned using discounted Spot pricing.

To deploy with Spot VMs, set the `spot` variable in `gke-a4.yaml` to `true`:

```yaml
  spot: true
```

### Testing

To test this change, you can deploy the cluster with different configurations:
1. **With Spot VMs:** Set `spot: true` in your configuration. Deploy the cluster and verify in the Google Cloud Console or via `kubectl get nodes` that the A4 node pool uses Spot VMs (e.g., checking for the `cloud.google.com/gke-spot=true` label on the nodes).
2. **Without Spot VMs (Default):** Set `spot: false` (or leave it as the default) and ensure your `reservation` is configured correctly. Deploy the cluster and verify the nodes are provisioned using the standard configuration with the specified reservation.
