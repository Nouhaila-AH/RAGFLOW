# RAGFLOW
What is RAGFLOW?
A advanced search app to help users of the equivalence platform get easy access to information about diplomas and their equivalence. This project is a Generative AI based system including RAG and advanced AI models for relevant information retrieval.

## 🛠️ Get Started!

The project is implemented in Docker, the user should initially have basic knowledge about it in order to run it correctly;
here are the steps to follow


### ✅ Requirements

- **CPU**: ≥ 4 cores  
- **RAM**: ≥ 16 GB  
- **Disk**: ≥ 50 GB  
- **Docker**: ≥ 24.0.0  &  **Docker Compose**: ≥ v2.26.1  

🔗 [Install Docker here !](https://docs.docker.com/engine/install/)





### 🚀 Starting the Server

1️⃣ **Check the value of `vm.max_map_count=262144`**  
(in order to run Elasticsearch without crashing)  

- Open your **WSL**  
- Run:  
```bash
sysctl -w vm.max_map_count=262144
````

* Make it permanent:

```bash
echo "vm.max_map_count=262144" >> /etc/sysctl.conf
sysctl -p
```

2️⃣ **Clone the repository**

```bash
git clone https://github.com/infiniflow/ragflow.git
```

3️⃣ **Start up the server**

```bash
cd ragflow/docker
docker compose -f docker-compose.yml up -d
```

✅ A successful launch will display:

```
      ____   ___    ______ ______ __
     / __ \ /   |  / ____// ____// /____  _      __
    / /_/ // /| | / / __ / /_   / // __ \| | /| / /
   / _, _// ___ |/ /_/ // __/  / // /_/ /| |/ |/ /
  /_/ |_|/_/  |_|\____//_/    /_/ \____/ |__/|__/
```

4️⃣ **Access RAGFLOW**

* Enter the **IP address** in your browser and log in to your account.(usually :http://127.0.0.1)

5️⃣ **Configure LLM**

* Set the **LLM settings**
* Add **documents** and the relevant chunking method
* Customize answers by changing the **prompt section**

---

## 🛠️ Working with Local LLM

**Ollama** provides open-source LLM chat models and embeddings.

###  Download Ollama

[Download here!](https://ollama.com/download)

###  Install Chat & Embedding Models

(In CMD, you can choose another integrated LLM in Ollama)

```bash
# Chat LLM
ollama pull llama3.2

# Embedding model
ollama pull bge-m3
```

###  Check Installation

```bash
ollama list
```

###  Add Models to the App

* Base URL for the app:

```
http://host.docker.internal:11434/
```

### 6️⃣ Rebuild After Code Changes

When code changes are made, the Docker image must be rebuilt to apply the updates.

#### 1. Stop and remove existing containers
    docker compose down

#### 2. Enable Docker BuildKit (recommended)
    export DOCKER_BUILDKIT=1   # if not already enabled

#### 3. Rebuild the Docker image
    docker build --progress=plain -f Dockerfile -t infiniflow/ragflow:local .

#### 4. Recreate and start the containers
    docker compose up -d

✅ The application will now run with the latest code changes.

