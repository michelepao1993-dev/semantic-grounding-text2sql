# Semantic Grounding over Brute-Force Inference: A Symbiotic Evaluation of Text-to-SQL Systems

This repository contains the implementation, evaluation framework, experimental artifacts, and analysis notebooks associated with the paper:
"Semantic Grounding over Brute-Force Inference: A Symbiotic Evaluation of Text-to-SQL Systems"


---


# Overview

Recent Text-to-SQL systems often rely on brute-force strategies such as:

- full-schema prompting,
- large-scale candidate generation,
- expensive inference-time reasoning.


This repository explores an alternative perspective based on:

- information quality,
- semantic grounding,
- cost-aware evaluation.


The proposed framework introduces a cost-aware Symbiotic Evaluation Framework that jointly considers:
- execution quality,
- relation-level correctness,
- token usage,
- latency,
- inference complexity,
- information quality.


The framework based on relation-level utility metrics complements standard Text-to-SQL evaluation protocols such as Execution Accuracy.


---


# Repository Structure
```text
.
├── README.md
├── LICENSE.txt
├── requirements.txt
├── .gitignore
│
├── Semantics/
│   ├── N0_First_API.ipynb
│   └── ...
│
├── agents/
│   ├── baseline_agent.py
│   ├── telemetry.py
│   └── types.py
│
├── analysis/
│   ├── aggregate.py
│   ├── insights.py
│   └── multi_run.py
│
├── data/
│   ├── spider_loader.py
│   ├── schema_text.py
│   └── spider/ <- The folder needs to be downloaded.
│       ├── dev.json
│       ├── train_spider.json
│       ├── tables.json
│       ├── database/
│       └── ...
│
├── evaluation/
│   ├── advanced_metrics.py
│   ├── component_match.py
│   ├── candidate_diversity.py
│   └── oracle.py
│
├── execution/
│   └── sql_executor.py
│
├── experiment_logging/
│   ├── logger.py
│   └── schema.py
│
├── fewshot_retrieval/
│   └── fewshot_retriever.py
│
├── models/
│   └── openai_chat_model.py
│
├── notebooks/
│   └── Experiments.ipynb
│
├── outputs/
│   └── logs_clean/
│       ├── enriched/
│       └── more_models/
│
└── runner/
    ├── db_setup.py
    ├── experiment_runner.py
    ├── grid_runner.py
    └── turn_runner.py
```


---


# Installation

 1. Clone the repository


```bash

git clone https://github.com/michelepao1993-dev/semantic-grounding-text2sql.git

cd semantic-grounding-text2sql

```


2. Create a virtual environment


```bash

python -m venv .venv

source .venv/bin/activate

```


Windows:


```bash

.\.venv\Scripts\Activate.ps1

```


 3. Install dependencies


```bash

pip install -r requirements.txt

```


4. Create a .env file


```bash

touch .env

```


Windows:


```bash

New-Item -Path .env -ItemType File

```


5. Open the .env file with a text editor and insert the necessary keys


OpenAI key:

\# --- OpenAI ---
OPENAI_API_KEY=***


---


# Dataset Setup

For convenience, this repository does not redistribute the full Spider dataset.

Spider benchmark:
https://yale-lily.github.io/spider

After downloading, the dataset is placed under:


```text

data/spider/

```


Expected structure:


```text

data/spider/
├── database/
├── train_spider.json
├── dev.json
├── tables.json
└── ...

```


---


# Educational Resources: From LLMs to Conversational Text-to-SQL Agents

The `Semantics/` directory provides a hands-on introduction to LLM-based conversational agents, building upon educational materials from LangChain Academy.

The notebooks progressively introduce:

- LLM APIs and message-based interaction.
- Graph-based orchestration with LangGraph.
- Tool calling and the ReAct paradigm.
- Conversational memory and state management.
- Safe SQL execution and database interaction.
- The implementation of a fully functional conversational Text-to-SQL agent.

The final notebook, `N6_Conversational_Text_to_SQL_Agent.ipynb`, integrates these concepts into a practical application using the Spider benchmark.

These educational resources complement the research framework by providing an accessible entry point for students, researchers, and developers interested in LLM-based agents, semantic grounding, and Text-to-SQL systems.


---


# Evaluation Metrics

The framework supports both standard and relation-level metrics.


## Standard Metrics

- Execution Accuracy (EX)
- Exact Match (EM)
- Component Matching (CM)


## Relation-Level Metrics

- Relational Accuracy
- Informational Relational Accuracy (beta=0)
- Utility-aware evaluation measures


The proposed metrics aim to better capture:

- partial correctness,
- useful over-complete answers,
- conversational utility,
- deployment realism.


---


# Notebooks

The repository includes:

## Semantics
This folder contains notebooks based on other materials published as part of LangChain Academy courses—designed to foster a better understanding of LangGraph, the Python library upon which this repository is built.


## Experiments.ipynb
It's a notebook for reproducibility and analysis. It reproduces the main quantitative tables reported in the paper.

Includes:

- aggregation of experiment logs,
- metric computation,
- final comparisons,
- models,
- temperatures,
- candidate generation strategies,
- other setups.


## Running Experiments

The experimental framework can be accessed through `notebooks/Experiments.ipynb`.

The notebook supports two workflows:

- **Offline evaluation:** reproduce the reported metrics and quantitative comparisons using the provided experimental logs, without making live API calls.
- **Live experimentation:** configure and launch new experiments using `ExperimentSpec` and `GridRunner`. This requires the Spider dataset and a valid OpenAI API key.

By default, the cells responsible for launching live experiments are commented out to prevent unintended API costs. To run new experiments, uncomment the desired experimental configurations and the corresponding execution cell.

When launching new experiments, use a separate output directory to preserve the original experimental artifacts.


---


# Logs and Reproducibility

The repository includes anonymized and cleaned experimental logs under:


```text

outputs/logs_clean/

```

Sensitive metadata, provider-specific identifiers, and internal traces were removed before publication.

The logs are sufficient to reproduce:

- aggregate metrics,
- tables,
- figures,
- statistical analyses.


---


# Reproducibility Notes

- All notebooks were executed from a clean environment before release.
- Outputs and figures included in the paper can be reproduced from the provided logs.
- The experimental analysis notebook reproduces the reported results from precomputed logs without requiring live API calls. The educational notebooks in `Semantics/` require an API key for hands-on experimentation.


---


# Limitations

This repository currently focuses on:

- Spider-style relational databases,
- GPT-family models,
- English-language Text-to-SQL settings.

Additional limitations and discussion are reported in the paper.


---


# Citation

If you use this repository, please cite:

```bibtex

@inproceedings{paolicelli2026semantic,
    title={Semantic Grounding over Brute-Force Inference: A Symbiotic Evaluation of Text-to-SQL Systems},
    author={Michele Paolicelli and Cataldo Musto and Giovanni Semeraro and Alessandro Crnjar and David Landi and Claudio Saccà},
    booktitle={Proceedings of AIxIA 2026},
    year={2026}
}
```


---


# License

This repository is released under the MIT License.

See:


```text

LICENSE.txt

```


for details.


---


# Disclaimer

This repository is provided for research and reproducibility purposes. The implementation reflects the experimental setup described in the accompanying paper unless otherwise specified.


---


# Running the Educational Notebooks for Free: Ollama and Qwen

The educational notebooks are designed to be largely model- and provider-independent. Students are not required to purchase API credits or subscribe to any commercial service.

## Local Inference with Ollama (Recommended)

[Ollama](https://ollama.com/) provides a simple way to download and run open-weight language models directly on your computer.

This approach offers several advantages:

- No API key or account registration required.
- No credit card or payment required.
- No external inference services.
- No dedicated GPU required.
- No provider-imposed API rate limits.
- Local execution, including prompts and database results.
- Internet access is not required for inference once the software and model have been downloaded.

## 1. Install Ollama

Download and install Ollama for your operating system:

https://ollama.com/download

Alternatively, on Windows, open PowerShell and run:

```powershell
irm https://ollama.com/install.ps1 | iex
```

Verify the installation:

```bash
ollama --version
```

## 2. Download a Language Model

We recommend starting with Qwen3-4B, a relatively lightweight model supporting tool calling and reasoning capabilities.

```bash
ollama pull qwen3:4b
```

You can immediately interact with the model from your terminal:

```bash
ollama run qwen3:4b
```

Other models from the Qwen3 family are also available:

| Model | Parameters | Approximate download size |
|---|---:|---:|
| `qwen3:0.6b` | 0.6B | 523 MB |
| `qwen3:1.7b` | 1.7B | 1.4 GB |
| `qwen3:4b` | 4B | 2.5 GB |
| `qwen3:8b` | 8B | 5.2 GB |
| `qwen3:14b` | 14B | 9.3 GB |

Smaller models require fewer computational resources but may be less reliable when performing complex tasks. Larger models may provide better results, depending on the task and available hardware.

See the [Qwen3 model collection](https://ollama.com/library/qwen3) for further information.

## 3. Install the LangChain Integration

If not already installed through the repository requirements, install the Ollama integration:

```bash
pip install langchain-ollama==0.3.9
```

When installing dependencies directly from Jupyter, remember to restart the kernel before proceeding.

## 4. Use Ollama in the Notebooks

With Ollama running, replace the OpenAI model initialization with:

```python
from langchain_ollama import ChatOllama

llm = ChatOllama(
    model="qwen3:4b",
    temperature=0,
    num_ctx=4096
)
```

Keep the original model variable name if required by the notebook, and skip the OpenAI API key configuration.

Test the model:

```python
response = llm.invoke("What is a Large Language Model?")
response.pretty_print()
```

For tool-calling agents, use the common LangChain interface:

```python
llm_with_tools = llm.bind_tools(tools)
```

Provider-specific arguments, such as `parallel_tool_calls=False`, should be removed when using Ollama.

The LangGraph architecture, database execution tools, conversational memory, and orchestration logic can remain unchanged.

## 5. Local Text-to-SQL: Experimental Example

Qwen3-4B has been successfully tested with the conversational ReAct Text-to-SQL agent presented in:

`Semantics/N6_Conversational_Text_to_SQL_Agent.ipynb`

For instance, given the question:

> How many singers are there in each country?

The model successfully generated and executed the following SQL query through the provided tool:

```sql
SELECT Country, COUNT(*)
FROM singer
GROUP BY Country;
```

It then interpreted the database results and provided a correct natural-language answer.

This preliminary example demonstrates that a relatively small, locally executed language model can perform a complete Text-to-SQL ReAct cycle without relying on commercial APIs.

## Computational Performance

Inference speed depends heavily on the available hardware, model size, quantization, context length, and number of generated tokens.

CPU-only inference is supported, but a complete agent turn may take several minutes on less powerful computers. Compatible GPUs can considerably accelerate inference.

To inspect the hardware currently used by Ollama, run:

```bash
ollama ps
```

Students are encouraged to experiment with different models and configurations, observing the trade-offs between accuracy, latency, memory consumption, and computational efficiency.

## Alternative Inference Providers

Students may also use cloud-based inference providers.

| Provider | Cost | API Key | Inference |
|---|---|---|---|
| Ollama | No API fees | No | Local |
| GroqCloud | Free tier available | Yes | Cloud |
| OpenAI | Pay-as-you-go | Yes | Cloud |

**GroqCloud.** [Groq](https://console.groq.com/) provides fast cloud inference for several open-weight language models. Its free tier does not require a payment method but is subject to usage limits.

```python
from langchain_groq import ChatGroq

llm = ChatGroq(
    model="openai/gpt-oss-20b",
    temperature=0
)
```

A personal `GROQ_API_KEY` is required.

**OpenAI.** Students who already have access to OpenAI API credits may use the original model configuration provided in the notebooks.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-5.4-mini")
```

A personal `OPENAI_API_KEY` with available credit is required.

Model availability, pricing, and free-tier limits may change over time. Always consult the official provider documentation.

## Educational Perspective

The objective of these notebooks is not to promote a specific language model or inference provider, but to understand how LLM-based conversational agents are designed, implemented, and evaluated.

The same agent architecture can operate with different language models, allowing students to investigate how model capabilities and computational resources affect overall agent performance.

**Building effective conversational agents does not necessarily require expensive computational resources. Thoughtful engineering, semantic grounding, and efficient resource management are equally fundamental.**

## Automatic GPU Acceleration

Ollama automatically detects and uses compatible GPUs when available. No additional Python code or CUDA configuration is required within the educational notebooks.

If GPU memory is insufficient, Ollama may distribute the model across the GPU and CPU.

Students can verify hardware utilization by running:

```bash
ollama ps
```

GPU acceleration can significantly reduce inference latency and enable experimentation with larger language models.

For further information, consult the [official Ollama hardware support documentation](https://docs.ollama.com/gpu).







