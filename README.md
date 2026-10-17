# ICL Optimized Fragility: How In-Context Learning Guides Change an LLM's Behavior

Two experiments on whether in-context learning (ICL) guides, a few examples placed in a model's context, change how an open-source model (gpt-oss-20b) answers questions, including questions unrelated to the guide.

The second study is published as a preprint on arXiv: [ICL Optimized Fragility (arXiv:2510.00300)](https://arxiv.org/abs/2510.00300).

> **Scope:** both studies use a single model (gpt-oss-20b), a small set of questions and prompts in Spanish. The results describe this setup and should be tested on other models before generalizing.

---

## Key terms

- **Optimized fragility:** the pattern I observed where a model with an ICL guide answers faster and more consistently, but less accurately on problems with subtle variations.
- **Chaotic resilience:** the base model's slower, more variable behavior, which in these tests solved some of those problems more often.

---

## Study 1: A symbolic-language guide ([Report1](./Report1))

**Setup:** the base model vs. the same model with a 15-example ICL guide written in a symbolic language. Three logic riddles with subtle variations (from Williams et al., 2024), 50 runs each per model, plus a Math Olympiad problem (10 runs each).

**Results (reproducible from [the data](./Report1/DATASET1)):**

| | Base model | Model with ICL guide |
| --- | --- | --- |
| Correct answers on riddles | 87 / 150 (58%) | 25 / 150 (17%) |
| Mean response time on riddles | 89 s | 36 s |

- The accuracy difference is statistically significant (Fisher's exact test, p < 0.001) and appears in each of the three riddles separately.
- The model with the guide was also significantly faster (Mann-Whitney U test, p < 0.001).
- In other words: the guide, which had nothing to do with the riddles, made the model faster but much less accurate on them.

## Study 2: Comparing five types of ICL guides ([Report2](./Report2))

**Setup:** six configurations of the same model: base, and guides of five types (simple, chain-of-thought, random, appended noise text, symbolic language). Each was tested on 10 general-knowledge questions, the same 3 riddles and 1 Olympiad problem, with 10 runs per question.

**Results:**

- **Response times** differed significantly between configurations on general questions and riddles (one-way ANOVA, p < 0.001), but not on the Olympiad problem (p = 0.22). These results are reproducible from the published data.
- **Accuracy:** on general questions, the guided models scored 91–99% vs. 88% for the base model. On riddles, most guided models dropped to 10–30%, while the base model and the chain-of-thought model reached 43%. These accuracy figures come from my manual grading and have not yet been tested statistically.

---

## Limitations

- One model only, and all prompts in Spanish.
- Few distinct questions (3 riddles, 1 Olympiad problem): repeated runs measure the model's variability, not whether the effect holds for other problems.
- Answers were graded by one person (me), without a second reviewer.
- Response times depend on hardware and answer length.
- In Study 2, the manual grades are not yet included in the dataset, so the accuracy results cannot be verified by others.

## Next steps

- Add the manual grades to the Study 2 dataset and test the accuracy differences statistically.
- Repeat the experiment with more riddles and with other models.

---

## Repository contents

- `Report1/`: first study (report, ICL guide in the Modelfile, results CSVs, and excerpts of the model's reasoning).
- `Report2/`: second study (report, the five Modelfiles, and results CSVs per model and test).

All raw data and configurations are public so the results can be checked and replicated.

## Reference

Gomez Wannaz, S. (2025). *ICL Optimized Fragility.* arXiv preprint [arXiv:2510.00300](https://arxiv.org/abs/2510.00300).

Riddles adapted from: Williams, S., Huckle, J., et al. (2024). *Easy Problems That LLMs Get Wrong.* arXiv.
