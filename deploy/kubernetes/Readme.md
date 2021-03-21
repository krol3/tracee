# Deploy Tracee on Kubernetes

> NOTE `Minimal Requirements to run tracee in the node`
````
https://aquasecurity.github.io/tracee/install/prerequisites/
````

1. Create a ConfigMap that will hold the templates files for tracee-rules
 ``` bash
 kubectl create configmap tracee-templates --from-file=../../tracee-rules/templates
 ```

2. Create the Tracee deployment

 ``` bash
 kubectl create -f tracee.yaml
 ```

3. Create a configMap for the falcosidekick config file.
> NOTE `See the complete config file in` [falcosidekick](https://github.com/falcosecurity/falcosidekick)

 ``` bash
 kubectl create configmap webhook-config --from-file=cfg.yaml
 ```

4. Create the webhook deployment and service for the falcosidekick.

 ``` bash
 kubectl create -f webhook.yaml
 ```

> Get the service to integrate with tracee.  `kubectl get service`
````
https://webhook.default.svc.cluster.local:2801
````
