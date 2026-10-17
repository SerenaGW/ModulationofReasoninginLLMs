 # Expanding the Research: The Modulation of LLM Reasoning through Heuristic Shortcuts

 > **Review note (October 2026):** This summary uses stronger language than the evidence supports. Phrases such as "validating the hypothesis" or "any ICL guide fundamentally modifies" should be read as observations on one model (gpt-oss-20b) with a small set of questions. See the main README for the results, limitations and what has been statistically tested.

## Project Overview

This repository presents the second phase of an ongoing research initiative into the fundamental impact of in-context learning (ICL) on the internal logic of Large Language Models (LLMs). Building on the concept of **Optimized Fragility**, this study investigates whether different types of ICL guides, beyond just a symbolic language, induce a fundamental shift in the model's reasoning strategy. The findings reveal that ICL acts as a **catalyst for heuristic shortcuts**, transforming the model's behavior from a state of **"chaotic resilience"** to a more efficient but brittle state of "optimized fragility." This research highlights a critical vulnerability and a new perspective on LLM security and evaluation.

---

## Introduction & Motivation

My previous research demonstrated that a minimal symbolic language prompt could fundamentally alter a model's logic, a finding that challenged conventional paradigms of model fine-tuning. This new investigation aims to expand on those findings by answering three core questions: Does ICL affect other domains of knowledge? Is symbolic language the sole cause of this modification? And do different types of ICL guides modulate the model's behavior in unique ways? The motivation for this work is to establish whether the **paradigm of optimized fragility** is an inherent and systematic behavior of LLMs when exposed to ICL, urging a reevaluation of current LLM security, robustness, and evaluation methodologies.

---

## Key Methodology

This research employs a comparative methodology to validate the hypothesis that any ICL guide, regardless of its content, fundamentally modifies an LLM's reasoning. The experiment was conducted on the GPT-OS 20B model using six distinct configurations, including a baseline and five ICL variants:
* **Base Model:** The original version without any ICL guide.
* **ICL Variants:** Models were tested with Simple, Chain-of-Thought (CoT), Random, Appended Text, and Symbolic Language guides.

To ensure reliability and exhaustiveness, each model was subjected to a comprehensive set of **140 tests** across various domains, including general knowledge questions, riddles, and a complex Math Olympiad problem. Key metrics such as response time (mean, median, and standard deviation) and accuracy were analyzed to quantify the changes in behavior.

---

## Data & Prompts

To ensure the reproducibility of the results and allow for the verification of my findings, the datasets and prompts used in the tests are included in this repository. The full dataset includes general knowledge questions and reasoning problems to test the model's versatility across different domains.

* **General Knowledge Questions:** A set of 10 questions covering mathematics, history, and creative tasks.
* **Riddles:** The three riddles from the first phase of research were used again to test for the `A-not-B` phenomenon.
* **Math Olympiad Problem:** A complex geometry problem was used to evaluate deep deductive reasoning and resilience.

---

## Key Findings & Impact

The experiments revealed a consistent and significant difference in the models' behavior, validating the central hypothesis and suggesting several key implications for the AI field:

* **The Heuristic Shortcut:** ICL guides force a model to adopt a new, optimized reasoning strategy. The rigidity of this process, while improving efficiency, introduces a critical vulnerability where the model becomes inflexible and brittle, particularly on complex tasks.
* **From Chaotic Resilience to Optimized Fragility:** The base model's flexible but erratic behavior (**chaotic resilience**) was systematically replaced by a more predictable and efficient but ultimately flawed behavior (**optimized fragility**).
* **Varied Manifestations:** The manifestation of this fragility varied depending on the type of guide. For example, the CoT model showed a consistent but often flawed logical process, while the Symbolic Language model demonstrated high efficiency but a significant drop in performance on other domains.
* **A New Evaluation Paradigm:** This research highlights the urgent need for new evaluation methodologies that can test for resilience and adaptability, not just for accuracy on a predefined dataset.

---

## Reproducibility and Raw Data

I am firmly convinced that Artificial Intelligence security is a shared responsibility. The complete raw data, examples of the models' `Thinking...` logs, and the modelfiles used for configurations will be made available in this repository. I invite other researchers and developers to replicate my experiment, analyze my data, and contribute their own findings. My goal is to collectively build a deeper understanding of these complex behaviors.

---

## Disclaimer

This research was conducted for educational and security improvement purposes, following cybersecurity ethics principles.
