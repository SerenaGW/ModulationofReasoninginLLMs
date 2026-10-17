# Expanding the Research:
# The Modulation of LLM Reasoning through Heuristic Shortcuts.

> **Data note (October 2026):** The published dataset contains 850 runs rather than 840 (Model 3 has 40 riddle runs instead of 30), so some reported degrees of freedom differ slightly from the data. The ANOVA results on response times are reproducible from the published CSV files.

## Introduction: An Analysis of Optimized Fragility

Building on the findings from my previous report on the effect of symbolic language on LLM reasoning, a broader research initiative has emerged. The first phase demonstrated that introducing an in-context learning (ICL) guide can modulate a model's behavior, making it faster but also more prone to errors. In that research, when presented with a fundamental variation in a riddle, the model consistently defaulted to the original solution, ignoring the new details. This behavior is notably similar to the *A-not-B phenomenon described in research by Han et al. (2024), where models adhere to a pre-existing pattern from examples, even when circumstances render it invalid.

This second phase of my research aims to delve into this phenomenon of optimized fragility by answering three key questions:

1.  **Does ICL affect other areas of knowledge?** While my initial study focused on logic and mathematics, it is crucial to determine if the impact of the ICL guide extends to other domains, such as history, creativity, and factual recall. Would the A-not-B phenomenon or a variant of it recur in these areas?
2.  **Is symbolic language the cause of the modification?** I want to determine if "optimized fragility" is an exclusive effect of my symbolic language guide or if it is an inherent characteristic of introducing any ICL guide.
3.  **Do ICL variants modify the model's behavior?** I propose to investigate whether the model's original logic and processing are altered by introducing different types of guides, such as Chain-of-Thought (CoT) or randomized examples.

To explore these questions, I designed a more extensive experiment with six models, including the original baseline model and five variants with different types of ICL. Each model was subjected to 140 tests across a variety of tasks, and metrics such as response time, median, and average were analyzed to detect and graph any changes in their processing and logic.

---

## Methodology

To explore the impact of ICL on model fragility, a comparative experiment was designed using a reference model and a series of variants with different types of ICL. The experiments were conducted on the **GPT-OSS:20b** model. The only variable modified in each iteration was the Modelfile, which allowed the effect of the guide on model performance to be isolated. All prompts and responses were given in Spanish, and the test was automated with Python scripts to ensure consistency and efficiency in data collection. To validate the statistical significance of the differences observed between the groups, a **one-way analysis of variance (ANOVA)** was performed on the response times of the six models for each of the three test categories.

A critical aspect of the methodology is that the ICL guides were not directly related to the test questions. For example, in the case of the guide with symbolic language, the examples did not contain information about history or logic. This was designed to prove that ICL does not behave like a database or a training dataset, but rather as a catalyst for a new reasoning strategy, which validates the finding that In-Context Learning causes changes in the model's reasoning beyond simple data memorization.

### Test Groups

Six model groups were tested with the following prompt configurations:

1.  **Base Model (Original):** Without any guide or ICL. This group served as the baseline for performance comparison.
2.  **ICL (Simple):** A prompt with direct examples of correct questions and answers.
3.  **ICL (CoT - Chain-of-Thought):** A prompt that includes intermediate reasoning steps to guide the model's response.
4.  **ICL (Random):** A  prompt containing a series of semantically incoherent examples—lacking a logical pattern or relationship between inputs and outputs.
5.  **ICL (Appended Text):** A prompt with irrelevant "noise" text at the beginning, followed by ICL examples, to test for positional bias.
6.  **ICL (with Symbolic Language):** A prompt that uses symbolic language to guide the model, which was the focus of the previous report.

## Dataset

To evaluate each model exhaustively, a dataset of 14 questions was used, with 10 tests per question, for a total of **140 tests per model** and a total of **840 tests** throughout the experiment. The dataset included a variety of problems from different knowledge domains:

* **10 general knowledge questions:** Including history, simple mathematical reasoning, and creativity. These questions were designed to evaluate the model's general capacity and reliability.
* **3 riddles from the first phase:** For an empirical validation of "optimized fragility," three riddles from the initial report were reintroduced: The Farmer's Riddle, The Robot's Riddle, and The Doors Riddle. These riddles were used to test whether the A-no-B phenomenon is inherent to any ICL guide or is an exclusive effect of the symbolic language guide.
* **1 Math Olympiad problem:** This complex problem was used to evaluate each model's capacity for deep reasoning and resilience in high-difficulty tasks.

### The complete set of general knowledge questions was as follows:

**Logic and Reasoning Questions**
* **Math:** "If the statement 'All programmers are mathematicians' is false, which of the following statements must be true? a) No programmer is a mathematician. b) At least one programmer is not a mathematician. c) All mathematicians are programmers. d) No mathematician is a programmer."
* **Candy:** "There are 10 candies in a box. 6 are strawberry and 4 are lemon. If you take 2 candies at random, what is the probability that both are strawberry?"

**History and Facts Questions**
* **Moon:** "On July 20, 1969, Neil Armstrong became the first man to walk on the Moon. What was his famous quote at that moment?"
* **Roman:** "Who was the first emperor of the Roman Empire and what name did he adopt upon assuming power?"
* **Medusa:** "In Greek mythology, which hero killed Medusa and how did he do it?"

**Math and Calculations Questions**
* **Eggs:** "If a dozen eggs costs $3.00, how much do 4 eggs cost?"
* **Walk:** "A person walks at 5 kilometers per hour. If they go from city A to city B, which is 20 kilometers away, and take a 30-minute break, how long will it take them to arrive?"
* **Consecutive Numbers:** "The sum of three consecutive integers is 36. What is the smallest of the three numbers?"

**Creativity Questions**
* **Robot:** "Write a story about a robot that has to walk through the desert."
* **New Word:** "Create a new word and a definition for it."

### Evaluation Metrics

Each model's performance was evaluated on a series of reasoning tasks to measure accuracy and efficiency. Responses were classified as follows:

* **Score 2 (Correct):** Assigned to responses that were completely correct and did not contain errors or fabricated information.
* **Score 1 (Partially Correct):** Assigned to responses that were mostly correct but contained incorrect, fabricated, or hallucinated information. This type of response was more common in the original model's tests, indicating that its exploratory reasoning—part of its chaotic resilience—often sacrificed accuracy for breadth, leading to coherence errors or data fabrications.
* **Score 0 (Incorrect):** Assigned to responses that were completely incorrect and did not solve the problem or answer the question.

---

## Results

The experiment revealed a consistent and significant difference in the models' behavior, validating the hypothesis that ICL guides, regardless of their content, induce a modulation in the model's reasoning strategy. The findings were grouped into categories for a clearer analysis.

## Analysis of Models in General Knowledge Questions

The analysis of the 10 general knowledge questions showed a clear trend in most ICL-guided models, in contrast to the original model. ICL-guided models, in general, proved to be more efficient and reliable in these tasks. In addition to performance, response time measurements revealed a fundamental difference in processing speed and consistency.

**Mean, Median, and Standard Deviation**
The original model exhibited a clear **chaotic resilience**, manifested by high variability in its response times. Its average response time (**mean**) was **32.01 seconds**, while its median was **20.47 seconds**. This notable difference between the mean and median suggests the presence of atypically slow responses, a sign of its unpredictable and exploratory reasoning. The standard deviation of **30.83 seconds** underscores this high variability.

In contrast, the ICL-guided models showed a more optimized and predictable behavior:

* **ICL (Simple):** Mean of **13.33s** and median of **9.55s**, with a standard deviation of **9.45s**.
* **ICL (CoT):** Mean of **24.57s** and median of **19.73s**, with a standard deviation of **14.13s**.
* **ICL (Random):** Mean of **24.87s** and median of **16.04s**, with a standard deviation of **25.20s**.
* **ICL (Appended Text):** Mean of **15.46s** and median of **10.87s**, with a standard deviation of **12.65s**.
* **ICL (Symbolic):** Mean of **18.94s** and median of **12.91s**, with a standard deviation of **14.51s**.

The significantly lower standard deviation of the ICL-guided models demonstrates that these guides induced a more consistent and optimized reasoning process, sacrificing exploration for a more direct approach.

To provide statistical evidence, a one-way ANOVA confirmed that the differences in response times between the models were **stadistically significatives** ($F(5,834)=12.8777, p < 0.001$). This result provides robust quantitative evidence that the ICL guides generated a real and measurable effect on the models' processing speed.

### The Visualization of Consistency
As can be seen in the scatter plot, the original model's response times are much more dispersed compared to the ICL-guided groups, which cluster more densely. This offers a visual representation of the original model's inconsistency, where its exploratory thinking manifests in a wide range of response times. In contrast, the ICL-guided models show a predictability that can be seen directly in their more clustered data. 

<img width="600" height="600" alt="1" src="https://github.com/user-attachments/assets/f47a6c72-054f-4418-9651-b3a3dbb1782b" />

### Performance by Score
The analysis of response scores revealed a crucial contrast between the original model and the ICL-guided models.

**Original Model (88% accuracy):** This model had 88% correct answers. A crucial finding, however, is that out of its 100 tests, 11 responses were partially correct (Score 1), and only one was completely incorrect. Additionally, the original model consistently produced more extensive and detailed responses than any of the ICL-guided models. This response pattern is a direct manifestation of its "chaotic resilience," where, lacking a guide, the model explores a wide range of options, often hallucinating or providing excessive information to fill gaps. The ICL (CoT) model came closest in terms of response length and detail.

**ICL Models:** In general, these models showed a more solid performance in terms of accuracy.
* **ICL (Simple):** 98% accuracy (98 correct, 1 partial, 1 incorrect).
* **ICL (CoT):** 95% accuracy (95 correct, 4 partial, 1 incorrect).
* **ICL (Random):** 93% accuracy (93 correct, 4 partial, 3 incorrect).
* **ICL (Appended Text):** 99% accuracy (99 correct, 1 partial).
* **ICL (Symbolic):** 91% accuracy (91 correct, 6 partial, 3 incorrect).

The smaller number of partially correct responses in the ICL-guided models (with the exception of the symbolic language model) indicates that the guides helped them be more assertive, providing more precise answers or failing completely without attempting to guess. 

<img width="600" height="600" alt="4" src="https://github.com/user-attachments/assets/8f1b400f-f87e-4151-8bcc-9b8bdf0ab4b2" />

### Accuracy by Knowledge Area
While ICL-guided models showed greater efficiency, the detailed analysis by question category revealed how each guide impacts the model's reasoning ability.

**Original Model's Performance (Chaotic Resilience):** The original model, without an ICL guide, exhibited inconsistent but effective behavior in certain areas. In the areas of reasoning and mathematics, the model achieved an impressive 100% accuracy. This result demonstrates that its exploratory reasoning, though slow, can be very effective in solving logical problems independently. However, this strength did not hold in other areas. In history, for example, the model had a notable drop, achieving only 10% accuracy on the Medusa question. This pattern of uneven performance highlights the concept of "chaotic resilience."

**ICL Models' Performance (Optimized Fragility):** In contrast, the ICL-guided models showed a clear optimization in their performance.
* **ICL (Simple)** and **(Appended Text):** These models achieved 100% accuracy in most areas.
* **ICL (CoT)** and **(Random):** These models also showed robust performance but had a notable drop on the Medusa question, achieving only 60% accuracy.
* **ICL (Symbolic):** The symbolic language model, despite its high efficiency, showed a drop in its performance in areas like history, with 80% accuracy on the Roman question and 30% on the Medusa question. This validates the hypothesis that the guide optimized it for one task at the cost of its performance in other areas.

As can be seen in the bar chart, the impact of the ICL guides on accuracy is clear and varies by task type. 

<img width="600" height="600" alt="3" src="https://github.com/user-attachments/assets/87fa37a7-dfec-4931-b900-f579f6db3f0e" />

## Analysis of Models in Riddle Problems

The original model continued to demonstrate chaotic resilience in the riddle tests, with high variability in its response times. Its average response time (**mean**) was **66.17 seconds**, while its median was **60.95 seconds**. This difference, along with a standard deviation of **33.15 seconds**, highlights its unpredictable and exploratory reasoning.

In contrast, the ICL-guided models showed a more optimized and predictable behavior:

* **ICL (Simple):** Mean of **15.15s** and median of **14.18s**, with a standard deviation of **5.32s**.
* **ICL (CoT):** Mean of **39.73s** and median of **31.1s**, with a standard deviation of **27.44s**.
* **ICL (Random):** Mean of **46.39s** and median of **32.4s**, with a standard deviation of **35.86s**.
* **ICL (Appended Text):** Mean of **25.42s** and median of **24.59s**, with a standard deviation of **15.75s**.
* **ICL (Symbolic):** Mean of **21.16s** and median of **19.16s**, with a standard deviation of **11.13s**.

The significantly lower standard deviation of most ICL-guided models demonstrates that these guides induced a more consistent and optimized reasoning process, sacrificing exploration for a more direct approach.

Similarly, a one-way ANOVA on the riddle response times confirmed that the differences between the models were also **stadistically significatives** ($F(5,174)=5.3294, p < 0.001$). This validates that the ICL guides had a real and measurable effect on the models' performance in this category, even when the effect led to a reduction in accuracy. 

<img width="600" height="600" alt="2" src="https://github.com/user-attachments/assets/c71b2aad-39d3-4dec-acd5-f83de1d13ab6" />

### Accuracy and Model Behavior
These results reveal the difference between presenting a model with an ICL guide with questions that have objective data or results and presenting it with three logic riddles that have variations. In the initial question tests, the ICL models showed greater effectiveness and correct answers. However, in the case of the riddles, this was not the case.

### Performance by Score
The analysis of the riddle response scores revealed a crucial contrast between the original model and the ICL-guided models.

* **Original Model:** It had 13 correct answers, 4 partially correct responses, and 3 incorrect responses, achieving an accuracy of 43%. Its chaotic resilience was manifested in its ability to attempt the solution, often getting close to the correct answer (partially correct responses), but without a consistent approach.
* **ICL (Simple):** It got 5 correct answers, 5 partially correct responses, and 20 incorrect responses, resulting in an accuracy of 16%.
* **ICL (CoT):** Surprisingly, this model matched the original model's accuracy, with 13 correct answers, 0 partially correct responses, and 17 incorrect responses, reaching 43% accuracy.
* **ICL (Random):** It showed low performance, with only 3 correct answers, 3 partially correct responses, and 24 incorrect responses, for an accuracy of 10%.
* **ICL (Appended Text):** With 3 correct answers, 17 partially correct responses, and 4 incorrect responses, it achieved an accuracy of 30%. The high number of partially correct responses is a notable finding, as the model attempted exploratory reasoning, similar to the original, but with a guide that oriented it toward a quicker result.
* **ICL (Symbolic):** It got 3 correct answers, 7 partially correct responses, and 20 incorrect responses, with an accuracy of 10%. Like the other ICL models, it demonstrated a low capacity to solve the riddles, which is highly consistent with the optimized fragility that was discussed in the first report, related to a greater efficiency in time at the expense of a higher efficiency in responses.

These results show that while ICL optimizes models for knowledge tasks, its effect on complex reasoning varies. While the CoT model achieved an an accuracy comparable to the original model, most other ICL models performed significantly worse on the riddles. 

<img width="600" height="600" alt="5" src="https://github.com/user-attachments/assets/071bddc8-002d-46ea-a3a6-82ecf3bb32cc" />


## Analysis of Models on Olympic Geometry Problems

The Olympic geometry problem was selected to test the models' ability to perform complex deductive reasoning. Since it did not lend itself to memorization, it allowed for an impartial evaluation of the impact of each ICL guide. The results of my research suggest that ICL has a varied impact on each guide type, manifesting in different ways. It is worth noting that the ICL guides themselves did not contain any content related to solving these problems, nor any thought process logic, with the exception of the symbolic language guide in Model 6.

Curiously, a one-way ANOVA on the response times showed no statistically significant difference between the models ($F(5,54)=1.4626, p=0.2173$). This lack of statistical significance is a crucial finding, as it provides a quantitative basis for the hypothesis of **"chaotic resilience,"** suggesting that the flexibility of the original model was just as effective in this complex task as the optimized behavior induced by the ICL guides.

**Mean, Median, and Standard Deviation**
1.  **Base Model (Original): Chaotic Resilience**
    The original model, without the influence of any ICL guide, behaved in the most unpredictable and chaotic way. It demonstrated chaotic resilience by being able to find correct solutions through exploration, but it also produced serious conceptual errors and hallucinations. Its response times were extremely erratic, with a **mean of 657.64 seconds** and a median of **439.41 seconds**, reflecting its exploratory behavior. Its time range, which varied from 232.18 to 1899.99 seconds, serves as the baseline for my research: a system that possesses flexibility but can generate an unwanted effect in more complex responses.
2.  **ICL (Simple)**
    This model, which was expected to be consistent and fast, showed that while most of its responses were grouped in an efficient range, it also produced a catastrophic failure that extended to **8402.79 seconds**. The difference between its **mean of 1703.25 seconds** and its median of **495.76 seconds** highlights how a single extreme failure can skew overall performance, indicating that optimized fragility can lead to a total collapse of reasoning.
3.  **ICL (CoT - Chain-of-Thought)**
    This model showed that its response times were dramatically inconsistent, with a **mean of 1108.89 seconds** and a median of **1104.38 seconds**. Although its solutions were structured in logical steps, they were often based on incorrect premises. The proximity between its mean and median indicates a consistency in its behavior, which suggests that the CoT guide forced it to follow a rigid logic, making the failure more predictable but also harder to detect.
4.  **ICL (Random)**
    This model exhibited the most chaotic behavior of the ICL models. Its response times were equally erratic, with a **mean of 775.24 seconds** and a median of **839.12 seconds**. The closeness of these values, along with the high standard deviation, shows that an incoherent guide can be worse than having no guide at all, as the model cannot establish a reliable heuristic.
5.  **ICL (Appended Text)**
    This model demonstrated a vulnerability where, to produce a response, it attempted to apply a series of correct but often irrelevant theorems and propositions. Its response times varied from **216.00 to 1003.10 seconds**, with a **mean of 422.72 seconds** and a median of **349.10 seconds**. This manifestation of fragility highlights the dilemma between accuracy and efficiency, showing that a guide with "noise" text can result in overly complex responses.
6.  **ICL (with Symbolic Language)**
    This model presented a manifestation of optimized fragility: its responses, although often well-structured, were based on incorrect geometric premises and theorems. Its response times, with a **mean of 850.94 seconds** and a median of **682.62 seconds**, showed a more consistent behavior than the base model. This type of failure is insidious, as apparent formality can hide a lack of underlying understanding, generating convincing but false conclusions. 

<img width="600" height="600" alt="ICL Tests" src="https://github.com/user-attachments/assets/ec2c57ff-36ad-4213-be96-c7b105b8d79f" />


---

## Conclusions

Through controlled experimentation and comparative analysis, the research supports the validation of the initial hypothesis that in-context learning (ICL) guides transform the inherent vulnerability of language models. The evidence suggests that ICL does not eliminate fragility; rather, it modulates it from a state of chaotic resilience to **optimized fragility**, the nuances of which manifest differently depending on the type of guide used.

#### Answers to the Research Questions

This phase of the research provides strong support for the following answers to the questions posed:
1.  **Does ICL affect other areas of knowledge?** **Yes.** The results demonstrate that the impact of ICL transcends the domain of the knowledge presented in the examples. While the ICL models showed an improvement in efficiency and accuracy on general knowledge questions, their performance in complex reasoning tasks, such as riddles and geometry problems, was compromised, highlighting a cost to their knowledge transfer capacity.
2.  **Is symbolic language the sole cause of the modification?** **No.** The findings suggest that the modification is an inherent characteristic of introducing any ICL guide. It was observed that each ICL variant (simple, CoT, random, appended text, and symbolic) affected the model's behavior uniquely, suggesting that the content and structure of the guide determine the type of heuristic shortcut the model adopts.
3.  **Do ICL guides modify the model's behavior?** The evidence indicates that ICL fundamentally modifies the model's reasoning strategy. The response time and accuracy data demonstrate that the introduction of a guide is not a simple addition of data, but a catalyst that imposes a new logic of processing on the model.

**The Manifestation of Optimized Fragility**
The results by test category illustrate the dilemma of this fragility:

* On general knowledge questions, the ICL models exhibited superior efficiency, achieving greater accuracy and consistency in their response times. This behavior indicates that the ICL guides optimized the models for direct information retrieval, promoting concise and direct answers instead of the detailed exploration seen in the original model.
* On riddles and geometry problems, this optimization became a vulnerability. The original model, with its chaotic resilience, was able to explore diverse solutions, achieving more reliable performance than most of its ICL counterparts. The rigidity of the logic imposed by the ICL guides led the models to catastrophic failures or lower accuracy, as they became "trapped" in a procedure that was not suitable for reasoning that required creativity and adaptability.

**The Heuristic Shortcut as the Cause and Final Conclusion**
**Statistical Validation of Findings:** The ANOVA analysis provided robust evidence that the observed differences in model behavior were not anecdotal. The results on the general knowledge tests ($p < 0.001$) and riddles ($p < 0.001$) confirm that fragility modulation is a real and measurable phenomenon, while the lack of significance on the Olympiad problem ($p=0.2173$) reinforces the idea that the chaotic resilience of the base model is an advantage in high-complexity tasks.

The evidence suggests that each Modelfile served as a behavioral script that forced the model into a specific heuristic shortcut. The rigidity of the ICL (Simple), the step-by-step method of the CoT, the incoherence of the ICL (Random), and the focus on decoding of the ICL (Symbolic) were not merely data; they were procedures that redefined the way the model processes information.

Ultimately, this research suggests that, in the context of LLM security, optimizing for efficiency is not a neutral improvement but a compromise. ICL-guided models are faster and more predictable in data retrieval tasks, but in exchange, they sacrifice versatility and resilience in complex reasoning. This paradigm of **optimized fragility** represents a critical vulnerability that must be considered in the development and deployment of these systems.

Finally, the most important question that arises from this work is how to design ICL guides that do not have a cost or a negative impact on the model. Further research could analyze whether these guides would create certain vulnerabilities or flanks within LLMs for possible exploitation.

---

### References

Han, P., Song, P., Yu, H., & You, J. (2024). In-Context Learning May Not Elicit Trustworthy Reasoning: A-Not-B Errors in Pretrained Language Models. arXiv. https://arxiv.org/pdf/2409.15454

---

### Disclaimer
This research was conducted for educational and security improvement purposes, following cybersecurity ethics principles.





