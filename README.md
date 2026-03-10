# Learn Kubernetes

Kubernetes config used for the [Learn Kubernetes](https://www.boot.dev/courses/learn-kubernetes) course on [boot.dev](https://www.boot.dev)

## Install Prerequisites

- [Docker Desktop](https://docs.docker.com/desktop/) or [Docker Engine](https://docs.docker.com/engine/install/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)

### Verify Installation

```bash
# Docker
docker version

# Kubectl (Ignore errors about the server)
kubectl version

# Minikube
minikube version
```

### Command Completion

#### Debian/Ubuntu Bash Completions Summary

```bash
# Install bash-completion
sudo apt install bash-completion

# Enable bash-completion in ~/.bashrc
cat <<EOT >> ~/.bashrc
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
EOT

# Create directory for completions
mkdir -p ~/.local/share/bash-completion/completions

# Create the completion files
docker completion bash > ~/.local/share/bash-completion/completions/docker
kubectl completion bash > ~/.local/share/bash-completion/completions/kubectl
minikube completion bash > ~/.local/share/bash-completion/completions/minikube

# Reload the profile
source ~/.bashrc
```

#### Detailed Instructions

- [docker completion](https://docs.docker.com/engine/cli/completion/)
- [kubectl completion](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_completion/)
- [minikube completion](https://minikube.sigs.k8s.io/docs/commands/completion/)

## Run Minikube

NOTE: Make sure Docker is running before starting Minikube

```bash
# Start Minikube
minikube start --extra-config="apiserver.cors-allowed-origins=['http://boot.dev']"

# Open a tunnel
minikube tunnel --bind-address="127.0.0.1" -c
```