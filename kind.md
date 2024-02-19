# Kind

kind is a tool for running local Kubernetes clusters using Docker container “nodes”.
kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI.

# Why kind?

~~~
kind supports multi-node (including HA) clusters
kind supports building Kubernetes release builds from source
support for make / bash or docker, in addition to pre-published builds
kind supports Linux, macOS and Windows
kind is a CNCF certified conformant Kubernetes installer

~~~

**chocolatey to install kind**

With PowerShell, you must ensure Get-ExecutionPolicy is not Restricted. 

They suggested using Bypass to bypass the policy to get things installed or AllSigned for quite a bit more security.

Run Get-ExecutionPolicy. If it returns Restricted, then run Set-ExecutionPolicy AllSigned or Set-ExecutionPolicy Bypass -Scope Process.

~~~
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
~~~

**Install docker-compose kind kubectl kustomize kubectx tilt using Choco**
~~~
choco install docker-compose kind kubectl kustomize kubectx tilt
~~~


~~~
sudo apt update
    5  sudo apt-get install build-essential curl file git
    6  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    7  sudo chown -R sbaline /home/linuxbrew/.linuxbrew/Cellar
    8  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    9  ls -l /home/linuxbrew/.linuxbrew/
   10  sudo chgrp -R sbaline /home/linuxbrew/.linuxbrew/Cellar
   11  ls -l /home/linuxbrew/.linuxbrew/
   12  sudo chown -R sbaline /home/linuxbrew/.linuxbrew/Caskroom
   13  sudo chgrp -R sbaline /home/linuxbrew/.linuxbrew/Caskroom
   14  ls -l /home/linuxbrew/.linuxbrew/
   15  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   16  ls -l /home/linuxbrew/.linuxbrew/bin/
   17  which brew
   18  sudo chown -R sbaline /home/linuxbrew/.linuxbrew/Homebrew
   19  sudo chgrp -R sbaline /home/linuxbrew/.linuxbrew/Homebrew
   20  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   21  pwd
   22  ls -l /home/linuxbrew/.linuxbrew/Homebrew/completions/zsh/_brew
   23  ls -l /home/linuxbrew/.linuxbrew/share/zsh/site-functions/_brew
   24  sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   25  mv /home/linuxbrew/.linuxbrew /home/linuxbrew/.linuxbrew2
   26  sudo mv /home/linuxbrew/.linuxbrew /home/linuxbrew/.linuxbrew2
   27  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   28  sudo rm -rf /home/linuxbrew/.linuxbrew2
   29  which brew
   30  test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv)
   31  test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
   32  test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile
   33  echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.profile
   34  which brew
   35  brew install git
   36  brew install docker-compose kind kubectl kustomize kubectx argo tilt
~~~

# Prerequisites
1. Docker (Desktop)
2. Kubectl (installed through Docker Desktop)
3. Kind

# 1 Install Docker Desktop on Windows
Docker Desktop Installer.exe - We can get it from Docker Hub.

https://docs.docker.com/desktop/install/windows-install/

~~~
PowerShell - Start-Process 'Docker Desktop Installer.exe' -Wait install
Windows Command Prompt  - start /w "" "Docker Desktop Installer.exe" install
~~~

If your admin account is different to your user account, you must add the user to the docker-users group:
~~~
net localgroup docker-users <user> /add
~~~

The default Docker Desktop installation will use Hyper-V to run Linux containers. Hyper-V is only included in Windows 10 Pro, not in Windows 10 Home.

We can run Docker Desktop in Windows 10 home, by using the WSL2 backend. 

# Settings for Docker Desktop

We need a minimum of 6GB of RAM dedicated to the virtual machine (VM) running the Docker engine. 8GB is recommended.

# 2 Kubectl (installed through Docker Desktop)

https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/

@ Download the latest 1.27 patch release: kubectl 1.27.4.

Or if you have curl installed, use this command:

~~~
curl.exe -LO "https://dl.k8s.io/release/v1.27.4/bin/windows/amd64/kubectl.exe"
~~~

**Note**  : To find out the latest stable version (for example, for scripting), take a look at https://dl.k8s.io/release/stable.txt.

**Options** 
We can Install on Windows using Chocolatey, Scoop, or winget 

**1** 
Download the latest 1.27 patch release: kubectl 1.27.4.
Created one dir and move exe file and Then set Env variable path

# 3 Installing and using kind on Windows

**Installing With A Package Manager**

**chocolatey to install kind**

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))


This will install kind on our system. With that, either open a new window or run refreshenv.
~~~
choco install kind
~~~

# Installing From Release Binaries

On Windows in PowerShell
~~~
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.20.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
~~~


We can create a kind cluster using:
~~~
kind create cluster
~~~
# Configuring our kind Cluster
To specify a configuration file when creating a cluster, use the --config flag:
~~~
kind create cluster --config kind-example-config.yaml
~~~

# Multi-node clusters & Control-plane HA
multiple control-plane & Worker nodes
~~~
# a cluster with 3 control-plane nodes and 3 workers
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: control-plane
- role: worker
- role: worker
- role: worker
~~~

# Mapping ports to the host machine 
We can map extra ports from the nodes to the host machine with extraPortMappings:
~~~
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    listenAddress: "0.0.0.0" # Optional, defaults to "0.0.0.0"
    protocol: udp # Optional, defaults to tcp
~~~
This can be useful if using NodePort services or daemonsets exposing host ports.

Note: binding the listenAddress to 127.0.0.1 may affect your ability to access the service.

# Setting Kubernetes version

We can also set a specific Kubernetes version by setting the node’s container image. 
We can find available image tags on the releases page. Please use the sha256 shasum for your desired kubernetes version, as seen in this example:

~~~
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
- role: worker
  image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
~~~
# Enable Feature Gates in Your Cluster
Feature gates are a set of key=value pairs that describe alpha or experimental features. 

In order to enable a gate we have to customize our kubeadm configuration, and it will depend on what gate and component we want to enable. An example kind config can be:
~~~
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
featureGates:
  FeatureGateName: true
~~~
# Configure kind to use a proxy
If We are running kind in an environment that requires a proxy, we may need to configure kind to use it.

We can configure kind to use a proxy using one or more of the following environment variables (uppercase takes precedence):
~~~
HTTP_PROXY or http_proxy
HTTPS_PROXY or https_proxy
NO_PROXY or no_proxy
~~~
Note: ~~~
        If we set a proxy it would be passed along to everything in the kind nodes.
         kind will automatically append certain addresses into NO_PROXY before passing it to the nodes so that Kubernetes components connect to each other directly, 
         but we may need to configure additional addresses depending on our usage.
      ~~~

# Exporting Cluster Logs
kind has the ability to export all kind related logs for us to explore. To export all logs from the default cluster (context name kind):
~~~
kind export logs
Exported logs to: /tmp/396758314
~~~

Like all other commands, if we want to perform the action on a cluster with a different context name use the --name flag.

As we can see, kind placed all the logs for the cluster kind in a temporary directory. 
If we want to specify a location then simply add the path to the directory after the command:
 
~~~
kind export logs ./somedir
Exported logs to: ./somedir
~~~
   ***The structure of the logs will look more or less like this:***
   ~~~
    .
├── docker-info.txt
└── kind-control-plane/
    ├── containers
    ├── docker.log
    ├── inspect.json
    ├── journal.log
    ├── kubelet.log
    ├── kubernetes-version.txt
    └── pods/
   ~~~

The logs contain information about the Docker host, the containers running kind, the Kubernetes cluster itself, etc.



# Installing From Source

In addition to the pre-built binary + package manager installation options listed above we can install kind from source with go install sigs.k8s.io/kind@v0.20.0 or clone this repo and run make build from the repository.


# *** We can create two clusters:

~~~
kind create cluster # Default cluster context name is `kind`.
...
kind create cluster --name kind-2
~~~
# list your kind clusters
~~~
kind get clusters
kind
kind-2
~~~
# In order to interact with a specific cluster, you only need to specify the cluster name as a context in kubectl:

~~~
kubectl cluster-info --context kind-kind
kubectl cluster-info --context kind-kind-2
~~~
# Deleting a Cluster
If the flag --name is not specified, kind will use the default cluster context name kind and delete that cluster.
~~~
kind delete cluster
~~~

# Loading an Image Into Your Cluster

Docker images can be loaded into your cluster nodes with:
~~~
kind load docker-image my-custom-image-0 my-custom-image-1
~~~
 **Note** 
 ~~~
  Note: If using a named cluster you will need to specify the name of the cluster we wish to load the images into:
  kind load docker-image my-custom-image-0 my-custom-image-1 --name kind-2
 ~~~
 
# Additionally, image archives can be loaded with: kind load image-archive /my-image-archive.tar
This allows a workflow like:

~~~
docker build -t my-custom-image:unique-tag ./my-image-dir
kind load docker-image my-custom-image:unique-tag
kubectl apply -f my-manifest-using-my-image:unique-tag
~~~












