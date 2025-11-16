Overview

This repository contains an n8n Retrieval-Augmented Generation (RAG) workflow built for the IST402 final project. The workflow uses Pinecone as a vector database and Google Gemini as the language model. Users can upload documents, embed them, store them in Pinecone, and query the system for answers grounded in the uploaded content.

The workflow is modular, event-driven, and fully replicable by anyone following the setup steps below.

Setup Instructions
Requirements
-- n8n (Desktop, Cloud, Docker, or self-hosted)
-- Google AI Studio API key (for Gemini)
-- Pinecone API key
-- Pinecone index named ist402 (or chosen name)
-- Documents you want to upload and index

Import the Workflow
-- Open n8n
-- Go to Workflows
-- Click Import from File
-- Upload IST402_n8n_GroupProject
-- Do not activate it yet

Configure Pinecone
Create the Index
-- Log into Pinecone
-- Create an index named ist402 (or chosen name)
-- Set the dimension to match your embedding model
-- Deploy the index

Add Pinecone Credentials in n8n
-- Go to Credentials
-- Create a new Pinecone credential
-- Enter your API key and environment
-- Save
-- Open the Pinecone Vector Store node in the workflow
-- Attach your new credential

Configure Gemini
-- Open Google AI Studio
-- Generate an API key
-- In n8n, create a Google Gemini credential
-- Paste your API key
-- Save
-- Open all Gemini nodes in the workflow
-- Attach your Gemini credential

Model used: models/gemini-2.0-flash

Upload and Index Documents
-- Open the document loader node
-- Upload or link your files
-- Run Execute Workflow manually
-- The workflow will:
-- Load the files
-- Extract text
-- Chunk the text
-- Generate embeddings
-- Store them in Pinecone

Your vector index is ready after this run.

Run Queries
-- Enter a prompt through the workflow input node
-- The workflow will:
-- Embed the query
-- Search Pinecone
-- Send results to Gemini
-- Return an answer grounded in your uploaded documents

Troubleshooting
Vector dimension mismatch
-- Update the Pinecone index dimension to match your embedding model
Index not found
-- Make sure the index name is exactly ist402 (or chosen name)

Empty responses
-- Confirm documents successfully embedded and inserted into Pinecone

Gemini authentication issues
-- Reconnect or recreate your Gemini credential and attach it to all Gemini nodes
