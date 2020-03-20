# Example-ms
Ideal micro service with basic structure and skeleton wrt `k8s/helm`

## Docker
`docker build . -f docker/Dockerfile -t localhost:5000/example-ms:master-latest`

##Helm chart
Helm charts details can be found at https://helm.sh/docs/intro/quickstart/

Prerequisites:
 * Docker installed and running; verify `docker version`
 * Kubectl installed https://kubernetes.io/docs/tasks/tools/install-kubectl/ ; verify `kubectl version`
 * Minikube installed and running https://kubernetes.io/docs/tasks/tools/install-minikube/; verify `minikube version`
 * Install/Run k8s dashboard; `minikube dashboard`
 * Running docker registry; refer Local docker registry section
 
Helm chart is found in `/charts` directory
To create helm chart `helm create exmaple-ms` in charts folder

Sanity check for charts:
 * Chart linting: `helm lint --strict ./charts/example-ms`
 * Dry installation of the chart: `helm upgrade --install --namespace hemant example-ms ./charts/example-ms --debug --dry-run`
 
## Local docker registry

   * `https://minikube.sigs.k8s.io/docs/tasks/registry/insecure/`
OR
   * `https://hasura.io/blog/sharing-a-local-registry-for-minikube-37c7240d0615/`, sample k8s deployment can be found dir /k8s/kube-registry.yml
    