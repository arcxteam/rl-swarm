<p align="center">
  <img src="https://github.com/user-attachments/assets/e951ce01-7420-403e-a14a-11dca4c3b81b"
       width="128" height="128"
       alt="logo-gensyn">
</p>

<h1 align="center">Gensyn RL-Swarm: Training & GGUF Inference for Quantized LLMs</h1>

<p align="center">
  <strong>A Comprehensive Guide to Running a Gensyn RL-Swarm Training</strong><br>
  <em>Continuous Training, an Experimental (advanced) mode, GGUF LLM Compatibility on Huggingface</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Trained%20with-Gensyn%20RL--Swarm-pink" alt="gensyn">
  <a href="https://github.com/gensyn-ai/rl-swarm/releases"><img src="https://img.shields.io/github/v/release/gensyn-ai/rl-swarm?label=Version&color=green" alt="version"></a>
  <img src="https://img.shields.io/badge/GGUF-Available-FF0069" alt="GGUF">
  <img src="https://img.shields.io/badge/LLama.cpp-Compatible-orange" alt="llama.cpp">
  <img src="https://img.shields.io/badge/🤗 Huggingface-Models-blue" alt="Huggingface">
</p>

---

## Overview

Our pick this model a continuously trained `Qwen2.5-Coder-0.5B-Instruct` fine-tuned using **Gensyn RL-Swarm** framework with **GRPO** (Generalized Reward Policy Optimization) and supported format **GGUF (llama.cpp)** for enhanced trained on logic, mathematical problem-solving & reasoning tasks capabilities. **Note: My modify previous Gensyn v0.6.2-v0.6.4 the training same focuses**.

- **Agent ID:** [Huggingface GGUF](https://huggingface.co/0xgr3y/Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-tall_tame_panther)
- **Training Status:** 🟢 LIVE - Model updates automatically every 5-10 minutes
- **Auto-Sync GGUF Pipeline Status:** 🟢 LIVE - Commits update automatically every 1h-hourly
- **Current Progress:** Round 10,610+ target 100,000 (10,61%)
- **Framework Version:** Gensyn RL-Swarm (CodeZero) `v0.7.0`
- **Contract Judge:** SwarmCoordinator `v0.4.2`
- **GGUF Quantization:** Multiple quantized available `(F16, Q3_K_M, Q4_K_M, Q5_K_M, Q6_K)`

> [!NOTE]
> **ALWAYS LATEST UPDATE:** Currently in recent update Gensyn RL-Swarm is **CodeZero (Solvers, Proposers & Evaluators)**, This was modify config by me for Gensyn training LLmodels thats effective for any min-low vRAM GPU resources like **RTX Series 20xx, 30xx, 40xx, A1xx, A2xx, A4xx** is same optimize any swarm inferences (originally).

- **Proposers:** Generate coding problems and unit tests, adjusting difficulty dynamically based on solver performance. Proposers create challenges that adapt to the swarm's current capabilities, ensuring continuous learning opportunities.
- **Solvers:** Attempt coding challenges, learn locally through RL, and share rollouts with peers. Solvers exchange solutions to promote diversity and accelerate collective learning across the network.
- **Evaluators**: Frozen models that assess correctness and assign rewards. Evaluators use rule-based assessment to score submissions without executing code, ensuring safety and scalability.

## Requirements

![VPS](https://img.shields.io/badge/CPU/GPU_Server-232F3E?style=for-the-badge&logo=digitalocean&logoColor=red)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Huggingface](https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)

| Requirement     | Detail                 |
| :----------     | :--------------------  |
| **Linux**       | Ubuntu 20 - 22 - 24 LTS          |
| **Windows**     | WSL - Ubuntu                     |
| **CPU**         | vCores 10 with 12GB RAM - more   |
| **VRAM GPU**    | Min 6GB - more VRAM              |
| **GPU-Series**  | GTX 1080 with CUDA 12.4-12.8 - RTX series |
| **STORAGE**     | Pass-lock 98GB - 99GB              |

> **Note: Its just a imagine, you can choose anything your take. But i can sharing any tips if your rent cloud GPU to [https://octa.space](https://octa.space/?ref=rTXHXwn7D96) I'm not promoter choose this my principals rent any low-cost, its very cheaper than rental GPU competitors. For tips & trick read... https://github.com/arcxteam/octa-rental-gpu**

> Basically, if you rent a GPU with a minimum of 6GB or even 8-12-16-24GB of VRAM, you can run other nodes because only 4-5GB of VRAM will be used for this GENSYN with the configuration I modified.

![photo_6271671078992153653_w](https://github.com/user-attachments/assets/adf9e6cc-1125-4a75-b000-cc1b0c1e1541)

## Configure Modify
- `rgym_exp/config/rg-swarm.yaml` → <mark>support low-vRAM GPU</mark>
- `rgym_exp/src/datasets.yaml` → <mark>boost-rewards = weighted sampling composition</mark>
- `run_rl_swarm.sh` → <mark>latest mark for compatible</mark>
- `other configs` → <mark>latest mark for compatible</mark>

## Official Support Models
- `Qwen/Qwen2.5-Coder-0.5B-Instruct`  → <mark>Recommend Solver</mark>
- `deepseek-ai/deepseek-coder-1.3b-instruct` → <mark>Recommend Proposers, Evaluators</mark>
- `Qwen/Qwen2.5-Coder-1.5B-Instruct` → <mark>Recommend Proposers, Evaluators</mark>

> The model is trained on a composite dataset (1,000 samples) with weighted sampling strategy

| Dataset | Weight | Focus Area |
|---------|--------|------------|
| Propositional Logic | 7 | Logical reasoning, truth tables, Boolean operations |
| Calendar Arithmetic | 6 | Date calculations, leap years, recurring events |
| Decimal Arithmetic | 5 | Multi-term decimal operations with precision |
| Base Conversion | 4 | Number system conversions (base 2-16) |
| Fraction Simplification | 4 | GCD/LCM, fraction reduction |
| Basic Arithmetic | 2 | Foundation operations with parentheses |

## Installation Setup

**1. Update System Packages**
```bash
apt update && apt upgrade -y && \
apt install screen curl ufw nload tree iptables git wget lz4 jq make gcc nano automake autoconf \
htop tmux libgbm1 protobuf-compiler python3 python3-pip python3-venv python3-dev python3-setuptools \
tar clang nethogs ncdu unzip build-essential pkg-config libssl-dev libleveldb-dev \
speedtest-cli ca-certificates libffi-dev libsqlite3-dev -y
```

**2. Install v22 Node.js - Npm - Yarn - Pm2**
```
source <(wget -qO- https://raw.githubusercontent.com/arcxteam/w-ai-wombo/main/nodejs.sh)
```

**3. Clone Repository**
```bash
git clone https://github.com/arcxteam/rl-swarm.git && cd rl-swarm
```

## Running Gensyn RL-Swarm

### 1. CLI (Shell/sh)

**A. If you run with <mark>OctaSpace cloud GPU</mark> default is Tmux/Termux sessions**
- Full comprehensif guide tips & trick read here [Octaspace](https://github.com/arcxteam/octa-rental-gpu)
- Quick-1: Always rent with this template **UBUNTU 22.04 LTS** dont use another template
- Quick-2: Always deploy in coloum **(Expose HTTP Ports)** input https port as **3000** will auto create localhost services for gensyn login
- Create new sessions `CTRL+B+C`
- Go to sessions `tmux attach`
- List sessions `CTRL+B+W`
- Navigate sessions `scroll up ↑ down ↓ or click any sessions & then enter`
- Close with run background `CTRL+B+D`

**B. If you run with <mark>another cloud GPU</mark> use Screen sessions**
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

**A. Install Docker & Compose → <mark>if the cloud GPU was support & use Ubuntu VM</mark>**

```bash
curl -sSL https://raw.githubusercontent.com/arcxteam/succinct-prover/refs/heads/main/docker.sh | bash
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

## Other Cloud GPU & VPS Users: Setup Manual [localhost:3000]
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
