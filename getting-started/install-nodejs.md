# Install NodeJS

For Ubuntu system, use `sudo apt-get install nodejs` to install nodejs, but it maybe an old version.

Follow this link to choose a new nodejs [nodesource/distributions](https://github.com/nodesource/distributions)

    # Nodejs 16.x for Ubuntu
    curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
    sudo apt-get install -y nodejs
    # Install yarn v1.x
    sudo npm install --global yarn
    # Update npm
    sudo npm install -g npm@8.10.0
    # Instal node npm packages from package.json
    # yarn