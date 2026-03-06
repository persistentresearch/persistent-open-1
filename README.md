# Persistent Open-1

> Open-weight language models from Persistent Research

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![HuggingFace](https://img.shields.io/badge/🤗-Models-yellow)](https://huggingface.co/persistent-research)
[![Research](https://img.shields.io/badge/Research-persistentresearch.in-black)](https://persistentresearch.in)

## Models

| Model | Parameters | Context | Download |
|-------|-----------|---------|----------|
| Persistent-Open-1-1B | 1.3B | 8K | Coming Soon |
| Persistent-Open-1-3B | 3.2B | 16K | Coming Soon |
| Persistent-Open-1-7B | 7.3B | 32K | Coming Soon |

## About

Persistent Open-1 is the first open-weight
model series from Persistent Research - a
frontier AI research company built in India.

Trained with efficiency-first methodology,
Persistent Open-1 delivers competitive
performance at a fraction of standard
training compute.

## Quick Start

````
pip install persistent
````

next

````
from persistent import PersistentModel
````

model selection

````
model = PersistentModel("persistent-open-1-1b")
response = model.generate("Hello, world!")
````

## Model Card
See MODEL_CARD.md for full details on
training data, methodology, evaluation,
and known limitations.

## Citation
If you use Persistent Open-1 in your research:

@misc{persistentresearch2025open1,
  title={Persistent Open-1: Efficient Open
         Language Models},
  author={Persistent Research},
  year={2025},
  url={https://persistentresearch.in}
}

## License
Apache 2.0 — see LICENSE file.

## Contact
research@persistentresearch.in
