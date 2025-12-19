# Ollama on Colab + Gradio Web UI

> Spin up a full Ollama stack on Google Colab, backed by cloud GPUs, and talk to any supported open-source LLM through a clean Gradio interface.

<a target="_blank" href="https://colab.research.google.com/github/theelderemo/ollama-google-colab/blob/main/ollamacolab.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

---

## Overview

This repository contains a Jupyter Notebook that:

- Deploys a fully functional **Ollama** instance on **Google Colab**
- Exposes an **interactive Gradio web UI** for chatting with models
- Lets you run and test **open source LLMs** on **Google’s cloud GPUs**  
  (no high end local hardware required)

---

## Features

### Inference & Models

- **Cloud-Based Inference**  
  Run resource-intensive models without a powerful local machine.

- **Universal Model Support**  
  Load and use any model available in the [Ollama library](https://ollama.com/search).

- **Custom System Prompts**  
  Inject specific instruction sets directly into the system context.

- **Parameter Tuning**  
  Adjust `temperature`, `top_p`, and `top_k` to match your use case.

### Interface

- **Interactive Web UI**  
  Specialized chat interface built with **Gradio**, served from within Colab.

---

## Quick Start

### 1. Set the Runtime

1. Open the notebook in Google Colab. <a target="_blank" href="https://colab.research.google.com/github/theelderemo/ollama-google-colab/blob/main/ollamacolab.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

2. Go to **Runtime → Change runtime type**.
3. Set the **hardware accelerator** to:
   - **T4 GPU** (free tier), or  
   - **A100** (Colab Pro / Pro+), if available.

> **Note**  
> The initial setup cell may take several minutes while it installs Linux dependencies and NVIDIA drivers.

---

### 2. Run the Notebook

1. Execute **all cells in order** from top to bottom.
2. When the final cell finishes:
   - Locate the **Gradio live link** in the output.
   - Click it to open your **chat dashboard** in a new tab.

---

## How to Run Any Model

The deployment is model agnostic: you are not restricted to a single preinstalled model. Any model exposed by Ollama’s library can be pulled and used dynamically.

1. Open the generated **Gradio public link** after the Colab cells finish.
2. In the **Configuration** sidebar, find the **Model Name** input.
3. Enter the desired model tag, for example:
   - llama3
   - dolphin3
   - mistral
   - gemma:7b
4. Refer to the [Ollama Library](https://ollama.com/search) for the full list of valid model tags.
5. Click **Pull Model**.
6. Wait until the status indicates **“Successfully pulled”**.
7. Start chatting with the selected model immediately.

---

## Technical Details

<details>
<summary><strong>Environment & Stack</strong></summary>

* **Backend:** Ollama (Linux `amd64` bundle)
* **Frontend:** Gradio (Python)
* **Environment:** Ubuntu 22.04 (standard Google Colab runtime)
* **Networking:** Gradio tunnel exposing the local server to the public web

</details>

---

## Runtime Behavior & Disclaimer

This notebook runs entirely on **Google Colab resources**:

* The server is active only while the **Colab runtime** is alive.
* If the browser tab is closed, the runtime idles out, or the session times out:

  * The Ollama instance stops.
  * The Gradio link becomes invalid.
* To resume, you must:

  * Reconnect the runtime
  * Rerun the notebook cells
  * Reopen the new Gradio link

Use this setup as an ephemeral, GPU backed playground rather than a persistent production deployment.
