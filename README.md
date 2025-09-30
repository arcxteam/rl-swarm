Currently in the new recent update, Gensyn testnet is running and training the reasoning-gym swarm datasets on the Testnet. This swarm is supporting the current list of default models:

- Gensyn/Qwen2.5-0.5B-Instruct
- Qwen/Qwen3-0.6B
- nvidia/AceInstruct-1.5B
- dnotitia/Smoothie-Qwen3-1.7B
- Gensyn/Qwen2.5-1.5B-Instruct


**1. Update System Packages**
```bash
apt update && apt upgrade -y && \
apt install screen curl ufw nload tree iptables git wget lz4 jq make gcc nano automake autoconf htop tmux libgbm1 protobuf-compiler python3 python3-pip python3-venv python3-dev python3-setuptools \
tar clang ncdu unzip build-essential pkg-config libssl-dev libleveldb-dev \
speedtest-cli ca-certificates libffi-dev libsqlite3-dev -y
```

**2. Install Node.js, Npm, Yarn, and PM2**
```
#!/usr/bin/env bash

# -------------------------------------------------
# Name: node‑setup.sh
# Description: Bootstrap install Node.js, npm, Yarn, and PM2
# Platform: Linux (Ubuntu/Debian)
# -------------------------------------------------

# Install NVM
echo "Installing NVM (Node Version Manager)..."
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# load environment NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

# Install Node.js
echo "Installing Node.js v22.18.0 (LTS)..."
nvm install 22.18.0
nvm use 22.18.0
nvm alias default 22.18.0

echo "Verifying Node.js and npm installation..."
node -v
npm -v

# Install PM2
echo "Installing PM2..."
npm install -g pm2

echo "Verifying PM2 installation..."
pm2 -v

# Install Yarn
echo "Installing Yarn..."
npm install -g yarn

echo "Verifying Yarn installation..."
yarn -v

# add to .bashrc
echo "Adding NVM to .bashrc..."
cat <<EOF >> ~/.bashrc
export NVM_DIR="$HOME/.nvm"
[ -s "\$NVM_DIR/nvm.sh" ] && \. "\$NVM_DIR/nvm.sh"
[ -s "\$NVM_DIR/bash_completion" ] && \. "\$NVM_DIR/bash_completion"
EOF

# reload .bashrc
source ~/.bashrc

echo "Setting proper permissions for NVM and Node.js installation..."
chown -R $USER:$USER ~/.nvm
chmod -R 755 ~/.nvm

# Ready version help
echo "Installation completed successfully."
echo "Node.js version: $(node -v)"
echo "Npm version: $(npm -v)"
echo "PM2 version: $(pm2 -v)"
echo "Yarn version: $(yarn -v)"
```

## Clone the Repository
```bash
git clone https://github.com/arcxteam/rl-swarm.git
```

---

### CLI Method (GPU)
1- Open a screen to run it in background
```bash
screen -S gensyn
```
2- Get into the `rl-swarm` directory
```
cd rl-swarm
```
3- Install swarm
```bash
python3 -m venv .venv

source .venv/bin/activate
# if not worked, then:
. .venv/bin/activate

./run_rl_swarm.sh
```

## Install swarm build docker
* Mac or CPU-Only VPS
```bash
docker compose run --rm --build -Pit swarm-cpu
```

* GPU
```bash
docker compose run --rm --build -Pit swarm-gpu
```

* **GPU Cloud & VPS Users: Tunnel to external URL:**
  * 1- Open a new terminal
  * 2- Install **localtunnel**:
    ```
    npm install -g localtunnel
    ```
  * 3- Get a password:
    ```
    curl https://loca.lt/mytunnelpassword
    ```
  * The password is actually your VPS IP
  * 4- Get URL
    ```
    lt --port 3000
    ```
  * Visit the prompted url, and enter your password to access Gensyn login page
