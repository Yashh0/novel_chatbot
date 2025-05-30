# Document-Aware Chatbot using Groq AI

This is a chatbot that allows users to ask questions about a long document (100+ pages). It uses Groq's ultra-fast LLM to give accurate, context-aware answers in real time.

## Objective

Build a chatbot that can:
- Ingest and understand a large document
- Accept user questions in natural language
- Provide relevant and useful answers
- Optionally include sources or citations

## Tools Used

| Tool | Purpose |
|------|---------|
| Groq (`meta-llama/llama-4-scout-17b-16e-instruct`) | Fast, high-performance LLM |
| LangChain | Manages the Retrieval-Augmented Generation (RAG) pipeline |
| Chroma | Vector database for storing and retrieving embeddings |
| PyMuPDF | Extracts text from PDF documents |
| Tiktoken | Tokenizes and chunks the text efficiently |

## Architecture

1. **Document Parsing**
   - Extract text from a large PDF using PyMuPDF.

2. **Chunking**
   - Split the text into overlapping chunks to manage long input size.

3. **Embedding**
   - Generate vector embeddings using Groq's embedding API for each chunk.
   - Store them in Chroma (vector DB).

4. **Retrieval**
   - When a user asks a question, retrieve the most relevant chunks from Chroma.

5. **Prompt Construction**
   - Combine the user’s question with retrieved chunks to create a complete prompt.

6. **LLM Inference**
   - Use Groq’s `llama-4-scout` model to generate an answer based on the prompt.

7. **Answer Display**
   - Return the generated answer to the user through a simple notebook interface.

## Setup and Usage

This project is implemented in a Google Colab notebook.

Steps:
1. Open the Colab notebook.
2. Upload a PDF file with 100+ pages.
3. Follow the cells to load, chunk, embed, and index the document.
4. Ask questions in the provided input.
5. View fast and context-aware responses from the chatbot.

## Why This Approach?

- **Groq** provides high-speed, low-latency LLM responses.
- **Chunking** allows handling of large documents.
- **RAG** improves answer accuracy by grounding answers in source material.
- **Chroma** efficiently retrieves the most relevant parts of the document.

## Document Used

> Example: [The Adventures of Huckleberry Finn]([https://www.gutenberg.org/files/76/76-h/76-h.htm](https://www.planetebook.com/free-ebooks/the-adventures-of-huckleberry-finn.pdf))

## Notes

- This is a single-turn chatbot. Multi-turn can be enabled using LangChain’s memory module.
- Embedding is done once per document upload. Re-running chunks/embedding isn’t necessary unless the document changes.
- Prompt templates can be customized to change the tone or style of the bot.

