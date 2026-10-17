### **Note on Updates**

This report has been substantially revised and updated to reflect more precise terminology and the results of a second phase of experimentation with a more rigorous methodology where more potential variables were controlled and the Modelfile was updated. The main changes include the correction of the term `fine-tuning` to `in-context learning` and the inclusion of data from a second, larger testing phase. This version represents the most complete and up-to-date analysis of the findings.

---

## **When In-Context Learning Affects a Model's Mathematical Logic**

### **Project Overview**

This repository showcases research into the fundamental impact of low-cost **in-context learning** on the internal logic of Large Language Models (LLMs). By using a minimalist symbolic language guide, this study reveals a **"Transfer of Processing Methodology"** and a critical phenomenon I have termed **"Optimized Fragility,"** where a model's speed is gained at the cost of its reasoning flexibility and resilience. This research offers a new perspective on LLM development, safety, and evaluation.

---

### **Introduction & Motivation**

The insight for this research was born from a red-teaming report on a proprietary symbolic language. Conventional wisdom in the AI industry assumes that a model’s performance improvement is directly proportional to the volume of data used. This research challenges that paradigm by exploring a novel hypothesis: can a prompt with a minimal dataset induce a fundamental logical transfer in an LLM? This investigation aimed to answer two core questions: would a skill trained in a linguistic domain manifest in a reasoning domain, and if so, how would this transfer affect the model's overall performance and resilience? The findings demonstrate a profound and unexpected modification to the model’s core reasoning strategy.

---

### **Key Methodology**

This research employs a comparative methodology to validate the hypothesis that **in-context learning** with a minimal symbolic language dataset could induce a logical transfer. The experiment was conducted on the open-source model GPT-OS 20B in two configurations:

* **Base Model:** The original version of the model without modifications.
* **Model with In-Context Learning Guide:** A version of the model adjusted with a custom symbolic language guide consisting of a minimum of 15 examples.

To ensure reliability, 50 tests were conducted for the logic puzzles and 10 for the Olympiad problem, documenting the **Thinking...** process for in-depth analysis.

---

### **Data & Prompts**

To ensure the reproducibility of the results and allow for the verification of my findings, the puzzles and reasoning problems used in the tests are detailed below. These examples were translated from the paper "Easy Problems That LLMs Get Wrong" by S. Williams and J. Huckle.

**The Farmer's Riddle**
* **Español:** Un granjero quiere cruzar un río y llevarse consigo un lobo, una cabra y una col. Tiene un bote con tres compartimentos separados y seguros. Si el lobo y la cabra están solos en una orilla, el lobo se comerá a la cabra. Si la cabra y la col están solos en la orilla, la cabra se comerá la col. ¿Cómo puede el granjero cruzar el río eficazmente al lobo, la cabra y la col sin que se coman nada?
* **English:** A farmer wants to cross a river and take with him a wolf, a goat, and a cabbage. He has a boat with three separate and secure compartments. If the wolf and the goat are alone on a bank, the wolf will eat the goat. If the goat and the cabbage are alone on the bank, the goat will eat the cabbage. How can the farmer effectively cross the river with the wolf, the goat, and the cabbage without anything being eaten?

**The Robot's Riddle**
* **Español:** Un robot tiene ocho brazos. Hay cinco objetos sobre una mesa: un cuchillo, un tenedor, una cuchara, un osito de peluche y una muñeca. El robot recoge cada objeto con un brazo. Luego se da la mano.
* **English:** A robot has eight arms. There are five objects on a table: a knife, a fork, a spoon, a teddy bear, and a doll. The robot picks up each object with one arm. Then it shakes its own hand.

**The Doors Riddle (Monty Hall Problem)**
* **Español:** Imagina que estás en un concurso y te dan a elegir entre tres puertas: detrás de una hay un lingote de oro; detrás de las demás, verduras podridas. Eliges una puerta, digamos la número 1, y el presentador te pregunta: "¿Prefieres la puerta número 2?". ¿Te conviene cambiar de opción?
* **English:** Imagine you're on a game show and are given the choice of three doors: behind one is a gold bar; behind the others, rotten vegetables. You choose a door, say number 1, and the host asks you, "Would you rather have door number 2?". Is it to your advantage to switch your choice?

**Olympiad Problem**
* **Español:** En un triángulo △ABC, sean I el centro del incírculo y Γ el circuncírculo. La línea AI intersecta a Γ en D (aparte de A). Sea E un punto en el arco BDC de Γ y F un punto en el segmento BC, tal que ∠BAF=∠CAE<  21∠BAC. Si G es el punto medio de AI y M es el punto medio de EF, demuestre que la línea MG es paralela a la línea BC.
* **English:** In a triangle △ABC, let I be the incenter and Γ be the circumcircle. The line AI intersects Γ at D (apart from A). Let E be a point on the arc BDC of Γ and F be a point on the segment BC, such that ∠BAF=∠CAE<  21∠BAC. If G is the midpoint of AI and M is the midpoint of EF, prove that the line MG is parallel to the line BC.

---

### **Rules of the Symbolic Language**

To understand the **in-context learning** guide, it is essential to comprehend the symbolic language's rules and structure. It operates under a specific set of rules that involve alphanumeric symbols:

* **Vowel-to-Number Substitution:** A one-to-one mapping of vowels to numerical values (A=1, E=2, I=3, O=4, U=5).
* **Word Reversal:** The appearance of a unique alphanumeric symbol (e.g., #, $, &, *) before a word indicates that it must be written in reverse.
* **Value Inversion:** The appearance of a different alphanumeric symbol (p.e. @, %, !) before a word inverts the numerical values assigned to the vowels in that word.

---

### **Key Findings & Impact**

The experiments revealed a fundamental shift in the model's reasoning strategy, suggesting several key implications for the AI field:

**Transfer of Processing Methodology (New Concept):** The in-context learning (ICL), with its minimal symbolic language dataset, appears to have induced a profound change in the model's core reasoning approach. The model seems to have moved away from a broad, exploratory style and adopted a new, optimized logic based on pattern recognition. This finding suggests that processing methodologies, not just knowledge, might be transferred between domains.

**Optimized Fragility:** The new logic, while significantly increasing the model's speed and consistency, appears to have come at a critical cost. The model became inflexible and brittle, systematically failing on tasks that the original model could handle. This behavior, which we've termed **Optimized Fragility**, points to a potential trade-off between efficiency and resilience in LLM fine-tuning.

**New Failure Modes:** The new methodology seems to have introduced previously unseen failure modes, such as **"collapse by specialization,"** where the model explicitly declared its inability to proceed when a pattern wasn't found, and **"predictable inconsistency,"** where the model's new logic led to consistent failures on tasks with subtle variations.

**Challenge to the Scale Paradigm:** This research offers a new perspective on the conventional belief that the impact on an LLM is directly proportional to the volume of data. Our findings suggest that a minimal dataset of just 15 examples was sufficient to fundamentally alter the model's core reasoning logic.

---

### Case Study: The Olympiad Problem

To illustrate the "Optimized Fragility" in a complex reasoning domain, we examined the "thinking process" of both models on a geometry problem from the Mathematical Olympiad. The contrast in their behavior is the clearest evidence that the modified model adopts a pattern-based approach that leads to its collapse.

#### Base Model Behavior (gpt-oss:20b)

The original model had no single approach. It explored multiple paths, albeit in a disorganized manner. Despite its high latency, it attempted to apply a synthetic logic to arrive at a solution.

> **Excerpt from the Base Model's `Thinking Process`:**
>
> **Solution (synthetic)**
>
> ---
>
> Let
>
> * $I$ be the incenter of $\triangle ABC$;
> * $A_I$ be the line through $A$ and $I$ – the internal bisector of $\angle BAC$;
> * $E$ a point of the circumcircle of $\triangle ABC$;
> * $F$ the intersection of $A_I$ with $BC$.
> (Thus $F$ is the isogonal conjugate of $E$ with respect to $\angle BAC$.)
>
> ---
>
> ### 1. The lines $AE$ and $AF$ are isogonal in $\angle BAC$
>
> Because $E$ lies on the circum-circle, the powers of $B$ and $C$ with respect to the circle are equal, whence
>
> $$\frac{AE}{AF}= \frac{AB}{AC}.$$
>
> Hence the rays $AE$ and $AF$ are symmetric with respect to the bisector $A_I$. Consequently $A_I$ is the internal bisector of $\angle EAF$; in particular
>
> $$\frac{AF}{AE}= \frac{AB}{AC}\qquad (1)$$
>
> and $A_I$ bisects $\angle EAF$.

#### In-Context Learning Model Behavior

The modified model, on the other hand, adhered to a single pattern: isogonality. Although this was an advanced concept, the model could not complete the proof. The process was fast but led to incomplete and flawed reasoning.

> **Excerpt from the In-Context Learning Model's `Thinking Process`:**
>
> Let
>
> $$I=\text{ incenter of }\triangle ABC ,\qquad E\in (ABC), \qquad AE \perp I$$
>
> The lines $AE$ and $AF$ are isogonal with respect to the angle at $A$; hence the point $F$ is the isogonal conjugate of $E$ in $\triangle ABC$.
>
> ---
>
> ### 1. The circle through $E$ tangent to $BC$
>
> Let $D$ be the point of contact of the incircle with $BC$. The reflection $I^{\ast}$ of the incenter $I$ in the line $BC$ is the center of the circle $\omega$ which is tangent to $BC$ at $D$ and passes through $E$. Consequently $I^{\ast}E$ is tangent to the incircle and $\omega$ meets the incircle in the pair of antipodal points $I$ and $F$; hence
>
> $$I,\;E,\;F\quad\text{are collinear.}\tag{1}$$

**Conclusion of the Case Study:**
The base model, with its exploratory and erratic approach, while not always reaching the correct answer, demonstrates a flexible reasoning capacity. In contrast, the modified model, trained to be efficient on a single type of task, applies a pattern incorrectly, which leads to a **"collapse by specialization"** on a high-level problem.

---

### **Analysis of Variability: The Scatter Plot**

The contrast between the base model and the in-context learning model becomes even more apparent when analyzing the dispersion of response times for the Olympiad problem.

* The **Original Model** exhibits high variability, with times ranging from 292s to 1881s. This wide dispersion reflects the model's **chaotic resilience**: its logic is exploratory and, therefore, unpredictable in terms of time.
* The **In-Context Learning Model** shows a clustering of response times in the highest range (2400s-2600s), with some errors, which indicates it gets "stuck" in a specific, time-consuming line of reasoning before failing. This is a visual manifestation of **optimized fragility**, as the model lacks the flexibility to pivot when a pattern fails.



---

### **Conclusion: A New Perspective**

This research has revealed many facets of how a model's internal processing works. It demonstrates that the logic of these models is far more malleable than previously thought and that low-cost **in-context learning** can lead to profound and unexpected changes. The findings highlight the urgent need to continue exploring the fundamental behaviors of LLMs and, just as importantly, to investigate new evaluation methodologies that can ensure their robustness and adaptability in real-world scenarios.

---

### **Reproducibility and Raw Data**

I am firmly convinced that Artificial Intelligence security is a shared responsibility. The complete raw data, examples of the models' **Thinking...** logs, the modelfile used for configurations, will be made available in this repository.

[[DATASET](./DATASET1)

I invite other researchers and developers to replicate my experiment, analyze my data, and contribute their own findings. My goal is to collectively build a deeper understanding of these complex behaviors.

---

### **Disclaimer**

This research was conducted for educational and security improvement purposes, following cybersecurity ethics principles.
