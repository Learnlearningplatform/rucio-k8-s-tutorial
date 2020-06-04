# Setting up a Rucio Kubernetes environment

## Prerequisites

First, we have to clone this repo to our Local development environment. 

```
git clone https://github.com/tbeerman/rucio-k8s-tutorial.git
```
- After cloning now we will install `kubectl` which is a command line toll for controlling `Kubernetes` clusters. `kubectl` looks for a file names config in the `$HOME/...` For details about each command, including all the sopported falgs and subcommands, see the `kubectl` [reference documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/). To install `kubectl` visit on the [following link](https://kubernetes.io/docs/tasks/tools/install-kubectl/):

```
https://kubernetes.io/docs/tasks/tools/install-kubectl/
```

- Now we need of `helm` package manager for `Kubernetes`. `Helm` is a tool that streamlines installing and managing Kubernetes applications. We can think of it like Apt/Yum/Homebrew for `K8S`. `Helm` uses a packaging format called charts which is a collection of files that describe a related set of Kubernetes resources. To install `helm` use the [following link](https://helm.sh/docs/intro/install/)

```
https://helm.sh/docs/intro/install/
```

- Now, we will install `minikube` which is tool that will make us easy to run Kubernetes locally. `Minikube` will run a single-node cluster inside our provided Hypervisor on our laptop. There are different packages to install `minikube`. You can install according to your preference. To install `minikube` follow the [given link](https://kubernetes.io/docs/tasks/tools/install-minikube/):

```
https://kubernetes.io/docs/tasks/tools/install-minikube/

https://minikube.sigs.k8s.io/docs/start/
```
After installing `minikube` just confirm the installation`. To confirm successful installation of both a `hypervisor` and `minikube`, you can run the following command to start up a local cluster:

!!! Note
       For setting the `--driver` with `minikube start`, enter the name of `hypervisor` you instaled in lowercase letters where `<driver_name>` is mentioned below. A full list of `--driver` values is available in [specifying the driver documentation](https://kubernetes.io/docs/setup/learning-environment/minikube/#specifying-the-vm-driver).

```
minikube start --driver=<driver_name>
```

Once `minikube start` finishes, run the command below to check the status of the cluster:

```
minikube status
```

If your cluster is running, the output from `minikube status` should be similar to:

```
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

After you have confirmed whether whether `Minikube` is working with your chosen `hypervisor` , you can continue to use `Minikube` or you can stop your cluster. To stop your cluster, run:

```
minikube stop
```

- Start minikube with extra RAM to avoid insufficient memory issue:

```
minikube start --memory='4000mb'
```

- As in the previous steps we had installed `Helm`. Now we will add `Helm chart` repository that houses an index. yaml file and optionally some packaged charts. Follow the given command:

```
$ helm repo add stable https://kubernetes-charts.storage.googleapis.com/

$ helm repo add rucio https://rucio.github.io/helm-charts
```

Once this is installed, you will be able to list the charts you can install:

```
helm search repo stable
NAME                                    CHART VERSION   APP VERSION                     DESCRIPTION
stable/acs-engine-autoscaler            2.2.2           2.1.1                           DEPRECATED Scales worker nodes within agent pools
stable/aerospike                        0.2.8           v4.5.0.5                        A Helm chart for Aerospike in Kubernetes
stable/airflow                          4.1.0           1.10.4                          Airflow is a platform to programmatically autho...
stable/ambassador                       4.1.0           0.81.0                          A Helm chart for Datawire Ambassador
# ... and many more
```






