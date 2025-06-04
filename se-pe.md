# Prompt Engineering, Lee Boonstra, Google

- **Author**: Lee Boonstra
- **Date**: September 2024

This whitepaper focuses on writing and optimizing prompts for the Gemini model within Google Vertex AI or via its API, covering prompting techniques, model configuration, best practices, and practical coding examples.

Links:

- [Document: Prompt Engineering](https://www.gptaiflow.tech/assets/files/2025-01-18-pdf-1-TechAI-Goolge-whitepaper_Prompt%20Engineering_v4-af36dcc7a49bb7269a58b1c9b89a8ae1.pdf)
- [youtube: Prompt Engineering Guide - From Beginner to Advanced, Matthew Berman](https://www.youtube.com/watch?v=uDIW34h8cmM)

---

## Key ideas

### 🔧 **1. Prompt Engineering Is Iterative**

* Writing effective prompts is a trial-and-error process.
* Prompts must be tuned for the specific task, model, and desired output format.

---

### 📐 **2. Prompting Techniques**

* **Zero-shot**: Ask directly without examples.
* **One-shot & Few-shot**: Provide 1 or a few examples to guide the model.
* **System prompting**: Define task scope and structure (e.g., output in JSON).
* **Role prompting**: Assign personas (e.g., “act as a travel guide”).
* **Contextual prompting**: Provide background context to guide responses.
* **Step-back prompting**: Ask a general question before a specific one.
* **Chain of Thought (CoT)**: Include step-by-step reasoning to improve accuracy.
* **Self-consistency**: Run the same prompt multiple times and choose the most common answer.
* **Tree of Thoughts (ToT)**: Explore multiple reasoning paths instead of one.
* **ReAct**: Combine reasoning with external actions (e.g., search APIs).

---

### ⚙️ **3. LLM Output Configuration**

* **Temperature**: Controls randomness. Use low values (e.g., 0) for deterministic results.
* **Top-K / Top-P**: Limit token sampling pool to control diversity.
* **Token limit**: Cap response length to control cost and focus.

---

### 💡 **4. Code Prompting**

* Prompts can write, explain, debug, and translate code.
* Examples demonstrate Bash-to-Python translation and bug fixing via prompts.

---

### 🤖 **5. Automatic Prompt Engineering (APE)**

* LLMs can help write better prompts by generating and evaluating prompt variants.
* Useful for scaling prompt creation, e.g., for training chatbots.

---

### 🧠 **6. Best Practices**

* **Give examples** (few-shot).
* **Be specific** about expected output format.
* **Use instructions instead of constraints** (tell what to do, not what not to).
* **Keep prompts simple and clear**.
* **Use variables** for dynamic prompts.
* **Log and document prompt attempts** (use tables or spreadsheets).
* **Experiment with format/style/output**.
* **Mix classification examples** to avoid bias.
* **Adapt prompts to model updates**.

---

### 📋 **7. Operational Advice**

* Save and version prompts alongside code.
* Use tools like Vertex AI Studio to test and store prompts.
* Integrate evaluation and regression testing for production-grade prompts.