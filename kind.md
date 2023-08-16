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

We suggest using Bypass to bypass the policy to get things installed or AllSigned for quite a bit more security.

Run Get-ExecutionPolicy. If it returns Restricted, then run Set-ExecutionPolicy AllSigned or Set-ExecutionPolicy Bypass -Scope Process.

~~~
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
~~~

**Install docker-compose kind kubectl kustomize kubectx tilt using Choco**
~~~
choco install docker-compose kind kubectl kustomize kubectx tilt
~~~
