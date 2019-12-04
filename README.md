# ![Icon](./.bluemix/knative-logo_72px.png) Developing a Knative Service app

## How Knative deployment works
The application code is stored in source control, along with its Dockerfile and Knative service definition. If your app doesn't have a Knative service definition, the toolchain automatically generates one during deployment. The target cluster is configured during toolchain setup by using an IBM Cloud API key and cluster name. You can update them at any time by altering the Delivery Pipeline configuration. Any code changes detected in the Git repo are automatically built, validated, and deployed into the Kubernetes cluster.

![Icon](./.bluemix/toolchain.png)

## Creating a Knative Service app
You can continuously deliver a secure Knative Service container app to a Kubernetes Cluster. Learn how to create a "Hello World" application that uses Docker, Node.js, and a DevOps toolchain. The app comes preconfigured for continuous delivery with the following features:
* Vulnerability Advisor
* Source control
* Issue tracking
* Online editing
* Knative deployment to the IBM Kubernetes Service

## Prerequisites
* Depending on your [IBM Cloud account type](https://cloud.ibm.com/registration), access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities required by this toolchain might not be available.
* Install the [IBM Cloud CLI, the IBM Cloud Kubernetes Service plug-in, and the Kubernetes CLI](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install).
* Create a [standard Kubernetes cluster](https://cloud.ibm.com/kubernetes/catalog/cluster) with 3 worker nodes that each have 4 cores and 16 GB memory (b3c.4x16) or more. For more information, see [Creating a standard classic cluster in the console](https://cloud.ibm.com/docs/containers?topic=containers-clusters#clusters_ui). Ensure that you note the total monthly cost before you create the cluster.
* Install the [Istio add-on](https://cloud.ibm.com/docs/containers?topic=containers-istio).
* Install the [Knative add-on](https://cloud.ibm.com/docs/containers?topic=containers-serverless-apps-knative#knative-setup).

1. To get started, click **Create toolchain**:
<br> [![Create toolchain](https://cloud.ibm.com/devops/graphics/create_toolchain_button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Freedcozart%2Fknative-service-toolchain&env_id=ibm:yp:us-south)
2. You can use the default settings, or make changes as needed.
3. Under **Tool Integrations**, select **Delivery Pipeline**.
4. Enter your **IBM Cloud API key**, or generate a new API key by clicking **Create**.
5. Confirm the container registry region, container registry namespace, and cluster information.
6. Click **Create**.

The following best practices are implemented automatically upon app creation:
- Sanity check the Dockerfile before image creation.
- Build a container image on every Git commit, setting a tag based on build number, time stamp, and commit ID for traceability.
- Use a private image registry to store the image, and automatically configure access permissions for target cluster deployment by using API tokens that can be revoked.
- Check the container image for security vulnerabilities.
- Insert the image tag into the deployment manifest automatically.
- Use an explicit namespace in a cluster to insulate each deployment, which makes it easy to clear by running `kubectl delete namespace`.

---
## Learn more 

* [Continuously deliver your app to Kubernetes with Bluemix](https://www.ibm.com/blogs/bluemix/2017/07/continuously-deliver-your-app-to-kubernetes-with-bluemix/)
* [Deploying serverless apps with Knative](https://cloud.ibm.com/docs/containers?topic=containers-serverless-apps-knative)
* [Step-by-step "Develop a Kubernetes app" tutorial](https://www.ibm.com/devops/method/tutorials/tc_secure_kube)
* [Getting started with clusters](https://cloud.ibm.com/docs/containers?topic=containers-getting-started)
* [Getting started with toolchains](https://cloud.ibm.com/devops/getting-started)
* [Getting started with IBM Cloud Continuous Delivery](https://cloud.ibm.com/docs/services/ContinuousDelivery?topic=ContinuousDelivery-getting-started&pos=2)
