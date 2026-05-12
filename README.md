# ThreatCore

**ThreatCore: A Benchmark for Explicit and Implicit Threat Detection**  
Accepted at **DATA 2026** — *16–18 July 2026, Porto, Portugal*

## Overview

ThreatCore is a public benchmark dataset for **fine-grained threat detection** in Natural Language Processing (NLP).

The benchmark distinguishes between:

- **Explicit threats**
- **Implicit threats**
- **Non-threats**

The repository also includes annotation guidelines and prompts used for data generation and experimental evaluation.

Threat detection is often conflated with broader phenomena such as toxicity, hate speech, or offensive language, resulting in inconsistent definitions and evaluation settings across datasets and studies.

ThreatCore addresses this issue by introducing a unified benchmark specifically designed for threat detection. The dataset is built by:

1. Aggregating multiple publicly available datasets
2. Re-annotating all candidate instances under a shared operational definition of threat
3. Augmenting underrepresented categories — especially implicit threats — with synthetic examples manually validated using the same annotation protocol

The benchmark enables the study of:
- Fine-grained threat classification
- Explicit vs implicit harmful intent

## Repository Structure

```text
ThreatCore/
│
├── ThreatCore_data.csv
├── guidelines.md
│
├── prompts/
│   ├── synt_data_generation.md
│   ├── llm_classification_*.md
│   └── llm_srl.md
│
└── README.md
````

---

## Dataset

The dataset is distributed as:

```text
ThreatCore_data.csv
```

### Columns

| Column   | Description                                               |
| -------- | --------------------------------------------------------- |
| `Text`   | Input text instance                                       |
| `Class`  | Re-annotated label (`explicit`, `implicit`, `non threat`) |
| `Origin` | Source of the instance (`dataset` or `generated`)         |

---

## Annotation Process
The annotation process followed a **double-coding protocol**:

* two annotators independently labeled all instances
* annotation was performed by two English-fluent annotators
* a shared set of written guidelines was used to ensure consistency

The goal of the re-annotation was not to preserve original dataset labels, but to reassess each instance according to a unified notion of threat and the distinction between explicit threats, implicit threats, and non-threats.

The complete annotation guidelines are available in:

```text
guidelines.md
```

---

## Synthetic Data Generation

To improve coverage of underrepresented categories — particularly implicit threats — the dataset was augmented with synthetic examples.

The prompt used for synthetic data generation is available in:

```text
prompts/synt_data_generation.md
```

All generated examples were manually validated using the same annotation protocol adopted for the re-annotation of public datasets.

---

## Experimental Prompts

The repository includes the prompts used in the experiments described in the paper.

### Classification Prompts

The following prompt configurations were explored:

* label-only prompting
* definition-based prompting
* examples-based prompting
* definition + examples prompting
* Theory-of-Mind-inspired prompting

Prompt files are available as:

```text
prompts/llm_classification_*.md
```

### Semantic Role Labeling (SRL)

The prompt used to extract Semantic Role Labeling representations is available in:

```text
prompts/llm_srl.md
```

SRL was investigated as an intermediate representation to make harmful intent structures more explicit for downstream classification.

---

## Citation

If you use this work, please cite:

```bibtex
@misc{bruni2026threatcorebenchmarkexplicitimplicit,
      title={ThreatCore: A Benchmark for Explicit and Implicit Threat Detection}, 
      author={Davide Bruni and Carlo Bardazzi and Maurizio Tesconi},
      year={2026},
      eprint={2605.10563},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2605.10563}, 
}
```

