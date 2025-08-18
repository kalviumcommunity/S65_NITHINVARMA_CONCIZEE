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


## Conclusion
Concizee combines advanced AI techniques—prompt engineering, structured JSON output, function calling for backend operations, and optional retrieval-augmented generation—to create a powerful and user-friendly text summarization tool. This project offers both practical value and hands-on experience with key concepts in modern AI application development.
