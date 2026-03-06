# Model Card - Persistent Open-1

**Model Series:** Persistent Open-1

**Organization:** Persistent Research

**Version:** 1.0.0

**Release Date:** 2026 Q2

**License:** Apache 2.0

---

## Model Overview

Persistent Open-1 is the first open-weight language model series from Persistent Research - a frontier AI research company built in India. The series consists of three model sizes designed to deliver competitive performance at a fraction of standard training compute, trained with an efficiency-first methodology and released openly for the global research community.

| Model | Parameters | Context Window | Architecture | Status |
|---|---|---|---|---|
| Persistent-Open-1-1B | 1.3B | 8,192 tokens | Decoder-only Transformer | Coming Soon |
| Persistent-Open-1-3B | 3.2B | 16,384 tokens | Decoder-only Transformer | Coming Soon |
| Persistent-Open-1-7B | 7.3B | 32,768 tokens | Decoder-only Transformer | Coming Soon |

---

## Intended Use

### Primary Intended Uses

- **Research:** Academic and industrial research in natural language processing, model efficiency, and AI capabilities
- **Benchmarking:** Evaluation of language model capabilities across standard and custom benchmarks
- **Fine-tuning:** Base models for task-specific fine-tuning across domains including code, science, and instruction following
- **Education:** Teaching and learning about large language model architectures and capabilities
- **Application development:** Building AI-powered applications via the Persistent API or local inference

### Primary Intended Users

- AI researchers and academics
- Independent developers and engineers
- Organizations evaluating open-weight language models
- Students and educators in AI and machine learning

### Out-of-Scope Uses

Persistent Open-1 models are not intended for and should not be used for:

- Generation of content designed to deceive, manipulate, or harm individuals
- Automated decision-making in high-stakes domains (medical diagnosis, legal judgment, financial advice) without human oversight
- Surveillance, profiling, or tracking of individuals without consent
- Generation of disinformation, propaganda, or synthetic media designed to mislead
- Any application that violates applicable laws or regulations
- Weapons development or any use that could cause physical harm

---

## Training Data

### Data Overview

Persistent Open-1 is trained on a curated multilingual corpus assembled through Persistent Research's six-stage data curation pipeline. The training data spans multiple domains and languages with a deliberate focus on quality over quantity.

### Data Sources

| Tier | Description | Approximate Proportion |
|---|---|---|
| Tier 1 - Licensed & Verified | High-quality licensed text from publishers and institutions | 25% |
| Tier 2 - Public Domain & Open | Permissively licensed public domain text and open datasets | 45% |
| Tier 3 - Synthetic | AI-generated training data, verified and quality-controlled | 20% |
| Tier 4 - Code | Open-source code repositories across 40+ programming languages | 10% |

### Data Processing Pipeline

All training data passes through the following six-stage pipeline before entering model training:

1. **Ingestion & Deduplication** - Raw data is ingested, normalised, and deduplicated using exact and near-duplicate detection to remove redundant content that degrades model diversity.

2. **Quality Scoring** - Each document is scored across factual density, linguistic clarity, structural coherence, and information novelty. Documents below quality thresholds are filtered.

3. **Toxicity & Harm Filtering** - Automated and human-reviewed filtering removes harmful, hateful, explicit, or otherwise unsuitable content. This is applied as a continuous process across all data batches.

4. **Diversity Balancing** - The corpus is analysed for topical, linguistic, demographic, and geographic diversity. Underrepresented domains and languages are upsampled. Overrepresented domains are capped.

5. **Verification Sampling** - A statistically significant sample of every data batch is manually reviewed by trained human reviewers before entering the training pipeline.

6. **Provenance Logging** - Every training document is logged with its source, license status, curation date, and pipeline pass record.

### Data Not Used

- User interactions or conversations without explicit consent
- Private documents or proprietary data
- Content from minors
- Data with unverifiable provenance or license status

### Languages

Persistent Open-1 has primary capability in English with meaningful capability across major world languages. Indian languages including Hindi, Telugu, Tamil, Kannada, Bengali, and Marathi receive specific attention in the training corpus.

| Language Group | Coverage |
|---|---|
| English | Primary |
| Indian languages (6 major) | Significant |
| European languages | Moderate |
| Other world languages | Limited |

---

## Training Procedure

### Architecture

Persistent Open-1 uses a standard decoder-only Transformer architecture with the following modifications:

- **Rotary Position Embeddings (RoPE)** for extended context handling
- **Grouped Query Attention (GQA)** for inference efficiency
- **SwiGLU activation function** for improved training stability
- **RMSNorm** for layer normalisation
- **Flash Attention 2** for memory-efficient attention computation

### Training Details

| Parameter | Value |
|---|---|
| Training framework | PyTorch with DeepSpeed ZeRO-3 |
| Precision | bfloat16 |
| Optimiser | AdamW |
| Learning rate schedule | Cosine with warmup |
| Context length during training | Model-specific (see table above) |
| Hardware | AWS Trainium2 + EC2 P4d instances |

### Training Tokens

| Model | Training Tokens |
|---|---|
| Persistent-Open-1-1B | 1.5 Trillion |
| Persistent-Open-1-3B | 2.5 Trillion |
| Persistent-Open-1-7B | 3.5 Trillion |

### Fine-tuning

All three models are released in two variants:

- **Base:** Pre-trained base model for researchers and fine-tuning workflows
- **Instruct:** Instruction-tuned variant using RLHF and DPO for general assistant use

---

## Evaluation

### Benchmark Results

*Results will be published upon model release. All evaluations are conducted using the Persistent Bench framework and are fully reproducible — evaluation code, prompt templates, and scoring methodology are published at github.com/persistent-research/persistent-bench.*

**Benchmarks evaluated:**

| Benchmark | Measures |
|---|---|
| MMLU | World knowledge and reasoning across 57 subjects |
| HellaSwag | Commonsense reasoning and sentence completion |
| ARC-Challenge | Science question answering |
| TruthfulQA | Factual accuracy and hallucination resistance |
| HumanEval | Code generation capability |
| GSM8K | Mathematical reasoning |
| BIG-Bench Hard | Challenging reasoning tasks |
| Persistent Bench | Our own evaluation framework |

### Evaluation Methodology

We evaluate on both standard public benchmarks and our own internal held-out evaluations. We explicitly evaluate for benchmark overfitting and publish results on held-out evaluations alongside standard benchmarks. All benchmark results are reproducible using our open-source evaluation framework.

### Limitations in Evaluation

Benchmark scores measure specific, narrow capabilities and do not fully capture real-world model performance. We caution against over-interpreting benchmark comparisons and encourage evaluation on task-specific data relevant to your use case.

---

## Risks and Limitations

### Known Limitations

**Factual accuracy:** Like all language models, Persistent Open-1 can generate factually incorrect information presented with apparent confidence. Users should verify important factual claims from authoritative sources.

**Temporal knowledge cutoff:** The model's knowledge has a training cutoff date. It does not have access to real-time information or events after this date.

**Mathematical reasoning:** While the model demonstrates meaningful mathematical reasoning capability, it is prone to errors in complex multi-step calculations. Outputs should be verified.

**Language quality variance:** Performance in non-English languages, particularly lower-resource languages, is meaningfully below English performance. Users should exercise additional caution when using the model in languages other than English.

**Hallucination:** The model may generate plausible-sounding but incorrect information, citations that do not exist, or confident-sounding claims that are false. This is a known limitation of the architecture class.

**Context limitations:** Performance may degrade on very long contexts approaching the maximum context window. Critical information should be positioned early in the context where possible.

### Bias and Fairness

Training data, despite careful curation, inevitably reflects societal biases present in text produced by humans. Persistent Open-1 may reproduce or amplify these biases in its outputs. Known areas of concern include:

- **Geographic and cultural bias:** Stronger representation of Western, English-language perspectives
- **Gender bias:** Potential reinforcement of gender stereotypes present in training data
- **Occupational bias:** Association of professions with demographic groups in ways that reflect historical inequities

We publish bias evaluation results alongside model release and will update this section as additional evaluation is completed.

### Safety

Persistent Open-1 includes safety training designed to reduce the likelihood of harmful outputs. However, no safety training is complete. The model may still produce harmful content under adversarial conditions or unexpected prompts. We recommend:

- Implementing application-level safety filters for production deployments
- Conducting red-team evaluation before deploying in sensitive contexts
- Monitoring model outputs in production
- Not relying solely on model-level safety for high-stakes applications

---

## Environmental Impact

### Compute and Carbon

We are committed to transparency on the environmental impact of model training. Estimated compute and carbon figures will be published at model release, calculated using the methodology from Patterson et al. (2021).

We train on AWS Trainium2 chips which are optimised for energy efficiency, and we offset compute carbon through verified carbon offset programmes.

---

## Citation

If you use Persistent Open-1 in your research, please cite:

```bibtex
@misc{persistentresearch2025open1,
  title        = {Persistent Open-1: Efficient Open-Weight
                  Language Models from Persistent Research},
  author       = {Persistent Research},
  year         = {2026 Q2},
  publisher    = {Persistent Research},
  url          = {https://persistentresearch.in},
  note         = {Model weights available at
                  huggingface.co/persistent-research}
}
```

---

## Model Access

| Access Method | URL |
|---|---|
| HuggingFace | huggingface.co/persistent-research |
| Persistent API | api.persistentresearch.in |
| Python SDK | `pip install persistent` |
| CLI | `persistent run open-1-7b` |
| GitHub | github.com/persistent-research/persistent-open-1 |

---

## License

Persistent Open-1 is released under the **Apache License 2.0**.

You are free to use, modify, and distribute the model weights and associated code for any purpose, including commercial use, subject to the terms of the Apache 2.0 license. See the LICENSE file for full terms.

**Note on acceptable use:** While the Apache 2.0 license is permissive, we ask that all users respect the intended use guidelines in this model card. Uses that cause harm to individuals or communities are contrary to the values of Persistent Research regardless of their technical permissibility under the license.

---

## Contact

| Purpose | Contact |
|---|---|
| Research inquiries | research@persistentresearch.in |
| Safety and security | security@persistentresearch.in |
| General | hello@persistentresearch.in |
| Press | hello@persistentresearch.in |

**Security disclosures:** Please do not report security vulnerabilities through public GitHub issues. Email security@persistentresearch.in directly.

---

## Version History

| Version | Date | Changes |
|---|---|---|
| 1.0.0 | 2026 | Initial model card - pre-release |

---

## Acknowledgements

Persistent Research thanks the open-source AI research community - particularly EleutherAI, Hugging Face, AI2, and the authors of the foundational papers and open datasets that make research like this possible.

---

*Persistent Research - persistentresearch.in*
*Built in India. Built for the world.*
