# tce-kcd-workshop

## Step 1: Install TCE

Latest TCE version as this writing is `v0.11.0`

Installation instructions:

- [TLDR; Manual installation](#tldr-manual-installation)
- [MacOS](#macos)
  - [Install with Homebrew](#install-with-homebrew-brew)
  - [Install with tar ball manually](#install-with-tar-ball-manually)
- [Linux](#linux)
  - [Install with Homebrew](#install-with-homebrew-brew-1)
  - [Install with tar ball manually](#install-with-tar-ball-manually-1)
- [Windows](#windows)
  - [Install with Chocolatey](#install-with-chocolatey)
  - [Install with zip manually](#install-with-zip-manually)

We are skipping installation from TCE source code as that takes quiet some time

### TLDR; Manual installation

Manual installation on Mac/Linux/Windows

- Download the [release tarball](https://github.com/vmware-tanzu/community-edition/releases/tag/v0.11.0) based on your operating system.
- Unpack the [release tarball](https://github.com/vmware-tanzu/community-edition/releases/tag/v0.11.0).
  - Unzip on Windows.
  - `tar zxvf <release-tarball-path>` on Mac/Linux.
  - Enter the directory of the unpacked release.
  - Run the install script.
    - `.\install.bat` on Windows as Administrator.
    - `./install.sh` on Mac/Linux

### MacOS

#### Install with Homebrew (`brew`)

[YouTube video reference](https://www.youtube.com/watch?v=idSTTVJhJ9Y)

Ensure [Homebrew](https://brew.sh/) is installed

```bash
brew install vmware-tanzu/tanzu/tanzu-community-edition

${HOMEBREW_EXEC_DIR}/configure-tce.sh
```

#### Install with tar ball manually

[YouTube video reference](https://www.youtube.com/watch?v=FEpZpAovSLE)

```bash
# download the tar ball with your favorite browser or something like wget or curl
wget https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-darwin-amd64-v0.11.0.tar.gz

# extract the tar ball using Finder or a CLI tool like tar
tar xvzf tce-darwin-amd64-v0.11.0.tar.gz

# cd into the extracted directory
cd tce-darwin-amd64-v0.11.0

# run install.sh
./install.sh
```

### Linux

#### Install with Homebrew (`brew`)

[YouTube video reference](https://www.youtube.com/watch?v=oweOlaquvDo)

Ensure [Homebrew](https://brew.sh/) is installed

```bash
brew install vmware-tanzu/tanzu/tanzu-community-edition

${HOMEBREW_EXEC_DIR}/configure-tce.sh
```

#### Install with tar ball manually

[YouTube video reference](https://www.youtube.com/watch?v=pa5cxhdOaz8)

```bash
# download the tar ball with your favorite browser or something like wget or curl
wget https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-linux-amd64-v0.11.0.tar.gz

# extract the tar ball using Finder or a CLI tool like tar
tar xvzf tce-linux-amd64-v0.11.0.tar.gz

# cd into the extracted directory
cd tce-linux-amd64-v0.11.0

# run install.sh
./install.sh
```

### Windows

#### Install with Chocolatey

```
choco install tanzu-community-edition --version 0.11.0
```

#### Install with zip manually

Download the zip with your favorite browser or something like `Invoke-WebRequest` or `wget` or `curl` etc

Link - https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-windows-amd64-v0.11.0.zip

```
$source = 'https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-windows-amd64-v0.11.0.zip'
$destination = '<destination-path>\tce-windows-amd64-v0.11.0.zip'
Invoke-WebRequest -Uri $source -OutFile $destination
```

Then extract the zip file using File explorer or something like `Expand-Archive`

```
Expand-Archive -LiteralPath "<destination-path>\tce-windows-amd64-v0.11.0.zip" -Destination '<destination-path-for-extracted-directory>'
```

Change directory into the extracted directory

```
cd <destination-path-for-extracted-directory>\tce-windows-amd64-v0.11.0
```

Run `install.bat` script

```
.\install.bat
```

## Step 2: Prep for installing Management Cluster

- Login to AWS Console
- Click on the profile name on top right
- Select `Security Credentials`

![AWS Security Credentials Button](images/aws-security-credentials.png)

- Create access key

![AWS Security Credentials Screen](images/aws-security-credentials-screen.png)

![Create Access Key popup](images/create-access-key-popup.png)

![Create Access Key popup with Secret](images/create-access-key-popup-with-secret.png)

- Run `aws configure` to configure your AWS credentials that you just got and also configure the default region. For example set region to something like `us-east-1`

```bash
$ aws configure
AWS Access Key ID [***************]:
AWS Secret Access Key [****************]:
Default region name [us-east-1]:
Default output format [None]:
```

Note: ⚠️ Here we assume that the AWS account's credentials has enough access to create a Kubernetes Cluster which means access to create different kinds of resources like - Cloud Formation Stacks, EC2 instances, Security Groups, Internet Gateways, Network Interfaces, Elastic Load Balancers (ELB), Virtual Private Cloud (VPC), Sub networks, Route Tables, NAT Gateways. We also assume that the AWS account has enough quota and available resources (based on current usage and quota) to create these resources for the Kubernetes Cluster

- Create a key pair in the region you want to create the cluster, for example `us-east-1`

![TCE AWS Install Prep for Key 1](images/tce-aws-install-prep-for-key-1.png)

![TCE AWS Install Prep for Key 2](images/tce-aws-install-prep-for-key-2.png)

![TCE AWS Install Prep for Key 3](images/tce-aws-install-prep-for-key-3.png)

![TCE AWS Install Prep for Key 4](images/tce-aws-install-prep-for-key-4.png)

## Step 3: Create the Management Cluster

We will be using the Kickstart Web UI to create our cluster

```bash
tanzu management-cluster create --ui
```

![TCE AWS Install 1](images/tce-aws-install-1.png)

![TCE AWS Install 2](images/tce-aws-install-2.png)

![TCE AWS Install 3](images/tce-aws-install-3.png)

![TCE AWS Install 4](images/tce-aws-install-4.png)

![TCE AWS Install 5](images/tce-aws-install-5.png)

![TCE AWS Install 6](images/tce-aws-install-6.png)

![TCE AWS Install 7](images/tce-aws-install-7.png)

![TCE AWS Install 8](images/tce-aws-install-8.png)

![TCE AWS Install 9](images/tce-aws-install-9.png)

![TCE AWS Install 10](images/tce-aws-install-10.png)

![TCE AWS Install 11](images/tce-aws-install-11.png)

![TCE AWS Install 12](images/tce-aws-install-12.png)

![TCE AWS Install 13](images/tce-aws-install-13.png)

![TCE AWS Install 14](images/tce-aws-install-14.png)

![TCE AWS Install 15](images/tce-aws-install-15.png)

![TCE AWS Install 16](images/tce-aws-install-16.png)

![TCE AWS Install 17](images/tce-aws-install-17.png)

![TCE AWS Install 18](images/tce-aws-install-18.png)

![TCE AWS Install 19](images/tce-aws-install-19.png)

![TCE AWS Install 20](images/tce-aws-install-20.png)

![TCE AWS Install 21](images/tce-aws-install-21.png)

![TCE AWS Install 22](images/tce-aws-install-22.png)

## Step 4: Get Management Cluster details

```
tanzu management-cluster get
```

It's kind of a wrapper around `clusterctl`

## Step 5: Get Management Cluster Admin Kubeconfig

```
tanzu management-cluster kubeconfig get --admin
```

## Step 6: Switch Kubernetes context to the Management Cluster in the Kubeconfig

```
kubectl config use-context tce-aws-demo-admin@tce-azure-demo
```

## Step 7: Connect to Management Cluster and check it out

```
kubectl version

kubectl get nodes

kubectl get pods -A
```

## Step 8: Checkout the AWS resources created for the Management Cluster in the AWS Console

## Step 9: Create Workload Cluster

```
tanzu cluster create tce-aws-demo-wkld -f <cluster-config-yaml-file>
```

An example cluster config yaml based on the above installation. We are using config similar to config used for management cluster with just the name changed

```yaml
AWS_PROFILE: default
CLUSTER_NAME: tce-aws-demo-wkld
AWS_AMI_ID: ami-04684ddd079ac3b6d
AWS_NODE_AZ: us-east-1a
AWS_PRIVATE_NODE_CIDR: 10.0.16.0/20
AWS_PUBLIC_NODE_CIDR: 10.0.0.0/20
AWS_REGION: us-east-1
AWS_VPC_CIDR: 10.0.0.0/16
BASTION_HOST_ENABLED: "true"
CLUSTER_CIDR: 100.96.0.0/11
CLUSTER_PLAN: dev
CONTROL_PLANE_MACHINE_TYPE: t2.2xlarge
ENABLE_CEIP_PARTICIPATION: "false"
ENABLE_MHC: "true"
IDENTITY_MANAGEMENT_TYPE: none
INFRASTRUCTURE_PROVIDER: aws
NODE_MACHINE_TYPE: t2.2xlarge
SERVICE_CIDR: 100.64.0.0/13
AWS_SSH_KEY_NAME: default
ENABLE_AUDIT_LOGGING: "true"
OS_ARCH: amd64
OS_NAME: ubuntu
OS_VERSION: "20.04"
```

## Step 10: Get Workload Cluster Admin Kubeconfig

```
tanzu cluster kubeconfig get tce-aws-demo-wkld --admin
```

## Step 11: Switch Kubernetes context to the Workload Cluster in the Kubeconfig

```
kubectl config use-context tce-aws-demo-wkld-admin@tce-aws-demo-wkld
```

## Step 12: Connect to Workload Cluster and check it out

```
kubectl version

kubectl get nodes

kubectl get pods -A
```

## Step 13: Checkout the AWS resources created for the Workload Cluster in the AWS Console
