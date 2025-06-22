---
layout: post
title: Implementing an RAG pipeline...
description: ...how simple yet naive
date: 2025-05-13
tags: [growth, technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: false

---

After spending some time fixing the connection to OpenSearch and writing the code to convert text into embedding vectors, store them in OpenSearch, retrieve them using k-NN, and generate responses using Claude, I've finally implemented a basic RAG (Retrieval-Augmented Generation) pipeline.

However, the initial results weren't as good as I had hoped. The responses often didn't match or directly answer the user's queries.

After going through some LLM cookbooks, I realized that my implementation was essentially a naive RAG pipeline. I had simply split large documents into chunks and directly converted them into embeddings. What I overlooked was that these long subtexts could benefit from summarization before embedding. Summarizing helps distill the key points from each chunk, which should improve the retrieval accuracy during the k-NN step.

Another area for improvement was reranking. Instead of relying solely on k-NN results, I could retrieve a larger pool of candidate chunks and then use the model to rerank them based on relevance to the query. This extra step provides a more focused context for generating responses.

Just by adding these two steps - summarization before embedding and reranking after retrieval - the quality of responses from my chatbot improved significantly. While I haven't done a rigorous evaluation, I tested the system using random questions related to bank credit cards (from PDFs available on the banks' websites), and the improvements were clearly noticeable. I know the answers to these queries since I personally use some of these credit cards.

These enhancements were made without any fine-tuning of the pipeline. Moving forward, I plan to evaluate the system more systematically and explore fine-tuning for further improvements.
