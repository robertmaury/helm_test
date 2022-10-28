# Helm charts for deploying accurics-cli-kubescanner


1.  Setup.

	Ensure to have a namespace to deploy the helm chart resources.
    It's recommended to create a new namespace.


2.  The helm chart creates a role to read all the resources across all namespaces.
    Feel free to edit `templates/role.yaml` if you wish to limit the read access.


3.  Deploy.
    ```
    helm install <release-name> . -n <namespace>
    ```

    The default container image is targeted for AMD64 architecture. 
    For ARM64 arch targeted container image, use:

    ```
    helm install <release-name> . -n <namespace> --set accurics.image=docker.io/accurics/cli-kubescan-arm64:1.0.41
    ```
 
    You can override the default cpu and memory request and limit values of the kubescanner pod like below:

    ```
    helm install <release-name> . -n <namespace> --set accurics.cpu.request=10m accurics.memory.request=50Mi accurics.cpu.limit=500m accurics.memory.limit=500Mi
    ```

    You can also use flags like `--wait` `--wait-for-jobs` `--timeout` as per preference.

4.  Clean up. 
    ```
    helm uninstall <release-name> -n <namespace>
    ```

That's it! Now you can view your scan results on Accurics Platform.

© 2021 Accurics, Inc. All rights reserved
