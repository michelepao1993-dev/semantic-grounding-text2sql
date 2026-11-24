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

git clone <PUBLIC_GITHUB_REPOSITORY_URL>

cd <repository_name>

```


2. Create a virtual environment


```bash

python -m venv .venv

source .venv/bin/activate

```


Windows:


```bash

.venv\Scripts\activate

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

├── database
├── train_spider.json
├── dev.json
└── ...

```


---

# Running Experiments


# Example: Spider Evaluation


```bash

python scripts/run_spider_eval.py

```


Additional configuration files may be placed under:


```text

configs/

```


---


# Evaluation Metrics

The framework supports both standard and relation-level metrics.


# Standard Metrics

- Execution Accuracy (EX)
- Exact Match (EM)
- Component Matching (CM)


# Relation-Level Metrics

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

The repository includes a notebook for reproducibility and analysis.


# Experiments.ipynb


Reproduces the main quantitative tables reported in the paper.

Includes:

- aggregation of experiment logs,
- metric computation,
- final comparisons,
- models,
- temperatures,
- candidate generation strategies,
- other setups.



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
- The repository avoids live API calls inside notebooks for reproducibility purposes.


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

If you use this repository, please cite:

@inproceedings{paolicelli2026semantic,
    title={Semantic Grounding over Brute-Force Inference: A Symbiotic Evaluation of Text-to-SQL Systems},
    author={Michele Paolicelli, Cataldo Musto, Giovanni Semeraro, Alessandro Crnjar, David Landi and Claudio Saccà},
    booktitle={Proceedings of AIxIA 2026},
    year={2026}
}
```


---


# License

This repository is released under the MIT License.

See:


```text

LICENSE

```


for details.


---


# Disclaimer

This repository is provided for research and reproducibility purposes. The implementation reflects the experimental setup described in the accompanying paper unless otherwise specified.



```

```



