## Setup Instructions

### 1. Clone the Repository
```sh
git clone https://github.com/your-username/3_tier_jenkins_project.git
cd 3_tier_jenkins_project
```
- `git clone`: Downloads the repository from GitHub.
- `cd 3_tier_jenkins_project`: Navigates into the project directory.

### 2. Deploy Kubernetes Manifests
Apply all Kubernetes YAML files in the `k8s-manifests/` directory:
```sh
kubectl apply -f k8s-manifests/
```
- `kubectl apply -f`: Deploys Kubernetes resources defined in YAML files.

### 3. Verify Deployment
Check the status of the pods and services:
```sh
kubectl get pods
kubectl get svc
```
- `kubectl get pods`: Lists running pods.
- `kubectl get svc`: Shows the services and their exposed ports.

### 4. Access the Application
Find the **LoadBalancer** or **NodePort** service to access the frontend:
```sh
kubectl get svc frontend-service
```
If using **Minikube**, run:
```sh
minikube service frontend-service
```
- `minikube service frontend-service`: Opens the frontend service in a browser.

## Install Git and VS Code on Windows

### 1. Install Git
1. Download Git from [git-scm.com](https://git-scm.com/).
2. Run the installer and select the default options.
3. After installation, verify with:
   ```sh
   git --version
   ```
   - This checks if Git is installed and displays the version.

### 2. Configure Git User Details
```sh
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```
- `git config --global user.name`: Sets the Git username.
- `git config --global user.email`: Sets the Git email address.

### 3. Install VS Code
1. Download VS Code from [code.visualstudio.com](https://code.visualstudio.com/).
2. Run the installer and follow the setup instructions.
3. Open VS Code and install the Git extension if needed.

### 4. Verify Git Integration in VS Code
- Open VS Code and navigate to `View` > `Source Control`.
- If Git is installed correctly, it will detect your repository.
- You can now commit and push changes directly from VS Code
