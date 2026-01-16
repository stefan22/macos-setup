# 💻 macOS Dev Setup Script

A lightweight shell script for initial macOS development environment configuration. This script automates the installation of essential tools to get you up and running quickly.

<br />

## 📦 Core Tools

    😲 Homebrew: Package manager for macOS.

    😲 Oh My Zsh: Enhances your terminal with themes and plugins.

    😲 Git, NVM, Yarn, Commitizen, Starship, Firefox, Brave-browser, Calibre, Figma, ImageOptim, Hack-Nerd-Font


<br />    


## ⚙️ Installation

1. Create the file and paste the contents from `dev-setup-script.md`:

```bash
  sudo touch /usr/local/bin/dev-setup-script.sh // or somewhere in your local directory
  sudo nano /usr/local/bin/dev-setup-script.sh
```


2. Set file Ownership

   ####   Set wheel as root

  ```bash
    sudo chown root:wheel /usr/local/bin/dev-setup-script.sh
  ```

3. Set file Permissions 

   ####       Make the script executable
   
  ```bash
    sudo chmod +x /usr/local/bin/dev-setup-script.sh
  ```

4. Usage

    #### Run the script directly by entering its full path:
  ```bash
    /usr/local/bin/dev-setup-script.sh
  ```

5. Create an Alias for easier access
   
    #### Add alias to ~/.zshrc file
```bash
  echo 'alias macsetup="/usr/local/bin/dev-setup-script.sh"' >> ~/.zshrc
```

6. Alias run
   
    #### Restart terminal or run source ~/.zshrc
  ```bash
    source ~/.zshrc

    # Type `macsetup` anywhere in terminal
    macsetup
  ```

<br/>

## 🚀  One-liner: 


   ####     Creates script file, sets permissions and opens it up for pasting
  ```bash
    # Create file, set permissions
    sudo touch /usr/local/bin/dev-setup-script.sh && sudo chmod +x /usr/local/bin/dev-setup-script.sh && sudo nano /usr/local/bin/dev-setup-script.sh

    # Add alias to env
    echo 'alias macsetup="/usr/local/bin/dev-setup-script.sh"' >> ~/.zshrc

    # Run file
    macsetup
  ```


<br />

<img width="1631" height="1018" alt="macsetup" src="https://github.com/user-attachments/assets/4186a140-b690-42cd-ba77-738530ccf269" />


:100:

<br />
