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



## Configure Git CLI and Push Code to GitHub

### 1. Install Git CLI
Download and install Git from [git-scm.com](https://git-scm.com/). 
After installation, verify with:
```sh
git --version
```
- `git --version`: Checks if Git is installed and displays the version.

### 2. Configure Git User Details
```sh
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```
- `git config --global user.name`: Sets the Git username.
- `git config --global user.email`: Sets the Git email address.

### 3. Initialize Git Repository
Navigate to your project folder:
```sh
cd path/to/3_tier_jenkins_project-main
```
Initialize Git:
```sh
git init
```
- `git init`: Creates a new Git repository in the project folder.

### 4. Add Remote Repository
Replace `your-username` with your GitHub username:
```sh
git remote add origin https://github.com/your-username/3_tier_jenkins_project.git
```
- `git remote add origin`: Links the local repository to GitHub.

Verify the remote:
```sh
git remote -v
```
- `git remote -v`: Displays the configured remote repository.

### 5. Add and Commit Files
```sh
git add .
git commit -m "Initial commit - Kubernetes manifests and project files"
```
- `git add .`: Adds all files to the staging area.
- `git commit -m`: Saves changes with a message.

### 6. Push to GitHub
Set the branch name to `main`:
```sh
git branch -M main
```
- `git branch -M main`: Renames the current branch to `main`.

Push the code:
```sh
git push -u origin main
```
- `git push -u origin main`: Pushes code to GitHub and sets upstream tracking.


