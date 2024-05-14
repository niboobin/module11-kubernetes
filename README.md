# Reflection 1

## Application Logs

When an app is exposed as a service and it is accessed multiple times, there will be an increase of logs because each request to the app is logged.

## Two versions of `kubectl get`

The `-n` option in `kubectl get` is used to specify the namespace in which to look for resources.

# Reflection 2

## Rolling Update and Recreate

Rolling update is When you update a deployment, the deployment gradually replaces pods of the old version with pods of the new version. If a deployment is updated mid-way, the deployment pauses and can be resumed later. This ensures zero downtime during application updates, as new pods are scheduled on nodes with available resources.

Recreate is a another deployment strategy where all existing pods are killed before new ones are created. he downside of this approach is that it causes downtime during the deployment until the new pods are up and running.

## Deployment using Recreate deployment strategy

1. Get the latest version of the object:

    ```
    kubectl get deployment spring-petclinic-rest -o yaml > deployment.yaml
    ```

2. Make changes to the `deployment.yaml` file by changing the strategy to `Recreate`

    ```
    strategy:
        type: Recreate
    ```

3. Apply the updated manifest file:

    ```
    kubectl apply -f deployment.yaml
    ```

## Benefits of using kubernetes manifest files

Manifest files allow you to define your desired state of resources, and Kubernetes works to maintain this state. Manifest files can be stored in a version control system like Git. Once you've defined a manifest file, it can be used to create identical resources across different environments.