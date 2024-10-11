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
2. **Set up a Virtual Environment**:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # On Windows use `.venv\Scripts\activate`
3. **Install Required Packages**:
   ```bash
   pip install -r requirements.txt

4. **Install and Configure AWS CLI**: Follow AWS CLI installation instructions and configure it with:
   ```bash
   aws configure
Enter your Access Key ID, Secret Access Key, and default region name.

## Configuration

1. **AWS Credentials**:
- Ensure your IAM user has permissions to access Bedrock, S3 (optional), and any other required services.
- AWS credentials can be set up via the AWS CLI (aws configure) or environment variables.
2. **Set Up PDF Files**:
- Place your PDF files in the data folder within the project directory. The application will load and process these files.
3. **Streamlit Configuration**:
- Update Streamlit’s configuration settings to adjust page titles and icons as per your preference.
- In the app code, you can set the parameters like chunk_size and chunk_overlap in data_ingestion() to optimize PDF processing.

## How to Use

1. **Launch the Application**:
   ```bash
   streamlit run ragapp.py
The application will open in your default web browser.

2. **Upload PDFs**:
- Go to the "Update Or Create Vector Store" sidebar option and click the "Vectors Update" button. This will process the PDF files in the data directory and create a vector store.

3. **Ask Questions**:
- Type a question in the main input field and choose either "Claude Output" or "Llama2 Output" to retrieve responses. The application will process the question, retrieve relevant text chunks from the PDF, and provide a contextual answer.

## Example Usage

Here’s a quick example of how to interact with the app:

1. Place sample.pdf in the data directory.
2. Start the application and click Vectors Update in the sidebar to process the document.
3. Enter a question like “What is the summary of the document?” in the input field and click Claude Output.
4. The application will return a response based on the content of sample.pdf.

## Future Improvements

**Add Support for More File Types**: Extend document loader to support Word, text, and other file formats.
**Database Integration**: Store processed documents in a persistent database for faster retrieval.
**Improve UI**: Add more options for file uploads and vector store management.
**Model Choice**: Implement more Bedrock models and other frameworks for additional flexibility in retrieval and question-answering.







