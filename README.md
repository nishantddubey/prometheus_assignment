Issues That  Arised While Configuring Prometheus and Grafana in Kubernetes
 
    1. Invalid YAML Configuration for Prometheus or Grafana Deployment:
        ◦ Issue: Deployment failures or crash loops due to invalid YAML configuration files.
          
        ◦ Solution: Validate the YAML configuration files for syntax errors, indentation issues, and incorrect field values. Utilize commands like kubectl apply --dry-run=client -f <file.yaml> to check the validity of YAML files before applying them to the cluster. Correct any errors found in the configuration files.
          
    2. Container Image Pull Failures:
        ◦ Issue: Pods failing to start due to Kubernetes being unable to pull container images for Prometheus or Grafana.
          
        ◦ Solution: Check the availability of the specified container images in the designated container registry. Ensure that the registry is accessible and that the images are properly tagged and named.
       
    3. kubectl logs command issues:
        ◦ Issue: Unable to retrieve container logs using kubectl logs command.
          
        ◦ Solution: Verify the pod name and namespace, and ensure that the pod is running. Check the permissions and access rights of the user executing the command. If necessary, troubleshoot any networking or connectivity issues that may prevent access to pod logs.
          
    4. Missing NodePort in Prometheus Configuration:
        ◦ Issue: Unable to see metrics as NodePort is not specified in the target configuration of Prometheus.
          
        ◦ Solution: Add NodePort to the target configuration in the Prometheus YAML file to expose the metrics endpoint and allow access to Prometheus from outside the cluster. For example, specify the NodePort under the "targetPort" field in the Prometheus Service configuration.
    5. Metrics Collection Limitation to Node Metrics Only:
        ◦ Issue: Unable to collect metrics for the entire Kubernetes cluster, only obtaining node metrics using node-exporter.
        
        ◦ Solution: Deploy and configure additional components such as kube-state-metrics to gather metrics beyond just node-level metrics. 
        
                    ◦ kube-state-metrics provides insights into the state of various Kubernetes objects such as pods, deployments, and services, enabling comprehensive monitoring of the entire cluster. 
        
                    ◦ Install and configure kube-state-metrics to capture metrics for various Kubernetes objects like pods and deployments. Adjust Prometheus configuration to scrape kube-state-metrics endpoints alongside other targets for broader cluster monitoring
