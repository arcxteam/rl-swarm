> [!NOTE]
> **Always Latest Update:** Currently in the new recent update, This was modify config by me for Gensyn training LLmodels thats effective for any **low vRAM GPU** resources like **RTX Series 20xx, 30xx, 40xx, A1xx, A2xx, A4xx** is same optimize any swarm inferences (originally).

[![Gensyn](https://img.shields.io/github/v/release/gensyn-ai/rl-swarm?label=OfficialUpdate&color=blue)](https://github.com/gensyn-ai/rl-swarm/releases)

## System Requirements

![VPS](https://img.shields.io/badge/CLOUD_GPU_SERVER-232F3E?style=for-the-badge&logo=digitalocean&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)

| Requirement     | Detail                 |
| :----------     | :--------------------  |
| **Linux**       | Ubuntu 20 - 22 - 24 LTS          |
| **Windows**     | WSL - Ubuntu                     |
| **CPU**         | vCores 10 with 12GB RAM - more   |
| **VRAM GPU**    | Min 6GB - more VRAM              |
| **GPU-Series**  | GTX 1080 with CUDA 12.4-12.8 - RTX series |
| **STORAGE**     | Pass-lock 98GB - 99GB              |

> **Note: Its just a imagine, you can choose anything your take. But i can sharing any Tips & Trick if your rent cloud GPU to [https://octa.space](https://octa.space/?ref=rTXHXwn7D96) I'm not promoter choose this my principals rent any low-cost, its very cheaper than rental GPU competitors. For Tips & Trick read here https://github.com/arcxteam/octa-rental-gpu**

### Basically, if you rent a GPU with a minimum of 6GB or even 8-12-16-24GB of VRAM, you can run other nodes because only 4-5GB of VRAM will be used for this GENSYN with the configuration I modified.

![photo_6271671078992153653_w](https://github.com/user-attachments/assets/adf9e6cc-1125-4a75-b000-cc1b0c1e1541)

## Modify Configs
- `rgym_exp/config/rg-swarm.yaml` → <mark>support any GPU</mark>
- `rgym_exp/src/datasets.yaml` → <mark>boosting rewards</mark>
- `run_rl_swarm.sh` → <mark>all running</mark>
- `other configs` → <mark>latest tags for compatible</mark>

## Official Support LLModels
- `Gensyn/Qwen2.5-0.5B-Instruct`  → <mark>Recommend</mark>
- `Qwen/Qwen3-0.6B` → <mark>Recommend</mark>
- `nvidia/AceInstruct-1.5B`
- `dnotitia/Smoothie-Qwen3-1.7B`
- `Gensyn/Qwen2.5-1.5B-Instruct`

## Installation Setup

**1. Update System Packages**
```bash
apt update && apt upgrade -y && \
apt install screen curl ufw nload tree iptables git wget lz4 jq make gcc nano automake autoconf \
htop tmux libgbm1 protobuf-compiler python3 python3-pip python3-venv python3-dev python3-setuptools \
tar clang nethogs ncdu unzip build-essential pkg-config libssl-dev libleveldb-dev \
speedtest-cli ca-certificates libffi-dev libsqlite3-dev -y
```

**2. Install NODE.JS - NPM - YARN - PM2**
```
source <(wget -qO- https://raw.githubusercontent.com/arcxteam/w-ai-wombo/main/nodejs.sh)
```

**3. Clone the Repository**
```bash
git clone https://github.com/arcxteam/rl-swarm.git && cd rl-swarm
```

## Running Gensyn

### 1. CLI (shell/sh)

**A. If you run with <mark>OctaSpace GPU</mark> is default with Tmux/Termux Container**
- Quick: before deploy in (Expose HTTP Ports) input as `3000` will create localhost no setup need Tips-Trick read [Octaspace](https://github.com/arcxteam/octa-rental-gpu)
- Create new sessions `CTRL+B+C`
- Go to sessions `tmux attach`
- List sessions `CTRL+B+W`
- Navigate sessions `scroll up ↑ down ↓ or click any sessions & then enter`
- Close with run background `CTRL+B+D`

**B. If you run with <mark>Other Rent GPU</mark> create Screen sessions**
- Create sessions `screen -S gensyn`
- Close sessions `CTRL+A+D`
- Go to sessions `screen -r gensyn`

**C. Get into the `rl-swarm` directory**
```
cd rl-swarm
```
**D. Virtual Python & Run Gensyn Swarm**
```bash
python3 -m venv .venv

source .venv/bin/activate
# if not worked, then:
. .venv/bin/activate

./run_rl_swarm.sh
```

### 2. Docker (Container)

**A. Install Docker & Compose → <mark>if the rental was support & use Ubuntu VM</mark>**

```bash
curl -sSL https://raw.githubusercontent.com/arcxteam/succinct-prover/refs/heads/main/docker.sh | sudo bash
```
**B. Install swarm build docker**
* CPU
```bash
docker compose run --rm --build -Pit swarm-cpu
```

* GPU
```bash
docker compose run --rm --build -Pit swarm-gpu
```

## Other GPU Cloud & VPS Users: Setup port localhost:3000 
- Open a new terminal
- Install localtunnel
```
npm install -g localtunnel
```
- The password is actually your VPS-IP
```
curl ifconfig.me && echo
```
- Get URL access
```
lt --port 3000
```
**Visit the prompted url, and enter your password to access Gensyn login page**
