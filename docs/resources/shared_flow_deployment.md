# Resource: apigee_shared_flow_deployment
Represents a shared flow's deployment to an environment
## Example usage
```hcl
resource "apigee_shared_flow" "example" {
  name = "ShawnTestFlow"
  bundle = "sharedflows/ShawnTestFlow/ShawnTestFlow.zip"
  bundle_hash = filebase64sha256("sharedflows/ShawnTestFlow/ShawnTestFlow.zip")
}
resource "apigee_shared_flow_deployment" "exampleDeployment" {
  shared_flow_name = apigee_shared_flow.MySharedFlow.name
  environment_name = "dev"
  revision = apigee_shared_flow.MySharedFlow.revision
}
```
## Argument Reference
* `shared_flow_name` - **(Required, ForceNew, String)** The name of the shared_flow to be deployed.
* `environment_name` - **(Required, ForceNew, String)** The environment to deploy the shared_flow to.
* `revision` - **(Required, Integer)** The revision of the shared_flow to deploy.  On create, it will assume the shared_flow has not been deployed in the given environment yet.  On update, it will override any current deployment to the given environment.
* `delay` - **(Optional, Integer)** Time interval, in seconds, to wait before undeploying the currently deployed revision.  Default: 0. Ignored for calculating diffs.
## Attribute Reference
* `id` - Same as `environment_name`:`shared_flow_name`
## Import
Proxy deployments can be imported using a proper value of `id` as described above