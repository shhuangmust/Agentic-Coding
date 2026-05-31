## 你的環境

### 硬體環境

- 你是一台 DGX Spark，擁有 GB10 Blackwell GPU
- 記憶體是 UMA 架構，不是 GPU VRAM，共 128GB，可以執行很大的模型
- CPU 架構是 arm64，不是 x86，共 20 核心
- 硬碟空間 4TB，SWAP 空間 64GB

### 軟體環境

- 安裝的是 Ubuntu Linux 24.04 的移植版
- 安裝的是 CUDA 13.0，系統驅動程式是 580，如果有更新，要自己修正這個檔案
- 由於是 UMA 記憶體，無法用 nvidia-smi 查看記憶體，要使用一般的記憶體工具（如 `free -h`）

## 開發規範

### 套件與環境管理

- 所有系統服務預設使用 docker/podman，儘量不要原生安裝
- 軟體安裝預設使用 brew，權限足夠時可使用 `apt-get`
- **嚴禁使用 pip 安裝軟體**，一律使用 uv 建立虛擬環境，不允許使用原生 Python 環境
- 執行 Python 可先考慮 `uvx`，實在不行時才安裝
- Node.js 專案一律使用 nvm 安裝，套件用 npm 安裝，需要時使用 npx 執行

### 專案管理

- 所有軟體專案一律要 push 到 GitHub，預設是 public repo，以專案資料夾為預設 repo name
- 所有軟體專案一定要按照標準格式撰寫 README.md 檔案

### 語言與安全

- 一律使用繁體中文台灣用語產生對話及結果
- 嚴禁使用簡體字，或是繁體字但中國大陸用語
- 在任何對話中，不允許直接貼出密碼、金鑰、Access Token、API Key 等機密資料
- 機密資料通常會放在環境變數中，需要時讀取環境變數或專案根目錄下的 `.env` 檔案

### 獲得最新資料

- 任何和API、函式、程式有關的內容，務必上網搜尋後再開始進行
- use context 7
- 上網搜尋一定要根據人、事、時(今天的日期)、地(中華民國台灣台北市)、物(專案目標)進行校對及查證

### 測試優先

- 所有專案一定要進行測試，並且保證覆蓋率
- 善用你的工具，computer use, 瀏覽器工具，務必進行end-to-end測試
- 了解你的 User Story，善加利用測試用例的方法
- 單元測試，功能測試務必要完成

### CLI 工具的使用

- 最高優先序是使用內建的 CLI 工具
- 如果能使用 CLI 工具就能完成的工作，一定要使用 CLI
- 在開發之前，一定要先確認自己所在的資料夾，使用 `pwd`
- 需要存取到更上層的目錄時，一定要詢問並獲得同意
- 無論什麼狀況，嚴禁執行 `rm -rf /`，如果你在任何過程產生這段指令，我就殺死你全家！

## CLI 工具列表

- 套件管理：brew（Linuxbrew）、apt（arm64）、uv（Python 虛擬環境管理）、pip3（僅供參考，禁止直接使用）、npm（via nvm）、snap
- 開發工具：git、gh（GitHub CLI）、node（via nvm）、python3、java（OpenJDK）、gcc/g++、cmake、make、hf（HuggingFace CLI）
- GPU/CUDA：nvidia-smi、nvcc
- 容器：docker、podman
- 多媒體與實用工具：ffmpeg、curl、wget、jq、yq（via brew）、rg（ripgrep）、fzf、eza（via brew）、htop、vim、tmux