---
title: Vector Database - A Large Collection of Vectors for AI Applications
author: Eka Prasetia
pubDatetime: 2023-08-10T18:00:06.700+07:00
slug: vector-database
featured: false
draft: false
tags:
  - ai
description: Vector databases are essential for training and deploying AI models that require vector representations of data.
---

## Vector Databases in Generative AI

### What Are Vector Databases?

Vector databases are specialized datastores that store and provide access to both structured and unstructured data, such as text or images, alongside their corresponding **vector embeddings**. These vector embeddings represent the semantic meaning of the original data objects in the form of numerical vectors. Typically, machine learning models generate these embeddings. The key insight is that similar objects are close together in vector space, allowing us to calculate the [similarity](https://en.wikipedia.org/wiki/Similarity_measure) between data objects based on the distance between their vector embeddings.

A vector database contains embeddings - mathematical representations of concepts and objects in a high-dimensional vector space. Each embedding is a point in hyperspace that encapsulates the semantic meaning and relationships between concepts. For example, an embedding for "cat" would be positioned closer to vectors for "dog" and "animal" than to "car" or "tree."

Vector databases are pre-trained on massive datasets like books, websites, and images to capture the nuances of human language and visual concepts.

### Vector Search and AI-Native Databases

Traditionally, databases supported storing vector embeddings for vector search. However, vector databases take this concept further. They are **AI-native**, optimized to perform lightning-fast vector searches at scale. Here's how they do it:

1. **Vector Indexing**: Vector databases pre-calculate distances between data objects using vector indexing. This optimization enables faster retrieval during query time.
2. **Vector Search**: Instead of traditional keyword-based search, vector databases allow semantic search based on similarity. Users can find and retrieve similar objects quickly, even in large-scale production environments.

### Use Cases of Vector Databases in Generative AI

1. **Natural-Language Search Enhancement**:

   - Vector databases excel at efficiently storing and retrieving high-dimensional data.
   - They enhance generative AI systems by enabling quick searches based on vector embeddings.
   - Applications include recommendation systems, semantic searches, and content generation.

2. **Addressing Long-Term Memory and Hallucination Challenges**:
   - Large language models (LLMs), like ChatGPT, sometimes suffer from limitations such as hallucinations and lack of long-term memory.
   - Vector databases complement LLMs by providing a robust mechanism for handling context and retrieving relevant information.
   - They bridge the gap between short-term context and long-term memory, improving the overall quality of generative AI outputs.

## Tools

[Weaviate](https://weaviate.io/), an open-source vector database, Weaviate allows developers to build GenAI applications quickly by leveraging vector search capabilities.

[Pgvector](https://github.com/pgvector/pgvector), a PostgreSQL extension, provides vector search capabilities for PostgreSQL databases. It allows users to store and search vector embeddings directly in PostgreSQL.

[Chroma](https://www.trychroma.com/), is the open-source embedding database. Chroma makes it easy to build LLM apps by making knowledge, facts, and skills pluggable for LLMs.

In summary, vector databases empower generative AI by enhancing search capabilities, addressing model limitations, and facilitating smooth transitions from prototypes to production. 🚀🔍🌟
