# cncf-crossplane

## Steps for a working setup

### 1 - Install via Winget

```
C:\work.0\cncf-crossplane>winget -v
v1.12.350
```
### 2 - Install K8s.Kubectl

```
C:\work.0\cncf-crossplane>winget install Kubernetes.kubectl
The `msstore` source requires that you view the following agreements before using.
Terms of Transaction: https://aka.ms/microsoft-store-terms-of-transaction
The source requires the current machine's 2-letter geographic region to be sent to the backend service to function properly (ex. "US").

Do you agree to all the source agreements terms?
[Y] Yes  [N] No: Y
Found Kubernetes CLI [Kubernetes.kubectl] Version 1.34.2
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://dl.k8s.io/release/v1.34.2/bin/windows/amd64/kubectl.exe
  ██████████████████████████████  59.2 MB / 59.2 MB
Successfully verified installer hash
Starting package install...
Path environment variable modified; restart your shell to use the new value.
Command line alias added: "kubectl"
Successfully installed
```
### 3 - Install Minikube

```
C:\work.0\cncf-crossplane>winget install Minikube.Minikube
No package found matching input criteria.

C:\work.0\cncf-crossplane>winget install Kubernetes.minikube
Found Kubernetes - Minikube - A Local Kubernetes Development Environment [Kubernetes.minikube] Version 1.37.0
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://github.com/kubernetes/minikube/releases/download/v1.37.0/minikube-installer.exe
  ██████████████████████████████  51.2 MB / 51.2 MB
Successfully verified installer hash
Starting package install...
Successfully installed
```
### Check status
```
C:\work.0\cncf-crossplane>minikube status
🤷  Profile "minikube" not found. Run "minikube profile list" to view all profiles.
👉  To start a cluster, run: "minikube start"
```
### 4 - Install Kubernetes.kubectl

```
C:\work.0\cncf-crossplane>winget install Kubernetes.kubectl
Found an existing package already installed. Trying to upgrade the installed package...
No available upgrade found.
No newer package versions are available from the configured sources.
```

### 5 - Install Helm

```
C:\work.0\cncf-crossplane>winget install Helm.Helm
Found Helm [Helm.Helm] Version 4.0.1
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://get.helm.sh/helm-v4.0.1-windows-amd64.zip
  ██████████████████████████████  19.4 MB / 19.4 MB
Successfully verified installer hash
Extracting archive...
Successfully extracted archive
Starting package install...
Path environment variable modified; restart your shell to use the new value.
Command line alias added: "helm"
Successfully installed
```

### 6 - Check kubectl

```
C:\work.0\cncf-crossplane>kubectl
kubectl controls the Kubernetes cluster manager.

 Find more information at: https://kubernetes.io/docs/reference/kubectl/

Basic Commands (Beginner):
  create          Create a resource from a file or from stdin
  expose          Take a replication controller, service, deployment or pod and expose it as a new Kubernetes service
  run             Run a particular image on the cluster
  set             Set specific features on objects
...
```


### 7 - Check Helm

```
C:\work.0\cncf-crossplane>helm
The Kubernetes package manager

Common actions for Helm:

- helm search:    search for charts
- helm pull:      download a chart to your local directory to view
- helm install:   upload the chart to Kubernetes
- helm list:      list releases of charts
```


### 8 - Start Minikube
Start Minikube by running: > minikube start
Minikube will automatically select the preferred driver available on your system. 

```
C:\work.0\cncf-crossplane>minikube version
minikube version: v1.37.0
commit: 65318f4cfff9c12cc87ec9eb8f4cdd57b25047f3
```
```
C:\work.0\cncf-crossplane>minikube start
😄  minikube v1.37.0 on Microsoft Windows 11 Home 10.0.26100.7171 Build 26100.7171
✨  Automatically selected the virtualbox driver
💿  Downloading VM boot image ...
    > minikube-v1.37.0-amd64.iso....:  65 B / 65 B [---------] 100.00% ? p/s 0s
    > minikube-v1.37.0-amd64.iso:  370.78 MiB / 370.78 MiB  100.00% 10.98 MiB p
👍  Starting "minikube" primary control-plane node in "minikube" cluster
💾  Downloading Kubernetes v1.34.0 preload ...
    > preloaded-images-k8s-v18-v1...:  337.07 MiB / 337.07 MiB  100.00% 10.97 M
🔥  Creating virtualbox VM (CPUs=2, Memory=4000MB, Disk=20000MB) ...
🤦  StartHost failed, but will try again: creating host: create: precreate: This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
🔥  Creating virtualbox VM (CPUs=2, Memory=4000MB, Disk=20000MB) ...
😿  Failed to start virtualbox VM. Running "minikube delete" may fix it: creating host: create: precreate: This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory

❌  Exiting due to HOST_VIRT_UNAVAILABLE: Failed to start host: creating host: create: precreate: This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
💡  Suggestion: Virtualization support is disabled on your computer. If you are running minikube within a VM, try '--driver=docker'. Otherwise, consult your systems BIOS manual for how to enable virtualization.
🍿  Related issues:
    ▪ https://github.com/kubernetes/minikube/issues/3900
    ▪ https://github.com/kubernetes/minikube/issues/4730
```
#### Set driver as Docker
```
C:\work.0\cncf-crossplane>minikube start --driver=docker
😄  minikube v1.37.0 on Microsoft Windows 11 Home 10.0.26100.7171 Build 26100.7171
E1205 23:57:35.403544   17404 start.go:829] api.Load failed for minikube: filestore "minikube": Docker machine "minikube" does not exist. Use "docker-machine ls" to list machines. Use "docker-machine create" to add a new one.

💢  Exiting due to GUEST_DRIVER_MISMATCH: The existing "minikube" cluster was created using the "virtualbox" driver, which is incompatible with requested "docker" driver.
💡  Suggestion: Delete the existing 'minikube' cluster using: 'minikube delete', or start the existing 'minikube' cluster using: 'minikube start --driver=virtualbox'

```
#### Minikube delete

```
C:\work.0\cncf-crossplane>minikube delete
🔥  Deleting "minikube" in virtualbox ...
❌  Failed to delete cluster: api remove: remove C:\Users\singh\.minikube\machines\minikube\minikube\Logs\VBoxHardening.log: The process cannot access the file because it is being used by another process.
📌  You may need to manually remove the "minikube" VM from your hypervisor
🔥  Removing C:\Users\singh\.minikube\machines\minikube ...

❌  Exiting due to GUEST_FILE_IN_USE: remove C:\Users\singh\.minikube\machines\minikube\minikube\Logs\VBoxHardening.log: The process cannot access the file because it is being used by another process.
💡  Suggestion: Another program is using a file required by minikube. If you are using Hyper-V, try stopping the minikube VM from within the Hyper-V manager
📘  Documentation: https://minikube.sigs.k8s.io/docs/reference/drivers/hyperv/
🍿  Related issue: https://github.com/kubernetes/minikube/issues/7300

```

### 9 - Install and Start Docker
#### Install Docker Desktop for windows x86_64 [Docker Desktop Installer.exe]

```
C:\work.0\cncf-crossplane>docker version
Client:
 Version:           29.1.2
 API version:       1.52
 Go version:        go1.25.5
 Git commit:        890dcca
 Built:             Tue Dec  2 21:57:33 2025
 OS/Arch:           windows/amd64
 Context:           desktop-linux
failed to connect to the docker API at npipe:////./pipe/dockerDesktopLinuxEngine; check if the path is correct and if the daemon is running: open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.
```
####  Start docker desktop and also do the register/login on docker-desktop application
```
C:\work.0\cncf-crossplane>minikube start --driver=docker
😄  minikube v1.37.0 on Microsoft Windows 11 Home 10.0.26100.7171 Build 26100.7171
✨  Using the docker driver based on user configuration
📌  Using Docker Desktop driver with root privileges
👍  Starting "minikube" primary control-plane node in "minikube" cluster
🚜  Pulling base image v0.0.48 ...
    > gcr.io/k8s-minikube/kicbase...:  488.52 MiB / 488.52 MiB  100.00% 9.37 Mi
🔥  Creating docker container (CPUs=2, Memory=4000MB) ...
❗  Failing to connect to https://registry.k8s.io/ from inside the minikube container
💡  To pull new external images, you may need to configure a proxy: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/
🐳  Preparing Kubernetes v1.34.0 on Docker 28.4.0 ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

### 10 - Check Minikube / local pods

```
C:\work.0\cncf-crossplane>kubectl get pods -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS     AGE
kube-system   coredns-66bc5c9577-89j5q           1/1     Running   0            30s
kube-system   etcd-minikube                      1/1     Running   0            36s
kube-system   kube-apiserver-minikube            1/1     Running   0            38s
kube-system   kube-controller-manager-minikube   1/1     Running   0            37s
kube-system   kube-proxy-jwmpr                   1/1     Running   0            30s
kube-system   kube-scheduler-minikube            1/1     Running   0            37s
kube-system   storage-provisioner                1/1     Running   1 (9s ago)   34s
```

```
C:\work.0\cncf-crossplane>kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   63s   v1.34.0
```
```
C:\work.0\cncf-crossplane>minikube config set driver docker
❗  These changes will take effect upon a minikube delete and then a minikube start
```

### 11 - Install Crossplane
#### We will use Helm to install Crossplane into your Minikube cluster.
```
C:\work.0\cncf-crossplane>kubectl create namespace crossplane-system
namespace/crossplane-system created

C:\work.0\cncf-crossplane>helm repo add crossplane-stable https://charts.crossplane.io/stable
"crossplane-stable" has been added to your repositories

C:\work.0\cncf-crossplane>helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "crossplane-stable" chart repository
Update Complete. ⎈Happy Helming!⎈


C:\work.0\cncf-crossplane>helm install crossplane --namespace crossplane-system crossplane-stable/crossplane
level=WARN msg="unable to find exact version; falling back to closest available version" chart=crossplane requested="" selected=2.1.3
NAME: crossplane
LAST DEPLOYED: Sat Dec  6 00:29:56 2025
NAMESPACE: crossplane-system
STATUS: deployed
REVISION: 1
DESCRIPTION: Install complete
TEST SUITE: None
NOTES:
Release: crossplane

Chart Name: crossplane
Chart Description: Crossplane is an open source Kubernetes add-on that enables platform teams to assemble infrastructure from multiple vendors, and expose higher level self-service APIs for application teams to consume.
Chart Version: 2.1.3
Chart Application Version: 2.1.3

Kube Version: v1.34.0
```



### 12 - Check Crossplane setup

```
C:\work.0\cncf-crossplane>kubectl get pods -n crossplane-system
NAME                                       READY   STATUS    RESTARTS   AGE
crossplane-5f6cd547ff-mn6qg                1/1     Running   0          3m47s
crossplane-rbac-manager-6d7d5844bd-ggr55   1/1     Running   0          3m47s
```


### 13 - Install GCP CLI 
#### Install GoogleCloudSDKInstaller.exe for GCP CLI > gcloud commands from https://docs.cloud.google.com/sdk/docs/install-sdk

```
C:\work.0\cncf-crossplane>gcloud init
Welcome! This command will take you through the configuration of gcloud.

Settings from your current configuration [default] are:
accessibility:
  screen_reader: 'False'
core:
  account: xx@yy.com
  disable_usage_reporting: 'True'

Pick configuration to use:
 [1] Re-initialize this configuration [default] with new settings
 [2] Create a new configuration
Please enter your numeric choice:  1

Your current configuration has been set to: [default]

You can skip diagnostics next time by using the following flag:
  gcloud init --skip-diagnostics

Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

Choose the account you want to use for this configuration.
To use a federated user account, exit this command and sign in to the gcloud CLI with your login configuration file, then run this command again.

Select an account:
 [1] xx@yy.com
 [2] Sign in with a new Google Account
 [3] Skip this step
Please enter your numeric choice:  1

You are signed in as: [xx@yy.com].

Pick cloud project to use:
 [1] covid19admin-278106
 [2] gen-lang-client-0046644228
 [3] gen-lang-client-0700953879
 [4] project-tracker-1111
 [5] reactapp-1579137965005
 [6] sampleapp-3e8a3
 [7] Enter a project ID
 [8] Create a new project
Please enter numeric choice or text value (must exactly match list item):  8

Enter a Project ID. Note that a Project ID CANNOT be changed later.
Project IDs must be 6-30 characters (lowercase ASCII, digits, or
hyphens) in length and start with a lowercase letter. cncf-crossplane
Waiting for [operations/create_project.global.] to finish...done.
Your current project has been set to: [cncf-crossplane].

Not setting default zone/region (this feature makes it easier to use
[gcloud compute] by setting an appropriate default value for the
--zone and --region flag).
See https://cloud.google.com/compute/docs/gcloud-compute section on how to set
default compute region and zone manually. If you would like [gcloud init] to be
able to do this for you the next time you run it, make sure the
Compute Engine API is enabled for your project on the
https://console.developers.google.com/apis page.

Error creating a default .boto configuration file. Please run [gsutil config -n] if you would like to create this file.
The Google Cloud CLI is configured and ready to use!

* Commands that require authentication will use xx@yy.com by default
* Commands will reference project `cncf-crossplane` by default
Run `gcloud help config` to learn how to change individual settings

This gcloud configuration is called [default]. You can create additional configurations if you work with multiple accounts and/or projects.
Run `gcloud topic configurations` to learn more.

Some things to try next:

* Run `gcloud --help` to see the Cloud Platform services you can interact with. And run `gcloud help COMMAND` to get help on any gcloud command.
* Run `gcloud topic --help` to learn about advanced features of the CLI like arg files and output formatting
* Run `gcloud cheat-sheet` to see a roster of go-to `gcloud` commands.
```

Access dashboard at https://console.cloud.google.com/home/dashboard?hl=en&project=cncf-crossplane


### 14 - Configure GCP

```
# Set your project ID
export PROJECT_ID=cncf-crossplane

# 1. Enable necessary APIs
gcloud services enable compute.googleapis.com container.googleapis.com storage.googleapis.com --project $PROJECT_ID

# 2. Create Service Account
gcloud iam service-accounts create crossplane-sa --display-name "Crossplane Provider" --project $PROJECT_ID

# 3. Grant 'Editor' role (Use granular roles like storage.admin in production)
gcloud projects add-iam-policy-binding $PROJECT_ID \
  --member "serviceAccount:crossplane-sa@$PROJECT_ID.iam.gserviceaccount.com" --role "roles/editor"

# 4. Generate the JSON key file
gcloud iam service-accounts keys create gcp-credentials.json --iam-account crossplane-sa@$PROJECT_ID.iam.gserviceaccount.com
```


### 15 - Create secret

```
C:\work.0\cncf-crossplane>kubectl create secret generic gcp-secret --from-file=creds=gcp-credentials.json -n crossplane-system
secret/gcp-secret created
```

### 16 - Install GCP Provider
```
# Create a file named provider-gcp.yaml:
apiVersion: pkg.crossplane.io/v1
kind: Provider
metadata:
  name: provider-gcp-storage
spec:
  # Installing the storage family for a lightweight test
  package: xpkg.upbound.io/upbound/provider-gcp-storage:v1.0.0
```
#### Apply it
```
C:\work.0\cncf-crossplane>kubectl apply -f provider-gcp.yaml
provider.pkg.crossplane.io/provider-gcp-storage created
```
### 17 - Configure the Provider
```
#Create a file named provider-config.yaml. Replace YOUR_PROJECT_ID with your actual Project ID.
apiVersion: gcp.upbound.io/v1beta1
kind: ProviderConfig
metadata:
  name: default
spec:
  projectID: YOUR_PROJECT_ID
  credentials:
    source: Secret
    secretRef:
      namespace: crossplane-system
      name: gcp-secret
      key: creds
```
#### Apply it
```
C:\work.0\cncf-crossplane>kubectl apply -f provider-config.yaml
providerconfig.gcp.upbound.io/default created
```


### 18 - Verify Success
Let's ask Crossplane to create a real Google Cloud Storage Bucket to prove it works.
```
#Create bucket.yaml:
apiVersion: storage.gcp.upbound.io/v1beta1
kind: Bucket
metadata:
  name: crossplane-minikube-demo-bucket
spec:
  forProvider:
    location: US
  providerConfigRef:
    name: default
```
#### Apply it
```
C:\work.0\cncf-crossplane>kubectl apply -f gcp-bucket.yaml
bucket.storage.gcp.upbound.io/crossplane-minikube-demo-bucket created
```
### 19 - Check GCP Status
Fetch buckets on local k8s  and also confirm on GCP Dashboard
```
C:\work.0\cncf-crossplane>kubectl get bucket
NAME                              READY   SYNCED   EXTERNAL-NAME                     AGE
crossplane-minikube-demo-bucket   True    True     crossplane-minikube-demo-bucket   73s
```

### 20 - List CRDs

```
C:\work.0\cncf-crossplane>kubectl get crd
NAME                                                            CREATED AT
bucketaccesscontrols.storage.gcp.upbound.io                     2025-12-05T19:44:21Z
bucketacls.storage.gcp.upbound.io                               2025-12-05T19:44:21Z
bucketiammembers.storage.gcp.upbound.io                         2025-12-05T19:44:21Z
bucketobjects.storage.gcp.upbound.io                            2025-12-05T19:44:21Z
buckets.storage.gcp.upbound.io                                  2025-12-05T19:44:21Z
clusterproviderconfigs.gcp.m.upbound.io                         2025-12-05T19:44:20Z
clusterusages.protection.crossplane.io                          2025-12-05T19:00:12Z
compositeresourcedefinitions.apiextensions.crossplane.io        2025-12-05T19:00:11Z
compositionrevisions.apiextensions.crossplane.io                2025-12-05T19:00:11Z
compositions.apiextensions.crossplane.io                        2025-12-05T19:00:11Z
configurationrevisions.pkg.crossplane.io                        2025-12-05T19:00:11Z
configurations.pkg.crossplane.io                                2025-12-05T19:00:11Z
cronoperations.ops.crossplane.io                                2025-12-05T19:00:11Z
defaultobjectaccesscontrols.storage.gcp.upbound.io              2025-12-05T19:44:21Z
defaultobjectacls.storage.gcp.upbound.io                        2025-12-05T19:44:21Z
deploymentruntimeconfigs.pkg.crossplane.io                      2025-12-05T19:00:11Z
environmentconfigs.apiextensions.crossplane.io                  2025-12-05T19:00:11Z
functionrevisions.pkg.crossplane.io                             2025-12-05T19:00:12Z
functions.pkg.crossplane.io                                     2025-12-05T19:00:12Z
imageconfigs.pkg.crossplane.io                                  2025-12-05T19:00:12Z
locks.pkg.crossplane.io                                         2025-12-05T19:00:12Z
managedresourceactivationpolicies.apiextensions.crossplane.io   2025-12-05T19:00:11Z
managedresourcedefinitions.apiextensions.crossplane.io          2025-12-05T19:00:11Z
notifications.storage.gcp.upbound.io                            2025-12-05T19:44:21Z
objectaccesscontrols.storage.gcp.upbound.io                     2025-12-05T19:44:20Z
objectacls.storage.gcp.upbound.io                               2025-12-05T19:44:20Z
operations.ops.crossplane.io                                    2025-12-05T19:00:11Z
providerconfigs.gcp.m.upbound.io                                2025-12-05T19:44:20Z
providerconfigs.gcp.upbound.io                                  2025-12-05T19:44:20Z
providerconfigusages.gcp.m.upbound.io                           2025-12-05T19:44:20Z
providerconfigusages.gcp.upbound.io                             2025-12-05T19:44:20Z
providerrevisions.pkg.crossplane.io                             2025-12-05T19:00:12Z
providers.pkg.crossplane.io                                     2025-12-05T19:00:12Z
usages.apiextensions.crossplane.io                              2025-12-05T19:00:11Z
usages.protection.crossplane.io                                 2025-12-05T19:00:12Z
watchoperations.ops.crossplane.io                               2025-12-05T19:00:11Z

C:\work.0\cncf-crossplane>

```
### 21 - Happy Crossplane
