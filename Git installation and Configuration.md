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
