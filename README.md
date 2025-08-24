# Concizee - AI-Powered Text Summarizer

## Project Overview
Concizee is an AI-powered text summarizer designed to help users quickly understand lengthy texts by generating concise and clear summaries. Users can upload or paste long texts, and the application produces structured summaries in bullet or numbered lists, making key information easier to digest. Concizee is ideal for students, researchers, and professionals who want to save time and efficiently grasp important points from lengthy documents, articles, or reports.

---

## Key Concepts Implementation

### 1. Prompting
Prompting is central to guiding the AI in generating accurate summaries.  
- The **system prompt** sets the AI's role as a summarization assistant tasked with extracting and presenting key points clearly and succinctly.  
- The **user prompt** includes the input text and may also specify preferences like summary length or format (bullet points or numbered lists).  
- Dynamic prompt engineering adjusts the instructions based on context, ensuring relevant and coherent output.

### 2. Structured Output
The summarized content is returned in a well-defined structure for ease of use and further processing.  
- The AI outputs summaries as JSON objects containing fields such as:  
  - `summary_points`: an array of bullet or numbered key points.  
  - `original_text_length`: the length of the input text.  
  - `summary_length`: the count of summary points generated.  
- This structure supports integration with front-end UI components or export functions, and enhances readability.

### 3. Function Calling
Function calls allow the AI to interact with backend utilities, improving efficiency and handling large inputs.  
- Backend functions preprocess user input by cleaning and splitting texts if they exceed token limits.  
- The AI triggers functions like `split_text()` to divide long documents, and `combine_summaries()` to merge partial summaries into a final output.  
- Function calls enable modular processing and ensure smooth handling of varying input sizes.

### 4. Retrieval-Augmented Generation (RAG)
RAG enhances the summarizer by supplementing generation with relevant external information.  
- When enabled, the system uses semantic search to retrieve related documents or contextual data from external databases or knowledge bases based on the user’s input.  
- These retrieved documents are then fed alongside the original text to the AI model to generate a more comprehensive and context-rich summary.  
- RAG helps keep summaries accurate and up-to-date by grounding them in real-world, external information beyond the model’s internal training.

## Prompting 

### Zero Shot Prompting 

A zero shot prompting means giving a task of AI without providing examples or other information, it relies the pre-trained model to respond to your question

* Translate "What is your name ?" in Russian - Text Transformation
* How is the weather today in Delhi - Information Retrieval 
* Write a poem on nature - Creative Task
* What is the answer to 147^89 ? - Reason & Problem Solving

# One-Shot Prompting Examples

---

## What is One-Shot Prompting?

One-shot prompting is a technique where you give **exactly one example** of a task to the AI in your prompt. This example shows the AI the **format and expected output**, so it can perform the task correctly on a **new input**.

Think of it as showing someone **how to do something once**, then asking them to do it again on a new problem.

---

## 1) Sentiment Classification

**Explanation:**
We give **one example sentence and its sentiment**, then ask AI to classify a new sentence.

**Example:**

* **Input-1:** "I love this movie!"
* **Output-1:** Positive

Now classify:

* **Input-2:** "The service was very slow and frustrating."
* **Output-2:** Negative ✅

Here, the AI sees the pattern: “sentence → sentiment” and applies it to the new input.

---

## 2) Summarization

**Explanation:**
We provide **one example of a long sentence and its concise summary**, then ask AI to summarize a new text.

**Example:**

* **Text-1:** "The cat climbed up the tree and got stuck on a high branch."
* **Summary-1:** "Cat stuck on tree branch."

Now summarize:

* **Text-2:** "Rain poured heavily all night, causing minor flooding in the streets."
* **Summary-2:** "Heavy rain caused street flooding." ✅

Here, the AI learns to **compress a long sentence into a short summary**.

---

## 3) Reasoning / Math

**Explanation:**
We show **one simple math problem and its answer**, then ask AI to solve another similar problem.

**Example:**

* **Problem-1:** 7 × 6 = ?
* **Answer-1:** 42

Now solve:

* **Problem-2:** 9 × 5 = ?
* **Answer-2:** 45 ✅

The AI understands the **pattern of the operation** and applies it to a new problem.

---

## Key Points of One-Shot Prompting

1. You give **exactly one example** of input → output.
2. Example shows the **format, style, and type of answer**.
3. AI uses this example to generate the correct output for **new inputs**.

# Multiple-Shot Prompting Examples

---

## What is Multiple-Shot Prompting?

Multiple-shot prompting is when you give an AI **multiple examples** as an input before asking it to generate its own response.
It’s like teaching by showing several solved examples so the AI can pick up the **pattern, style, and logic** before answering the actual question.

---

## 1) Structured Data Extraction

**Example 1:**

* **Text:** "John bought 3 apples for \$5."
* **Extracted Data:** {"name": "John", "item": "apples", "quantity": 3, "price": 5}

**Example 2:**

* **Text:** "Sara ordered 2 coffees for \$8."
* **Extracted Data:** {"name": "Sara", "item": "coffees", "quantity": 2, "price": 8}

Now extract data:

* **Text:** "Mike purchased 5 oranges for \$12."
* **Extracted Data:** {"name": "Mike", "item": "oranges", "quantity": 5, "price": 12} ✅

Here, the AI sees **multiple examples** and learns the **pattern for extracting structured information**.

---

## 2) Text Classification

**Example 1:**

* **Text:** "The movie was amazing, I loved every minute of it."
* **Sentiment:** Positive

**Example 2:**

* **Text:** "This is the worst service I've ever experienced."
* **Sentiment:** Negative

**Example 3:**

* **Text:** "The food was fine, nothing special."
* **Sentiment:** Neutral

Now classify:

* **Text:** "I'm impressed with the quality but delivery was slow."
* **Sentiment:** Positive ✅

Here, AI learns **how to classify sentiment** by looking at multiple examples, improving accuracy and understanding nuanced cases.

---

## Key Points of Multiple-Shot Prompting

1. You provide **several examples** of input → output.
2. Helps AI **understand patterns, nuances, and logic** better than one-shot.
3. Useful for tasks like **data extraction, text classification, summarization, reasoning, and more**.

# Dynamic Prompting Examples

---

## What is Dynamic Prompting?

Dynamic prompting is the technique of creating AI prompts that **change based on context, variables, or real-time data** instead of being fixed.
It uses a **template with placeholders** that get filled in at runtime, allowing the AI to adapt its response to the situation.
This makes outputs more **personalized, relevant, and context-aware** compared to static prompts.

---

## 1) Personalized Chatbot Greeting

**Template:**

* "Hello {user\_name}, welcome back! How was your {last\_activity}?"

**Runtime Example:**

* "Hello Priya, welcome back! How was your yoga session today?" ✅

Here, the AI fills in **dynamic variables** like `user_name` and `last_activity`.

---

## 2) Travel Assistant

**Template:**

* "Your flight to {destination} is scheduled at {departure\_time}. Remember to {travel\_tip}."

**Runtime Example:**

* "Your flight to Paris is scheduled at 7:30 AM. Remember to check in online." ✅

AI adapts the message based on **destination, departure time, and travel advice**.

---

## 3) Task Reminder

**Template:**

* "Hi {user\_name}, you have {task\_count} tasks pending for today, including: {task\_list}."

**Runtime Example:**

* "Hi Rahul, you have 3 tasks pending for today, including: submit report, call client, and update website." ✅

AI generates **context-aware reminders** based on **user and task details**.

---

## Key Points of Dynamic Prompting

1. Prompts are **not fixed**; they adapt to variables or context.
2. Templates have **placeholders** filled at runtime.
3. Makes AI outputs **personalized, relevant, and context-aware**.

---

## Chain-of-thought (CoT) prompting
→ A prompting technique where you ask the AI to **show its step-by-step reasoning** before giving the final answer. It helps the model solve **complex problems** more accurately.

---

### **Examples**

**1. Math Problem**
**Prompt:**

```
What is 20 × 15? Think step by step.
```

**Output:**

```
20 × 15 = (20 × 10) + (20 × 5) = 200+ 100 = 300.
Answer: 300
```

---

**2. Riddle Solving**
**Prompt:**

```
If John is older than Mary, and Mary is older than Sam, who is the oldest? Think step by step.
```

**Output:**

```
John > Mary > Sam.
So, John is the oldest.
```

---

**3. Word Problem**
**Prompt:**

```
A train travels 30 km in 2 hours. What is its average speed? Think step by step.
```

**Output:**

```
Speed = Distance ÷ Time = 30 ÷ 2 = 15 km/h.
Answer: 15 km/h.
```

---

## Embeddings
→ Numerical representations of text, images, or other data in a **high-dimensional vector space** where **similar items are close together**. They’re used for **semantic search, recommendation systems, clustering, and NLP tasks**.

---

### **Examples**

**1. Semantic Text Search**

* Input: `"Best pizza places in Delhi"`
* Embedding model converts the query & restaurant descriptions into vectors.
* Finds the **closest vectors** → returns most relevant pizza places.

---

**2. Document Similarity**

* Input documents:

  * Doc A: `"Machine learning improves AI."`
  * Doc B: `"Deep learning enhances artificial intelligence."`
* Their embeddings will be **close** → meaning they're **semantically similar**.

---

**3. Recommendation System**

* If you liked `"Interstellar"`, the system finds movies with **embedding vectors** closest to `"Interstellar"` and recommends them.

---

### Cosine Similarity
 → A metric used to measure **how similar two vectors are**, based on the **cosine of the angle** between them.

* Value ranges from **-1** to **1**:

  * **1** → exactly similar (same direction)
  * **0** → no similarity (orthogonal)
  * **-1** → completely opposite

### **Example**

Let’s say we have two vectors:

* **A = \[1, 2]**
* **B = \[2, 3]**

$$
\text{Cosine Similarity} = \frac{A \cdot B}{||A|| \, ||B||}
$$

**Step 1 — Dot product:**

$$
A \cdot B = (1)(2) + (2)(3) = 8
$$

**Step 2 — Magnitudes:**

$$
||A|| = \sqrt{1^2 + 2^2} = \sqrt{5}, \quad ||B|| = \sqrt{2^2 + 3^2} = \sqrt{13}
$$

**Step 3 — Cosine similarity:**

$$
\text{Cosine Similarity} = \frac{8}{\sqrt{5} \cdot \sqrt{13}} \approx 0.992
$$

**Interpretation:**
A and B are **very similar** because the cosine similarity is close to **1**.

---



## Conclusion
Concizee combines advanced AI techniques—prompt engineering, structured JSON output, function calling for backend operations, and optional retrieval-augmented generation—to create a powerful and user-friendly text summarization tool. This project offers both practical value and hands-on experience with key concepts in modern AI application development.
