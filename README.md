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

## Conclusion
Concizee combines advanced AI techniques—prompt engineering, structured JSON output, function calling for backend operations, and optional retrieval-augmented generation—to create a powerful and user-friendly text summarization tool. This project offers both practical value and hands-on experience with key concepts in modern AI application development.
