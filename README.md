# AWS Bedrock PDF Chat Application

This repository contains a Streamlit-based application that enables users to interact with PDF documents using AWS Bedrock and LangChain. With this app, you can upload PDF files, generate vector embeddings using Amazon Bedrock Titan, and retrieve contextual answers to your questions directly from the PDF content.

## Table of Contents
- [AWS Services Used](#aws-services-used)
- [Features](#features)
- [Workflow](#workflow)
- [Installation](#installation)
- [Configuration](#configuration)
- [How to Use](#how-to-use)
- [Example Usage](#example-usage)
- [Future Improvements](#future-improvements)
- [License](#license)

## AWS Services Used

1. **Amazon Bedrock**: Utilized for both embedding text using Amazon Titan and for providing large language models (LLMs) to generate responses based on the retrieved context.
2. **AWS Lambda** (Optional): For serverless handling of vector embeddings or response generation if hosted on AWS.
3. **Amazon S3** (Optional): To store PDFs, embedding files, or model outputs.
4. **Amazon IAM**: To manage access and permissions for AWS resources involved in the application.

## Features

- **PDF Ingestion**: Load and process PDF documents stored in a local directory.
- **Text Embedding with Bedrock**: Generate vector embeddings for PDF content using Amazon Titan Embeddings.
- **Vector Store with FAISS**: Store embeddings in a FAISS index, allowing efficient similarity-based retrieval.
- **Question-Answering via AWS Bedrock Models**: Use Amazon Bedrock’s language models to answer questions based on the PDF content.
- **Interactive Streamlit UI**: Engage with the application in an intuitive UI, where you can upload files, manage the vector store, and ask questions.

## Workflow

1. **PDF Loading**: Load PDF files from the `data` directory and split them into text chunks for better processing using LangChain’s `RecursiveCharacterTextSplitter`.
2. **Embedding Generation**: Use Amazon Bedrock’s `titan-embed-text-v1` model to create vector embeddings for the text chunks.
3. **Vector Store Creation**: Store the embeddings in a FAISS index locally.
4. **Question Answering**: Query the vector store for relevant text chunks and use an LLM model via AWS Bedrock to generate responses based on the retrieved context.

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/aws-bedrock-pdf-chat.git
   cd aws-bedrock-pdf-chat
