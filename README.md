<p align="center">
  <img src="https://github.com/user-attachments/assets/e951ce01-7420-403e-a14a-11dca4c3b81b"
       width="128" height="128"
       alt="logo-gensyn">
</p>

<h1 align="center">Gensyn RL-Swarm: Training & GGUF Quantized LLMs for Inference</h1>

<p align="center">
  <strong>A Comprehensive Guide to Running a Gensyn RL-Swarm Training</strong><br>
  <em>Continuous Training, an Experimental (advanced) mode, GGUF LLM Compatibility on Huggingface</em>
</p>

<p align="center">
  <a href="https://gensyn.ai"><img src="https://img.shields.io/badge/Trained%20with-Gensyn%20RL--Swarm-pink" alt="gensyn"></a>
  <a href="https://github.com/gensyn-ai/rl-swarm/releases"><img src="https://img.shields.io/github/v/release/gensyn-ai/rl-swarm?label=Version&color=green" alt="version"></a>
  <a href="https://huggingface.co/0xgr3y/Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-tall_tame_panther/tree/main"><img src="https://img.shields.io/badge/GGUF-Available-FF0069" alt="GGUF"></a>
  <a href="https://github.com/ggerganov/llama.cpp"><img src="https://img.shields.io/badge/LLama.cpp-Compatible-orange" alt="llama.cpp"></a>
  <a href="https://huggingface.co/0xgr3y/Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-tall_tame_panther"><img src="https://img.shields.io/badge/🤗%20Huggingface-Models-blue" alt="Huggingface"></a>
</p>

<div align="center">

[![Gensyn](https://img.shields.io/badge/Powered%20by-Gensyn%20AI-pink?style=for-the-badge)](https://gensyn.ai)

</div>

---

## **Overview**

Our pick an **experimental (advanced) mode** at this model a continuously trained `Qwen2.5-Coder-0.5B-Instruct` fine-tuned using **Gensyn RL-Swarm** framework with **GRPO (Group Relative Policy Optimization)** and supported format **GGUF (llama.cpp)** for enhanced code generation capabilities. **Note: Current training focuses on programming challenges with adaptive weighted sampling**.

- **Agent ID:** [Huggingface LLModels](https://huggingface.co/0xgr3y/Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-tall_tame_panther)
- **Training Status:** 🟢 LIVE - Model updates automatically every 5-10 minutes
- **Auto-Sync GGUF Pipeline Status:** 🟢 LIVE - Commits update automatically every hourly
- **Current Progress:** Round 14,854+ / 100,000 (14.85%)
- **Framework Version:** Gensyn RL-Swarm (CodeZero) `v0.7.0`
- **Contract Judge:** SwarmCoordinator `v0.4.2`
- **GGUF Quantization:** Multiple quantized available `(F16, Q3_K_M, Q4_K_M, Q5_K_M, Q6_K)`

> [!NOTE]
> **LATEST PULL:** Currently in recent update Gensyn RL-Swarm is **CodeZero (Solvers, Proposers & Evaluators)**, This was modify configure experimental (advanced) mode by for Gensyn training model thats support for any min-low vRAM GPU resources like **RTX Series 20xx, 30xx, 40xx, A1xx, A2xx, A4xx** is same optimize into swarm training (originally).

- **Proposers:** Generate coding problems and unit tests, adjusting difficulty dynamically based on solver performance. Proposers create challenges that adapt to the swarm's current capabilities, ensuring continuous learning opportunities.
- **Solvers:** Attempt coding challenges, learn locally through RL, and share rollouts with peers. Solvers exchange solutions to promote diversity and accelerate collective learning across the network.
- **Evaluators**: Frozen models that assess correctness and assign rewards. Evaluators use rule-based assessment to score submissions without executing code, ensuring safety and scalability.

## **Requirements**

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

> **Basically, if you rent a GPU with a minimum of 6GB or even 8-12-16-24GB of VRAM, you can run other nodes because only 4-5GB of VRAM will be used for this GENSYN with the configure modified.**

![photo_6271671078992153653_w](https://github.com/user-attachments/assets/adf9e6cc-1125-4a75-b000-cc1b0c1e1541)

## **Quick Configuration**
- **Adaptive Sampling Strategy**
- **Adaptive Threshold System**
- **Data Quality Enhanced Implementation**
- **Adaptive Reward System**: Dynamic quality enhanced and dataset weighting for optimal learning
- **Multi-domain Coding**: Trained on MBPP and CodeContests datasets with adaptive sampling

The model is trained on a composite dataset with adaptive weighted sampling strategy

| Dataset | Initial Weight | Adaptive Range | Focus Area | Stream Synthesis |
|---------|----------------|----------------|------------| ------------|
| MBPP | 5 | 5-6 | Basic Python programming problems with test cases | [google-research-datasets/mbpp](https://huggingface.co/datasets/google-research-datasets/mbpp) |
| CodeContests | 5 | 4-5 | Competitive programming challenges | [deepmind/code_contests](https://huggingface.co/datasets/deepmind/code_contests) |

> For detail on Huggingface → <mark>[Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-My-Agent-ID](https://huggingface.co/0xgr3y/Qwen2.5-Coder-0.5B-Instruct-Gensyn-Swarm-tall_tame_panther)</mark>

## **Gensyn - Official Support Models**
- `Qwen/Qwen2.5-Coder-0.5B-Instruct`  → <mark>**Recommend Solver**</mark>
- `deepseek-ai/deepseek-coder-1.3b-instruct` → **Proposers, Evaluators**
- `Qwen/Qwen2.5-Coder-1.5B-Instruct` → **Proposers, Evaluators**

## **Quick Launch**

**I. Update System Packages**
```bash
apt update && apt upgrade -y && \
apt install screen curl ufw nload tree iptables git wget lz4 jq make gcc nano automake autoconf \
htop tmux libgbm1 protobuf-compiler python3 python3-pip python3-venv python3-dev python3-setuptools \
tar clang nethogs ncdu unzip build-essential pkg-config libssl-dev libleveldb-dev \
speedtest-cli ca-certificates libffi-dev libsqlite3-dev -y
```

**II. Install v22 Node.js - Npm - Yarn - Pm2**
```bash
source <(wget -qO- https://raw.githubusercontent.com/arcxteam/w-ai-wombo/main/nodejs.sh)
```

**III. Clone Repository**
```bash
git clone https://github.com/arcxteam/rl-swarm.git && cd rl-swarm
```

## **Running Gensyn RL-Swarm**

### **1. CLI (Shell/sh)**

**I. If run with <mark>OctaSpace GPU</mark> default Tmux/Termux sessions**
- Full comprehensif guide tips & trick read here [Octaspace](https://github.com/arcxteam/octa-rental-gpu)
- Quick-1: Always rent with this template **UBUNTU 22.04/24.04 LTS** dont use another template
- Quick-2: Always deploy in coloum **(Expose HTTP Ports)** input https port as **3000** will auto create localhost to access gensyn login
- Create new sessions `CTRL+B+C`
- Go to sessions `tmux attach`
- List sessions `CTRL+B+W`
- Navigate sessions `scroll up ↑ down ↓ or click any sessions & then enter`
- Close with run background `CTRL+B+D`

**II. If run with <mark>other cloud GPU</mark> use Screen sessions**
- Create sessions `screen -S gensyn`
- Close sessions `CTRL+A+D`
- Go to sessions `screen -r gensyn`

**III. Virtual Python & Running**
```bash
python3 -m venv .venv

source .venv/bin/activate
# if not worked, then:
. .venv/bin/activate

./run_rl_swarm.sh
```

### **2. Docker (Container)**

**I. Install Docker & Compose → <mark>if the cloud GPU was support & use Ubuntu VM</mark>**

```bash
curl -sSL https://raw.githubusercontent.com/arcxteam/succinct-prover/refs/heads/main/docker.sh | bash
```
**II. Setup build on docker**
* CPU
```bash
docker compose run --rm --build -Pit swarm-cpu
```

* GPU
```bash
docker compose run --rm --build -Pit swarm-gpu
```

## **Gensyn Dashboard - Manual `localhost:3000`**

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

> **Visit the prompted url, and enter your password to access Gensyn login page**

## **Available GGUF Quantization**

| Format | Size | Precision | Use Case | Download |
|--------|------|-----------|----------|----------|
| Safetensors (BF16) | 988 MB | BF16 | Full precision training/fine-tuning | `model.safetensors` |
| GGUF F16 | 994 MB | FP16 | High quality inference | `Qwen2.5-Coder-0.5B-F16.gguf` |
| GGUF Q6_K | 506 MB | 6-bit | High quality compression | `Qwen2.5-Coder-0.5B-Q6_K.gguf` |
| GGUF Q5_K_M | 420 MB | 5-bit | Balanced quality/size | `Qwen2.5-Coder-0.5B-Q5_K_M.gguf` |
| GGUF Q4_K_M | 398 MB | 4-bit | **Recommended** for production | `Qwen2.5-Coder-0.5B-Q4_K_M.gguf` |
| GGUF Q3_K_M | 355 MB | 3-bit | Smallest, fastest | `Qwen2.5-Coder-0.5B-Q3_K_M.gguf` |

> All GGUF formats are **llama.cpp is compatible** ready to use **Inferences chat** and auto-update be hourly.


## **References**
- **Gensyn Documentation**: https://docs.gensyn.ai/
- **Gensyn GitHub**: https://github.com/gensyn-ai
- **RL-Swarm Contracts**: https://github.com/gensyn-ai/rl-swarm-contracts
- **Qwen2.5-Coder Model Card**: https://huggingface.co/Qwen/Qwen2.5-Coder-0.5B-Instruct
- **MBPP Dataset**: https://huggingface.co/datasets/google-research-datasets/mbpp
- **CodeContests Dataset**: https://huggingface.co/datasets/deepmind/code_contests
- **arXiv:1910.09700**: ML Carbon Emissions methodology
- **Community**: [Gensyn Discord](https://discord.gg/gensyn)

---

<div align="center">
  
**Trained with 🩷 using Gensyn RL-Swarm**

[![Gensyn](https://img.shields.io/badge/Powered%20by-Gensyn%20AI-pink?style=for-the-badge)](https://gensyn.ai)

</div>
