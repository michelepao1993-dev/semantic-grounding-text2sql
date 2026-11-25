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







